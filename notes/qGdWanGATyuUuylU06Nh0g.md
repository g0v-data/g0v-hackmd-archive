{"cmd":"notify",
            "orderid":"NO1597391810",
        "in_trade_id":"20200814200040011100290077820749",
            "status":"1",
            "clients":"ccc",
            "msg":"成功",
            "timestamp":1597414134787}
            
            




function generateRandomString($length = 10) {
    $characters = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';
    $charactersLength = strlen($characters);
    $randomString = '';
    for ($i = 0; $i < $length; $i++) {
        $randomString .= $characters[rand(0, $charactersLength - 1)];
    }
    return $randomString;
}