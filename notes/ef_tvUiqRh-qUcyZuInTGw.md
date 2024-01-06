# 群暉面試題目


麻將麻組有：萬 1~9 、筒 1~9、條 1~9共27種數字牌、東南西北中發白 7 種文字牌。每個34種牌有相同4張，共計136張牌。兩張牌一樣稱之 “將”，三張牌一樣稱之“刻”，萬、筒、條連續三張連號數字稱之“順”。勝利條件為若干組「刻、順」加上一組「將」即為“胡牌”

若我手上有一副牌，請撰寫程式檢查是否為“胡牌”？

```javascript=

// "1-9萬", "1-9筒", "1-9條", "[東南西北中發白]", 
// 0-8, 9-17, 18-26, 27-33

function 順(user, x){
    // 看有沒有符合順的條件
    if (x < 0) return false;
    if (x >= 27) return false;
    
    if (Math.floor((x+2)/9) != Math.floor((x)/9)) return false;
    
    for(let j = x; j <= x+2; j++){
        if (user[j] < 0) return false;
    }
    return true;
}

function 順刻(user){
    // 刻
    // 順: 第一張
    
    for(let i = 0; i < user.length; i++){
        if (user[i] >= 3){ // 是刻
            user[i] -= 3;
            if (順刻(user)) {
                user[i] += 3; // 牌還你
                return true;
            }
            user[i] += 3;
        }
        else if (順(user, i)) { // 順: 第一張
            for(let j = i; j <= i-2; j++){
                user[j] -= 1;
            }
            if (順刻(user)) {
                for(let j = i; j <= i-2; j++){
                    user[j] += 1;
                } // 牌還你
                return true;
            }
            for(let j = i; j <= i-2; j++){
                user[j] += 1;
            }
        }
    }
    return false;
}

function 胡(user){
    const user = [0,0,0,...];

    // 先找可能的將
    for(let i = 0; i < user.length; i++){
        if (user[i] < 2) continue; // 不是將

        // 他是將
        user[i] -= 2;

        // 看是不是順-刻的組合
        if (順刻(user)) {
            user[i] +=2;
            return true;
        }

        // 不是的話要把牌放回去
        user[i] +=2;
    }
    
    return false;
}
```