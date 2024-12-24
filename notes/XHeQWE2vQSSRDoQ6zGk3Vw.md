#final project

<pre>
#include <iostream>
#include <fstream>  // 用fin: 要讀檔userDB //記得開關檔 
#include <string.h>
#include <cstdlib>
#include<ctime>
using namespace std;

//個別user資料庫 
struct user{
	char username[20];
	char passwd[20];
	int loginno;
	int XAXBwin;
	int XAXBlose;
};


//checkusername是否valid 
bool checkusername(char u[])
{
	int flag;
	if(strlen(u)<3)
		return false;
	for(int i=0;i<strlen(u);i++)
	{
		flag = 0;
		if(u[i]>='0'&&u[i]<='9')
			flag = 1;
		if(u[i]>='a'&&u[i]<='z')
			flag = 1;
		if(u[i]>='A'&&u[i]<='Z')
			flag = 1;
		if(flag==0)
			return false;
	}
	return true;	
}
//check password valid or not
bool checkpassword(char p[])
{
	int flag,vote[2]={0};
	if(strlen(p)<3)
		return false;
	for(int i=0;i<strlen(p);i++)
	{
		flag = 0;
		if(p[i]>='0'&&p[i]<='9')//voteo檢查數字 
		{
			flag = 1;
			vote[0]++;
		}
		if(p[i]>='a'&&p[i]<='z')//vote1檢查字母 
		{
			flag = 1;
			vote[1]++;
		}
		if(p[i]>='A'&&p[i]<='Z')//vote1檢查字母
		{
			flag = 1;
			vote[1]++;
		}
		if(flag==0)
			return false;
	}
	if(vote[0]==0)
		return false;
	if(vote[1]==0)
		return false;
	return true;
}

//newuser
bool newuser(user users[], int* pno) //使用者編號，共幾個使用者 
{
    char username[20];
    char passwd[20];
    char passwd2[20];
    cout << "請輸入用戶名: ";
    cin >> username;

    if (!checkusername(username)) 
	{
        cout << "用戶名不符合規範！請使用至少3個字元的英文字母或數字。" << endl;
        return false;
    }

    for (int i = 0; i < *pno; i++) 
	{
        if (strcmp(users[i].username, username) == 0) {
            cout << "該用戶名已被使用！" << endl;
            return false;
        }
    }

    cout << "請輸入密碼: ";
    cin >> passwd;
    if (!checkpassword(passwd)) {
        cout << "密碼不符合規範！請使用至少3個字元，並包含字母和數字。" << endl;
        return false;
    }

    cout << "請再次輸入密碼: ";
    cin >> passwd2;
    if (strcmp(passwd, passwd2) != 0) {
        cout << "兩次密碼輸入不一致！" << endl;
        return false;
    }

    strcpy(users[*pno].username, username);
    strcpy(users[*pno].passwd, passwd);
    users[*pno].loginno = 0;
    users[*pno].XAXBwin = 0;
    users[*pno].XAXBlose = 0;
    (*pno)++;
    cout << "用戶註冊成功！" << endl;
    return true;
}


//=================XAXB game 

void sep(int n, int c[]) {
    c[0] = n / 1000;
    c[1] = n % 1000 / 100;
    c[2] = n % 100 / 10;
    c[3] = n % 10;
}

int isValid(int n) {
    if (n >= 10000 || n < 0)
        return 0;
    int d[4];
    sep(n, d);
    if (d[0] == d[1] || d[0] == d[2] || d[0] == d[3] || d[1] == d[2] || d[1] == d[3] || d[2] == d[3])
        return 0;
    else
        return 1;
}

int guess(int p[]) {
    int i = 0;
    while (p[i] == 0)
        i++;
    return i;
}

void match(int g, int a, int AB[]) {
    int gd[4], ad[4], m, n;
    sep(g, gd);
    sep(a, ad);
    AB[0] = 0;
    AB[1] = 0;
    for (m = 0; m < 4; m++) {
        for (n = 0; n < 4; n++) {
            if (gd[m] == ad[n]) {
                if (m == n)
                    AB[0]++;
                else
                    AB[1]++;
            }
        }
    }
}
/*
void XAXB_Game(user& currentUser) 
{
	
    int you_ans, com_guess, com_AB[2], tmp_AB[2], i;
    int pool[10000];
    int attempts = 0;//chance
    const int maxAttempts = 10;//chance

    do {
        cout << "!你只有十次機會! Please input your answer:";
        cin >> you_ans;
    } while (isValid(you_ans) == 0);

    for (i = 0; i < 10000; i++)
        pool[i] = isValid(i);

    do {
        com_guess = guess(pool);
        match(com_guess, you_ans, com_AB);
        cout << com_guess << ":" << com_AB[0] << "A" << com_AB[1] << "B" << endl;

        for (i = 0; i < 10000; i++) {
            if (pool[i] == 1) {
                match(com_guess, i, tmp_AB);
                if (tmp_AB[0] != com_AB[0] || tmp_AB[1] != com_AB[1])
                    pool[i] = 0;
            }
        }
		//chance
        attempts++;
        if (attempts >= maxAttempts) {
            cout << "Game over! You've used all your attempts. The computer wins!" << endl;
            currentUser.XAXBlose++;
            return;
        }

    } while (com_AB[0] != 4);

    cout << "Congratulations! you guessed computer's number in " << attempts << " attempts." << endl;
    currentUser.XAXBwin++;
}
*/
void XAXB_Game(user& currentUser) {
    int you_ans, com_ans;
    int you_AB[2] = {0, 0}, com_AB[2] = {0, 0};
    int pool[10000] = {0};
    int attempts = 0; // 用於追蹤總猜測次數
    bool gameOver = false; // 遊戲結束標誌

    // 玩家輸入自己的秘密數字
    do {
        cout << "請輸入一個四位數字，且每位數字不可重複（讓電腦猜）:";
        cin >> you_ans;
    } while (!isValid(you_ans));

    // 設定電腦的隨機答案
    srand(time(0));
    do {
        com_ans = rand() % 10000;
    } while (!isValid(com_ans));

    // 初始化數字池，用於電腦猜測
    for (int i = 0; i < 10000; i++) {
        pool[i] = isValid(i);
    }

    // 玩家和電腦輪流猜測
    while (!gameOver) {
        // 電腦猜測玩家的數字
        int com_guess = guess(pool);
        match(com_guess, you_ans, com_AB);
        cout << "電腦猜測: " << com_guess << " => " << com_AB[0] << "A" << com_AB[1] << "B" << endl;

        // 更新數字池
        for (int i = 0; i < 10000; i++) {
            if (pool[i] == 1) {
                int tmp_AB[2];
                match(com_guess, i, tmp_AB);
                if (tmp_AB[0] != com_AB[0] || tmp_AB[1] != com_AB[1]) {
                    pool[i] = 0;
                }
            }
        }

        // 檢查電腦是否猜中
        if (com_AB[0] == 4) {
            cout << "電腦成功猜中！電腦贏了！" << endl;
            currentUser.XAXBlose++;
            gameOver = true;
            break;
        }

        // 玩家猜測電腦的數字
        int you_guess;
        do {
            cout << "輪到你猜測電腦的數字:";
            cin >> you_guess;
        } while (!isValid(you_guess));

        match(you_guess, com_ans, you_AB);
        cout << "你的猜測: " << you_guess << " => " << you_AB[0] << "A" << you_AB[1] << "B" << endl;

        // 檢查玩家是否猜中
        if (you_AB[0] == 4) {
            cout << "恭喜你！你成功猜中電腦的數字！你贏了！" << endl;
            currentUser.XAXBwin++;
            gameOver = true;
            break;
        }

        // 次數累計
        attempts++;
        cout << "目前總猜測次數: " << attempts << endl;
    }

    // 等待玩家輸入0返回選單
    int returnToMenu;
    do {
        cout << "遊戲結束！輸入 0 返回主選單: ";
        cin >> returnToMenu;
    } while (returnToMenu != 0);
}



 
//=================

//整個程式架構 
int main()
{
    ifstream fin;
    // int user_no = 0, un; 
    int user_no, un;  //幾個user//user01234...的資料 
    user users[100];
    char username[20];
    char passwd[20];

    // 從檔案讀取用戶資料
    fin.open("userDB.text.txt");
    //if (fin.is_open()) {
    fin >> user_no;
    for (un = 0; un < user_no; un++) 
	{
   	    fin >> users[un].username;
        fin >> users[un].passwd;
        fin >> users[un].loginno;
        fin >> users[un].XAXBwin;
        fin >> users[un].XAXBlose;
    }
    fin.close();
    //}

    while (true)//檢查用戶密碼是否正確 
	{
        cout << "輸入用戶名: ";
        cin >> username;
        if (strcmp(username, "new") == 0) //用stringcompare比較是否一樣 
		{
            if (newuser(users, &user_no)) //新用戶存在 
			{
				un = user_no-1;//建立編號 
				break;
			}
            else //註冊失敗 再一次 
				continue;
        }

        cout << "輸入密碼: ";
        cin >> passwd;
        
        bool found = false;//initialize
        
        for (un = 0; un < user_no; un++)//先讀資料 
		{
            if (strcmp(username, users[un].username) == 0) //讀 
			{
                found = true;//讀到了即用戶存在 
                if (strcmp(passwd, users[un].passwd) == 0) //密碼正確，登入數次加一 
				{
                    users[un].loginno++;
                    goto LOGIN_SUCCESS;
                }
				else //密碼錯誤 
				{
                    cout << "密碼錯誤！" << endl;
                    //found = false;
                    break;
                }
            }
        }

        if (!found) 
			cout << "用戶不存在！" << endl;
        //else 
		//	break;
        
    }
    LOGIN_SUCCESS:

    // 登入後選單
    int select;
    do {
        system("cls");//清除前面畫面 
        cout << users[un].username << ", 您好！" << endl;
        cout << "[1] XAXB 遊戲\n[2] 聊天室\n[[3] 隨機笑話生成器\n[4] 電腦解數獨[5]記憶遊戲\n[6]查詢個人資料\n[7]變更密碼\n[0] 離開系統" << endl;
        cout << "請選擇: ";
        cin >> select;
        /*
        if(select==1)
			XAXB_Game(users[un].username);
		if(select==2)
			Chatroom_Main(users[un].username);	
		*/	
		
        switch (select) 
		{
            case 1:
                XAXB_Game(users[un]);
                break;
            case 2:
               // Chatroom_Main(users[un].username);
                break;
                
        }
        
    } while (select != 0);

    // 保存用戶資料
    //SaveUsers(users, user_no);
    return 0;
}

</pre>