# Wordpress


###  :pushpin: 使用 wp_query 搭配 add_filter，如下範例 : 
##### :green_book: 評估取得資料的 function 內，SQL全部自己寫，或是使用 wp_query 搭配 add_filter 
:arrow_forward: Blog 比較適合使用 wp_query
1. 因為 [Filters the WHERE](https://developer.wordpress.org/reference/classes/wp_query/get_posts/) 是共用的 hook，如果寫在共用檔案，當系統擁有很多後台頁面並且搜尋條件皆不同，每個 WP_Query 都會呼叫到 add_filter 的 hook，需要在 hook 裡面加入額外的頁面(templage page)等判斷，避免 WP_Query 查詢時相互影響，程式碼較為分散維護起來較不容易。
2. 當 template page 頁面有設定一些變數為搜尋條件時( 非 $_GET 或 $_POST )，要在 post add_filter 內使用比較不方便，設為 $GLOBALS 是一種方式。

```php
// template-backstage_order_proforma_list.php
$GLOBALS['backstage_order_proforma_list_dealer_id'] = $dealer_id;
$GLOBALS['GOGOJAPCAR'] = $GOGOJAPCAR;

// class-order.php
function backend_get_proforma_list(){
	$query = new WP_Query( array(
		'post_type' => 'car_orders',
		'post_status' => 'publish',
		'posts_per_page' => $count,
		'paged' => $paged,
		's' => $_GETP['search'],
		'date_query' => array(
			array(
				'after'     => $begin_date,
				'before'    => $end_date,
				'inclusive' => true,
			),
		),
	) );
	
	return array(
		'orders' =>$query,
	);
}

// class-order.php
function ct_search_where( $where, $query ) {
    global $pagenow, $wpdb;

	// 取得 搜尋的關鍵字 及 post_type
    $type = $query->query_vars['post_type'];    
    $search_keyword = $query->get('s');
    
	// 指定 templage page 頁面 或是 page_id
    if ( is_page(122) || is_page_template('template-backstage_order_proforma_list.php') ) {
        if ( isset($query) && $type == 'car_orders' ) {
            $dealer_id = $GLOBALS['backstage_order_proforma_list_dealer_id'];
            $GOGOJAPCAR = $GLOBALS['GOGOJAPCAR'];
            $apv_status = $_GET['apv_status'];
        
            // Agent 角度檢視訂單
            if ( $dealer_id != 0 && $dealer_id != $GOGOJAPCAR ) {
                $where .= $wpdb->prepare( ' AND wp_posts.ID IN ( SELECT post_id FROM wp_postmeta WHERE meta_key = %s AND meta_value = %s ) ',  array('status_dealer', $apv_status) );

            }else{
                $where .= $wpdb->prepare( ' AND wp_posts.ID IN ( SELECT post_id FROM wp_postmeta WHERE meta_key = %s AND meta_value = %s ) ',  array('status_gogojapcar', $apv_status) );
            }

            if ( !empty($search_keyword) ) {
                $search_keyword ='%' . $wpdb->esc_like( $search_keyword ) . '%';
                $where .= $wpdb->prepare( ' AND  wp_posts.ID IN ( SELECT post_id FROM wp_postmeta WHERE meta_key in ("location", "lot_no", "vin", "maker", "model", "model_grade") AND meta_value  LIKE %s ) ', array(  $search_keyword ) );
            } 
        }
    }

    return $where;
}
add_filter( 'posts_where', 'ct_search_where',10 ,2 );

```