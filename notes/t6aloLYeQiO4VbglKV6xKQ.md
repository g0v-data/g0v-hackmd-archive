# 在Laravel安裝React

    1. 設定npm下載包
        "@popperjs/core": "^2.11.8",
        "@vitejs/plugin-react": "^4.0.4",
        "bootstrap": "^5.3.1",
        "react": "^18.2.0",
        "react-dom": "^18.2.0",
        "sass": "^1.66.1"
        
        安裝環境依賴
        "dependencies": {
          "react-refresh": "^0.14.0"
        }
         
        結束後安裝：npm install

    2. composer require laravel/ui
    
    3. php artisan ui react
    
    4. npm install
    
    5. 修改vite.config.js
    
        import { defineConfig } from 'vite';
        import laravel from 'laravel-vite-plugin';
        import reactRefresh from 'react-refresh';

        export default defineConfig({
            plugins: [
                laravel({
                    input: [
                        'resources/sass/app.scss',
                        'resources/js/app.js',
                    ],
                    refresh: true,
                }),
                reactRefresh,
            ],
        });
        
    6. 執行編譯/運行伺服器
        npm run dev
        php artisan serve
        
安裝Laravel orchid

    https://orchid.software/en/docs/installation/