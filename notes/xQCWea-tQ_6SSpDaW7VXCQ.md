# **後端啟動時，自動撈取DB資料轉成property**


package tw.com.chubb.life.system.config;

import org.apache.commons.lang3.StringUtils;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.env.EnvironmentPostProcessor;
import org.springframework.core.env.ConfigurableEnvironment;
import org.springframework.core.env.MapPropertySource;
import org.springframework.jdbc.datasource.DriverManagerDataSource;
import org.springframework.jdbc.datasource.lookup.JndiDataSourceLookup;

import javax.sql.DataSource;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.HashMap;
import java.util.Map;

import static tw.com.chubb.life.system.config.SystemConfig.PROPERTIES_JNDI_KEY;

/**
 * 將 TM_TMPL_CONFIG 轉成 properties
 * TM_TMPL_CONFIG.SETTING為value
 */
public class ReadDbPropertiesPostConfig implements EnvironmentPostProcessor {
    /**
     * properties名稱設定
     */
    private static final String PROPERTY_SOURCE_NAME = "databaseProperties";

    @Override
    public void postProcessEnvironment(ConfigurableEnvironment environment, SpringApplication application) {
        // 放置properties key value
        Map<String, Object> propertySource = new HashMap<>();
        try {

            // 建立資料庫連線設定
            DataSource ds = dataSource(environment);

            Connection connection = ds.getConnection();

            // TM_TMPL_CONFIG
            getTmTmplConfigResource(propertySource, connection);

            connection.close();

            // 將抓取後的Map[propertySource]放入Spring環境Property
            environment.getPropertySources().addFirst(new MapPropertySource(PROPERTY_SOURCE_NAME, propertySource));

        } catch (Throwable e) {
            throw new RuntimeException(e);
        }
    }

    private DataSource dataSource(ConfigurableEnvironment env) {
        // 依照設定取得DataSource
        if (StringUtils.equalsIgnoreCase("dev", env.getProperty("spring.profiles.active"))) {
            return jdbcDataSource(env);
        } else {
            return jndiDataSource(env);
        }
    }

    public DataSource jdbcDataSource(ConfigurableEnvironment env) {
        DriverManagerDataSource dataSource = new DriverManagerDataSource();
        dataSource.setDriverClassName(env.getProperty("spring.datasource.driver-class-name"));
        dataSource.setUrl(env.getProperty("spring.datasource.url"));
        dataSource.setUsername(env.getProperty("spring.datasource.username"));
        dataSource.setPassword(env.getProperty("spring.datasource.password"));

        return dataSource;
    }

    /**
     * JNDI DB設定
     *
     * @param env ConfigurableEnvironment
     * @return DataSource
     */
    private DataSource jndiDataSource(ConfigurableEnvironment env) {
        JndiDataSourceLookup dataSourceLookup = new JndiDataSourceLookup();
        return dataSourceLookup.getDataSource(env.getProperty(PROPERTIES_JNDI_KEY));
    }

    private void getTmTmplConfigResource(Map<String, Object> propertySource, Connection connection)
            throws SQLException {
        PreparedStatement preparedStatement =
                connection.prepareStatement("SELECT TASK, SETTING from TM_TMPL_CONFIG");

        // 依照TASK值抓取內容SETTING
        ResultSet rs = preparedStatement.executeQuery();

        while (rs.next()) {
            String task = rs.getString("TASK");
            String setting = rs.getString("SETTING");

            // 從資料庫來源的properties
            propertySource.put(task, setting);
        }

        rs.close();
        preparedStatement.clearParameters();
        preparedStatement.close();
    }
}


****