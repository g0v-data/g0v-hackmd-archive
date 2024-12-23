#final project

<pre>
#include <iostream>
#include <fstream>  // 用fin: 要讀檔userDB //記得開關檔 
#include <string.h>
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
bool checkusername(char username[])
{
	int flag;
	if(strlen(u);<3)
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
bool checkpassword(char password[])
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

void XAXB_Game(user& currentUser) {
    int target[4], guess[4], A = 0, B = 0;
    srand(time(0));
    for (int i = 0; i < 4; i++) {
        target[i] = rand() % 10;
        for (int j = 0; j < i; j++) {
            if (target[i] == target[j]) {
                i--;
                break;
            }
        }
    }

    cout << "歡迎來到 XAXB 遊戲！\n請猜4位不重複的數字，輸入 Exit 結束遊戲。" << endl;
    while (A != 4) {
        A = 0;
        B = 0;

        string input;
        cout << "請輸入猜測: ";
        cin >> input;
        if (input == "Exit") break;

        if (input.length() != 4 || !isdigit(input[0])) {
            cout << "輸入格式錯誤，請重新輸入！" << endl;
            continue;
        }

        for (int i = 0; i < 4; i++) guess[i] = input[i] - '0';

        for (int i = 0; i < 4; i++) {
            if (guess[i] == target[i]) A++;
            else {
                for (int j = 0; j < 4; j++) {
                    if (guess[i] == target[j]) B++;
                }
            }
        }

        cout << A << "A" << B << "B" << endl;
    }

    if (A == 4) {
        cout << "恭喜猜對！遊戲結束。" << endl;
        currentUser.XAXBwin++;
    } else {
        cout << "遊戲結束，目標數字是：";
        for (int i = 0; i < 4; i++) cout << target[i];
        cout << endl;
        currentUser.XAXBlose++;
    }
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
    fin.open("userDB.txt");
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
                    break;
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

    // 登入後選單
    int select;
    do {
        system("cls");//清除前面畫面 
        cout << users[un].username << ", 您好！" << endl;
        cout << "[1] XAXB 遊戲\n[2] 聊天室\n[[3] 隨機笑話生成器\n[4] 電腦解數獨[5]記憶遊戲\n[6]查詢個人資料\n[7]變更密碼\n[0] 離開系統" << endl;
        cout << "請選擇: ";
        cin >> select;

        switch (select) {
            case 1:
                XAXB_Game(users[un]);
                break;
            case 2:
                Chatroom_Main(users[un].username);
                break;
            
        }
    } while (select != 0);

    // 保存用戶資料
    //SaveUsers(users, user_no);
    return 0;
}

</pre>