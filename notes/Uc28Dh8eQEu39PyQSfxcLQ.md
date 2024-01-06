3 Expressions (EXP) 
3.1 EXP50-CPP. Do not depend on the order of evaluation for side effects 
程式碼的邏輯不應受到the order of evaluation所影響。
3.2 EXP51-CPP. Do not delete an array through a pointer of the incorrect type 
刪除一個多型的物件會有不可預測的行為
3.3 EXP52-CPP. Do not rely on side effects in unevaluated operands 
sizeof(), typeid(), noexcept(), decltype(), and declval()不執行運算
3.4 EXP53-CPP. Do not read uninitialized memory 
變數應初始化
3.5 EXP54-CPP. Do not access an object outside of its lifetime 
注意物件生命週期
3.6 EXP55-CPP. Do not access a cv-qualified object through a cv-unqualified type
注意變數是否被定義為const或是volatile
3.7 Do not call a function with a mismatched language linkage
