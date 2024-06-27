# Form Validation
使用Html 搭配 JavaScript

1. **HTML5 原生檢查**
2. [**jQuery Validation**](https://github.com/jquery-validation/jquery-validation)
3. **Parsley.js**
4. **正則表達式**
5. **[Bootstrap Validation](https://getbootstrap.com/docs/5.0/forms/validation/)**
###### 1. HTML5 原生檢查
優點

- 簡單易用，不需要額外的庫或插件。
- 瀏覽器原生支持，性能好。

缺點

- 功能有限，僅支持基本的驗證規則。
- 各瀏覽器之間的支持和用戶體驗可能略有差異。

###### 2. jQuery Validation

優點

- 功能強大且靈活，可以自定義驗證規則和錯誤訊息。
- 大量文檔和社群支持。

缺點

- 依賴 jQuery，需要加載 jQuery 庫，增加頁面加載時間。
- 對於現代項目，可能過於臃腫。

    ###### 範例
    ```
    $('#prepare-submit').on('click', function() {
        // 如果表單驗證通過，進行進一步處理
        if ($('#payamtForm').valid()) {
            // 這裡可以添加提交表單的實際代碼
            alert('表單驗證通過，現在可以提交表單。');
        }
    });
    // 搭配 jQuery Validate 設定自定義驗證方法
    $.validator.addMethod("numericFormat", function(value, element) {
        return this.optional(element) || /^[0-9]$/.test(value);
        }, "請填寫有效的數字。");
    $.validator.addMethod("creditCardFormat", function(value, element) {
       const regex = /^(?:\d{4} ){3}\d{4}$/; // Pattern for 'xxxx xxxx xxxx xxxx'
        return this.optional(element) || regex.test(value);
    }, "信用卡號格式錯誤");
    // 使用 jQuery Validate 插件來設置表單驗證規則和錯誤訊息
    $('#payamtForm').validate({
        rules: {
             select_area_code: {
                 required: true,
            },
            area_code: {
                required: {
                    depends: function(element) {
                        return $('select[name="select_area_code"]').val() !== '+886';
                    }
                },
                mericFormat: true
            },
            con_phone: {
                required: true,
                numericFormat: true
            },
            con_email: {
                required: true,
                email: true
            },
        },
        messages: {
            select_area_code: {
                required: "請填寫手機號碼",
                },
            area_code: {
                required: "請填寫區碼"
            },
            con_phone: {
                required: "請填寫手機號碼",
                email: "請填寫有效的手機號碼"
            },
            con_email: {
                required: "請填寫電子郵件",
            },
        },
        // 錯誤處理：顯示錯誤訊息並彈出模態窗口
        errorPlacement: function(error, element) {
        // 將錯誤訊息顯示在input欄位後面
        //error.appendTo(element.parent()); // 將錯誤訊息添加到輸入欄位的父元素中
        // 檢查元素名稱並附加錯誤訊息
            if ( (element.attr("name") === "last_name" || element.attr("name") === "first_name") && error.text() && element.val() !== '') {
                    setTimeout(function() {
                        //error.appendTo($('#checkModal').find('.error-column'));
                        $('#checkModal .error-column').html(error);
                        $('#checkModal').modal('show');
                        $('input[name="'+element.attr("name")+'"]').val('');
                    }, 100); // 延遲100毫秒，避免輸入過快

                // 清空並隱藏模態視窗
                $('#checkModal .error-column').empty();

                $('input[name="'+element.attr("name")+'"]').focus();
            }
        },
        // 自定義錯誤訊息處理
        invalidHandler: function(form, validator) {
            // 清空之前的錯誤消息
            $('#checkModal .error-column').html('');
            // 顯示每個欄位的錯誤訊息
            $.each(validator.errorList, function(index, error) {
                // 彈出模態窗口來顯示錯誤訊息
                $('#checkModal .error-column').html(error.message);
                $('#checkModal').modal('show');
                exit;
            });
        }
    });
    ```
###### 3. Parsley.js

優點

- 易於使用，基於數據屬性的驗證規則，配置簡單。
- 支持多種內建驗證規則，擴展性好。

缺點

- 需要引入外部庫，可能增加頁面加載時間。
- 對於非常複雜的驗證需求，可能需要額外的自定義。

###### 4. 正則表達式

優點

- 極其靈活，適用於幾乎所有的驗證需求。
- 不需要額外的庫，僅使用原生 JavaScript。

缺點

- 需要手動編寫和管理驗證規則，可能容易出錯。
- 不夠直觀，對於不熟悉正則表達式的開發者不友好。

###### 5. Bootstrap Validation

優點

- 與 Bootstrap 完美整合，樣式和用戶體驗一致。
- 支持基於 HTML 的驗證規則配置，易於使用。
- 可與 Bootstrap 的樣式和組件無縫結合，增強 UI 的一致性。

缺點

- 依賴 Bootstrap，如果項目沒有使用 Bootstrap，則不推薦。
- 功能上可能沒有專門的驗證庫那麼強大，但對於大多數需求已經足夠。

###### 推薦

**Bootstrap Validation** 是一個很好的選擇，特別是在你的項目已經使用 Bootstrap 框架的情況下。它的主要優勢在於簡單易用，並且可以與 Bootstrap 的樣式無縫結合，提升整體的用戶體驗。如果你的項目對於驗證需求相對簡單且使用了 Bootstrap，這是一個不錯的選擇。

如果你的驗證需求較為複雜，並且希望有更高的靈活性和自定義功能，**jQuery Validation** 或 **Parsley.js** 可能更適合。這兩者都提供了強大的驗證功能和靈活的配置選項。

如果你希望保持頁面的簡潔和性能，並且能夠自行處理驗證邏輯，使用 **正則表達式** 搭配原生 JavaScript 是最佳選擇，特別是在不需要依賴外部庫的情況下。

##### 範例
###### 基礎表單驗證寫法
    ```
    // 預設的表單驗證html
    <label for="validationMCOwner">會員卡持有人</label>
    <input type="text" class="form-control" name="validationMCOwner" id="validationMCOwner" placeholder="姓名" required value="">
    <div class="invalid-feedback">請輸入會員卡持有人</div>

    //jacascript
    <script type="text/javascript">
        // 表單驗證初始化，Example starter JavaScript for disabling form submissions if there are invalid fields
        // 預設的表單驗證，訊息是抓取class=invalid-feedback的innerHtml
         (function () {
        'use strict'
        // Fetch all the forms we want to apply custom Bootstrap validation styles to
        var forms = document.querySelectorAll('.needs-validation')
        // Loop over them and prevent submission
        Array.prototype.slice.call(forms)
            .forEach(function (form) {
                form.addEventListener('submit', function (event) {

                    // 預設的表單驗證，訊息抓取class=invalid-feedback的innerHtml
                    if (!form.checkValidity()) {
                        event.preventDefault()
                        event.stopPropagation()
                    }
                    form.classList.add('was-validated')

                    if (!isValid) {
                        event.preventDefault();
                        event.stopPropagation();
                    }
                    form.classList.add('was-validated');
                }, false)
            })
        })()
    </script>
    ```

###### 客製化表單驗證寫法，除了為輸入之外，增加input資料格式的判斷

    ```
    // 經過客製化的表單驗證html
    <label for="validationToken">Token ID</label>
    <input type="text" class="form-control" name="validationToken" id="validationToken" placeholder="123" required  pattern="^[0-9]*$" value="">
    <div class="invalid-feedback" data-required="請輸入Token ID" data-pattern="僅可輸入數字">請輸入Token ID</div>

    <script>
    // 表單驗證初始化，Example starter JavaScript for disabling form submissions if there are invalid fields
    // 這邊訊息客製化，抓取 element 的 data getAttribute
            (function () {
            'use strict'

            // Fetch all the forms we want to apply custom Bootstrap validation styles to
            var forms = document.querySelectorAll('.needs-validation')

            // Loop over them and prevent submission
            Array.prototype.slice.call(forms)
                .forEach(function (form) {
                    form.addEventListener('submit', function (event) {
                        var inputs = form.querySelectorAll('input, select, textarea');
                        var isValid = true;

                        inputs.forEach(function(input) {
                            input.classList.remove('is-invalid');
                            var feedback = input.nextElementSibling;

                            // Clear previous feedback message
                            if (feedback && feedback.classList.contains('invalid-feedback')) {
                                feedback.textContent = '';
                            }

                            if (!input.checkValidity()) {
                                isValid = false;
                                input.classList.add('is-invalid');

                                if (feedback && feedback.classList.contains('invalid-feedback')) {
                                    if (input.validity.valueMissing) {
                                        feedback.textContent = feedback.getAttribute("data-required");
                                    } else if (input.validity.patternMismatch) {
                                        feedback.textContent = (feedback.getAttribute("data-pattern")) ? feedback.getAttribute("data-pattern") : '請輸入有效的資料格式';
                                    } else if (input.validity.typeMismatch) {
                                        feedback.textContent = '請輸入有效的資料類型 ' + input.type + '.';
                                    } else {
                                        if ( input.getAttribute("type") == "datetime-local" ){
                                            const currentDate = new Date();
                                            const selectedDate = new Date(input.value);
                                            if (selectedDate < currentDate) {
                                                feedback.textContent = (feedback.getAttribute("data-required")) ? feedback.getAttribute("data-required") : '時間錯誤';
                                            }
                                        }else{
                                            feedback.textContent = 'Invalid input.';
                                        }
                                    }
                                }
                            }
                        });

                        if (!isValid) {
                            event.preventDefault();
                            event.stopPropagation();
                        }

                        form.classList.add('was-validated');
                    }, false)
                })
            })()
    </sript>
    ```



### 使用 Next.js

Next.js 是一個基於 React 的前端框架，適合現代 Web 開發。以下是幾種常見的表單驗證方法：

1. **HTML5 原生檢查**
2. **React Hook Form**
3. **Formik 與 Yup**

#### 1. HTML5 原生檢查

優點：

- 簡單易用，無需額外的庫。

缺點：

- 功能有限，僅支持基本的驗證規則。

#### 2. React Hook Form

React Hook Form 是一個輕量級的 React 表單庫，性能優異，且易於集成。

優點：

- 輕量且高效，無需重渲染。
- 與 React 的 Hooks 完美結合。
- 易於擴展和自定義。

缺點：

- 需要學習新的 API 和使用方法。
#### 3. Formik 與 Yup

Formik 是一個強大的表單管理庫，Yup 是一個驗證庫。兩者結合可以提供強大的表單驗證功能。

優點：

- 強大的表單管理和驗證功能。
- 與 Yup 結合，可以輕鬆定義驗證規則。

缺點：

- 相對較重，可能對性能有一定影響。


     