#final project

<pre>
#include <iostream>
#include <fstream>  // 用fin: 要讀檔userDB //記得開關檔 
#include <string.h>
#include <cstdlib>
#include<ctime>
#include <vector>
#include <string>
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


//==================chatroom code=========================
void Chatroom_Main(char username[])
{
	ifstream fin;
	ofstream fout;
	char str[1000];
	char input[100];
	do{
		system("cls");
		fin.open("msg.txt");
		while(fin.getline(str,500))
			cout << str << endl;
		fin.close();
		cout << username << ": ";
		cin.getline(input,100);
		if(strcmp(input,"Exit")!=0 && strcmp(input," ")!=0)
		{
			fout.open("msg.txt",ios::app);
			fout<<username<< ": "<<input<<endl;
			fout.close();
		}
	}while(strcmp(input,"Exit")!=0);
}


//===========================================
//=========隨機笑話===============================


//using namespace std;

void Joke_main(char username[]) {
    ifstream fin("joke.txt");  // 開啟笑話資料檔案
    //if (!fin.is_open()) {
    //    cout << "無法開啟笑話檔案！" << endl;
    //    return;
    //}

    vector<string> jokes;  // 用來儲存檔案中的笑話
    string line;

    // 讀取檔案中的每一行笑話並儲存到 vector 中
    while (getline(fin, line)) {
        jokes.push_back(line);
    }

    fin.close();  // 關閉檔案


    // 設定隨機數種子
    srand(static_cast<unsigned int>(time(0)));

    int jokeIndex = rand() % jokes.size();

    cout << username << "，這是你的隨機笑話：" << endl;
    cout << jokes[jokeIndex] << endl;
    
    cout << endl;
    
    int returnToMenu;
    do {
    	cout << "遊戲結束！輸入 0 返回主選單: ";
        cin >> returnToMenu;
    } while (returnToMenu != 0);
    
}

/*

void Joke_main(char username[]) {
    ifstream fin("joke.txt");  // 開啟笑話資料檔案
    string line;
    int lineCount = 0;

    // 計算檔案中的行數
    while (getline(fin, line)) {
        lineCount++;
    }

    // 檔案中至少有一行笑話
    if (lineCount > 0) {
        // 回到檔案開頭
        fin.clear();  // 清除 EOF 標誌
        fin.seekg(0, ios::beg);  // 移動到檔案開頭

        // 設定隨機數種子
        srand(static_cast<unsigned int>(time(0)));

        // 隨機選擇一行
        int randomLine = rand() % lineCount;

        // 跳到隨機選中的行
        for (int i = 0; i <= randomLine; i++) {
            getline(fin, line);
        }

        // 顯示隨機笑話
        cout << username << "，這是你的隨機笑話：" << endl;
        cout << line << endl;
    }

    fin.close();  // 關閉檔案
}
*/
//=========記憶遊戲============ 

void Memory_Main(char username[])
{
    srand(static_cast<unsigned int>(time(0)));  // 設定隨機數種子

    int numDigits = 5;  // 設定數字長度
    vector<int> randomNumbers;  // 用來儲存隨機數字
    string playerInput;  // 儲存玩家輸入的數字

    
    for (int i = 0; i < numDigits; i++) {
        randomNumbers.push_back(rand() % 10);  // 隨機數字 0-9
    }

    // 顯示隨機數字給玩家
    cout << "記住以下數字，然後按 Enter 開始記憶遊戲!" << endl;
    for (int i = 0; i < numDigits; i++) {
        cout << randomNumbers[i] << " ";
    }
    cout << endl;

    // 給玩家 3 秒時間記住數字
    cout << "你有 3 秒鐘記住數字..." << endl;
    _sleep(3000);  // 讓程式等待 3 秒

    system("cls"); //clear

    cout << "請輸入你記住的數字： ";
    cin >> playerInput;

    // 檢查玩家輸入的數字是否正確
    bool isCorrect = true;
    for (int i = 0; i < numDigits; i++) {
        if (playerInput[i] != ('0' + randomNumbers[i])) {
            isCorrect = false;
            break;
        }
    }

    if (isCorrect) {
        cout << "恭喜你，答對了！" << endl;
    } else {
        cout << "很遺憾，答案錯誤。正確答案是：";
        for (int i = 0; i < numDigits; i++) {
            cout << randomNumbers[i];
        }
        cout << endl;
    }

    int returnToMenu;
    do {
        cout << "遊戲結束！輸入 0 返回主選單: ";
        cin >> returnToMenu;
    } while (returnToMenu != 0);
}


// ====================== 


//===============數獨==========================================
/*
void Update(int Q[][9][10],int R,int C,int D)
{
	int r,c,d;
	for(c=0;c<9;c++)
		Q[R][c][D] = 0;
	for(r=0;r<9;r++)
		Q[r][C][D] = 0;
	for(d=1;d<=9;d++)
		Q[R][C][d] = 0;
	for(r=R/3*3;r<=R/3*3+2;r++)
		for(c=C/3*3;c<=C/3*3+2;c++)
			Q[r][c][D] = 0;
	Q[R][C][D] = 1;
}

void Update(int Q[][9][10], int R, int C, int D) 
{
    int r,c;

    // 更新同一列
    for (c = 0; c < 9; c++)
        Q[R][c][D] = 0;

    // 更新同一行
    for (r = 0; r < 9; r++)
        Q[r][C][D] = 0;

    // 更新同一宮格
    for (r = R / 3 * 3; r <= R / 3 * 3 + 2; r++)
        for (c = C / 3 * 3; c <= C / 3 * 3 + 2; c++)
            Q[r][c][D] = 0;

    Q[R][C][0] = D; // 正確設定格子中的數字
}
void readQ(int Q[][9][10])
{
	ifstream fin;
	fin.open("Q1.txt");
	int r,c,d;
	for(r=0;r<9;r++)
		for(c=0;c<9;c++)
			for(d=1;d<=9;d++)
				Q[r][c][d] = 1;
	for(r=0;r<9;r++)
	{
		for(c=0;c<9;c++)
		{
			fin >> Q[r][c][0];
			if(Q[r][c][0]!=0)
			{
				Update(Q,r,c,Q[r][c][0]);
			}
		}
	}
	fin.close();
}

void Print(int Q[][9][10])
{
	int r,c;
	for(r=0;r<9;r++)
	{
		if (r % 3 == 0 && r != 0) 
            cout << "------+-------+------" << endl;
		for(c=0;c<9;c++)
		{
			if (c % 3 == 0 && c != 0) 
                cout << "| ";
			if(Q[r][c][0]>0)
				cout << Q[r][c][0] << " ";
			else
				cout << " . ";
		} 
		cout<<endl;
	}
}

int Test(int Q[][9][10],int R,int C)
{
	int count=0, result=0;
	for(int d=1;d<=9;d++)
	{
		if (Q[R][C][d] == 1) 
		{
            count++;
            result = d;
    	}
	}
	return count == 1 ? result : 0;
}

void Solve(int Q[][9][10])
{
	int change,r,c,d;
	do
	{
		change = 0;
		for(r=0;r<9;r++)
			for(c=0;c<9;c++)
			{
				if(Q[r][c][0]==0)
				{
					d = Test(Q,r,c);
					if(d>0)
					{
						Q[r][c][0] = d;
						Update(Q,r,c,d);
						change = 1;
					}
				}
			}
	}while(change==1);
}

void Sudoku_Main(char username[])
{
	int Q[9][9][10];
	readQ(Q);
	cout << "初始數獨盤面：" << endl;
	Print(Q);
	Solve(Q);
	cout << "\n解後數獨盤面：" << endl;
	Print(Q);
	//return 0;
	
}
 */
/*
void Print(int Q[][9][10]) {
    int r, c;
    for (r = 0; r < 9; r++) {
        for (c = 0; c < 9; c++) {
            if (Q[r][c][0] > 0)
                cout << Q[r][c][0] << " ";
            else
                cout << "  ";
        }
        cout << endl;
    }
}
*/

void Print(int Q[][9][10]) 
{
    int r, c;
    for (r = 0; r < 9; r++) 
    {
        if (r % 3 == 0 && r != 0) 
            cout << "------+-------+------" << endl;

        for (c = 0; c < 9; c++) 
        {
            if (c % 3 == 0 && c != 0) 
                cout << "| ";
            if (Q[r][c][0] > 0)
                cout << Q[r][c][0] << " ";
            else
                cout << " . ";  // 空格顯示為 "."
        } 
        cout << endl;
    }
}
/*
void Update(int Q[][9][10], int R, int C, int D) {
    int r, c, d;
    for (c = 0; c < 9; c++)
        Q[R][c][D] = 0;
    for (r = 0; r < 9; r++)
        Q[r][C][D] = 0;
    for (d = 1; d <= 9; d++)
        Q[R][C][d] = 0;
    for (r = R / 3 * 3; r <= R / 3 * 3 + 2; r++)
        for (c = C / 3 * 3; c <= C / 3 * 3 + 2; c++)
            Q[r][c][D] = 0;
    Q[R][C][D] = 1;
    
    //cout << "更新棋盤 (R=" << R << ", C=" << C << ", D=" << D << "):" << endl;
    //Print(Q);
    
}
*/
void Update(int Q[][9][10], int R, int C, int D) 
{
    int r, c;

    // 更新同一列
    for (c = 0; c < 9; c++) 
        Q[R][c][D] = 0;

    // 更新同一行
    for (r = 0; r < 9; r++) 
        Q[r][C][D] = 0;

    // 更新同一宮格
    for (r = R / 3 * 3; r <= R / 3 * 3 + 2; r++) 
        for (c = C / 3 * 3; c <= C / 3 * 3 + 2; c++) 
            Q[r][c][D] = 0;

    Q[R][C][0] = D; // 正確設定格子中的數字
}
/*
void readQ(int Q[][9][10], const string& filename) {
    ifstream fin;
    fin.open(filename.c_str());

    if (!fin.is_open()) {
        cerr << "Error: Cannot open file " << filename << endl;
        exit(1);
	}

    cout << "Reading Sudoku puzzles from " << filename << "..." << endl;

    int r, c, d;
    for (r = 0; r < 9; r++) {
        for (c = 0; c < 9; c++) {
            if (!(fin >> Q[r][c][0])) {
                cerr << "Error: Failed to read number at row " << r << ", column " << c << endl;
                exit(1);
            }
            if (Q[r][c][0] != 0) {
                Update(Q, r, c, Q[r][c][0]);
            }
        }
    }

    fin.close();
    cout << "Sudoku puzzles loaded successfully." << endl;
}
*/
/*
void readQ(int Q[][9][10], const string& filename) 
{
    ifstream fin;
    fin.open("filename.c_str()");  // 開啟檔案
    int r, c, d;

    // 初始化所有數字範圍設為可選
    for (r = 0; r < 9; r++) 
        for (c = 0; c < 9; c++) 
            for (d = 1; d <= 9; d++) 
                Q[r][c][d] = 1;

    // 讀取檔案中的每個數字並更新該格子
    for (r = 0; r < 9; r++) 
    {
        for (c = 0; c < 9; c++) 
        {
            fin >> Q[r][c][0];  // 讀取數字
            if (Q[r][c][0] != 0)  // 如果該格已經有數字，則進行更新
            {
                Update(Q, r, c, Q[r][c][0]);
            }
        }
    }
    fin.close();  // 關閉檔案
}
*/
void readQ(int Q[][9][10], const string& filename)
{
    ifstream fin;
    fin.open(filename.c_str());
    int r, c, d;
    for (r = 0; r < 9; r++)
        for (c = 0; c < 9; c++)
            for (d = 1; d <= 9; d++)
                Q[r][c][d] = 1;
    for (r = 0; r < 9; r++) {
        for (c = 0; c < 9; c++) {
            fin >> Q[r][c][0];
            if (Q[r][c][0] != 0) {
                Update(Q, r, c, Q[r][c][0]);
            }
        }
    }
    fin.close();
}


int Test(int Q[][9][10], int R, int C) {
    int count = 0, a, d;
    for (d = 1; d <= 9; d++) {
        count += Q[R][C][d];
        if (Q[R][C][d] == 1)
            a = d;
    }
    if (count == 1)
        return a;
    else
        return 0;
}
/*
void Solve(int Q[][9][10]) {
    int change, r, c, d;
    do {
        change = 0;
        for (r = 0; r < 9; r++)
            for (c = 0; c < 9; c++) {
                if (Q[r][c][0] == 0) {
                    d = Test(Q, r, c);
                    if (d > 0) {
                        Q[r][c][0] = d;
                        Update(Q, r, c, d);
                        change = 1;
                    }
                }
            }
    } while (change == 1);
}
*/
void Solve(int Q[][9][10]) {
    int change, r, c, d;
    do {
        change = 0;
        for (r = 0; r < 9; r++) {
            for (c = 0; c < 9; c++) {
                if (Q[r][c][0] == 0) { // If the cell is not solved
                    d = Test(Q, r, c);
                    if (d > 0) { // If there is exactly one valid number
                        Q[r][c][0] = d;
                        Update(Q, r, c, d);
                        change = 1;
                    }
                }
            }
        }
    } while (change == 1);
}


void Sudoku_Main(char username[]) 
{
    int Q1[9][9][10], Q2[9][9][10], Q3[9][9][10], Q4[9][9][10], Q5[9][9][10];
    
    cout << "Reading Sudoku puzzles..." << endl;
    readQ(Q1, "Q1.txt");
    readQ(Q2, "Q2.txt");
    readQ(Q3, "Q3.txt");
	readQ(Q4, "Q4.txt");
	readQ(Q5, "Q5.txt");
    
    cout << "\nPuzzle 1:" << endl;
    Print(Q1);
    cout << "\nPuzzle 2:" << endl;
    Print(Q2);
    cout << "\nPuzzle 3:" << endl;
    Print(Q3);
    cout << "\nPuzzle 4:" << endl;
    Print(Q4);
    cout << "\nPuzzle 5:" << endl;
    Print(Q5);

    cout << "\nEnter the puzzle number you want to solve (1, 2, or 3 or 4 or 5): ";
    int choice;
    cin >> choice;

    if (choice == 1) {
        cout << "\nSolving Puzzle 1..." << endl;
        Solve(Q1);
        Print(Q1);
    } else if (choice == 2) {
        cout << "\nSolving Puzzle 2..." << endl;
        Solve(Q2);
        Print(Q2);
    } else if (choice == 3) {
        cout << "\nSolving Puzzle 3..." << endl;
        Solve(Q3);
        Print(Q3);
    } else if (choice == 4) {
        cout << "\nSolving Puzzle 4..." << endl;
        Solve(Q4);
        Print(Q4);
    } else if (choice == 5) {
        cout << "\nSolving Puzzle 5..." << endl;
        Solve(Q5);
        Print(Q5);
    } else {
        cout << "Invalid choice. Exiting program." << endl;
    }
    
    int returnToMenu;
    do {
        cout << "輸入 0 返回主選單: ";
        cin >> returnToMenu;
    } while (returnToMenu != 0);

    //return 0;
}

//=========查詢個人資料==========================
void Query_Main(user users[], int user_no, char username[]) 
{
    bool found = false;

    // Iterate over the users to find the correct one
    for (int un = 0; un < user_no; un++) 
	{
        if (strcmp(username, users[un].username) == 0) 
		{
            found = true;
            // Print user's personal information
            cout << "用戶名: " << users[un].username << endl;
            cout << "密碼: " << users[un].passwd << endl;
            cout << "登入次數: " << users[un].loginno << endl;
            cout << "XAXB 勝場: " << users[un].XAXBwin << endl;
            cout << "XAXB 輸場: " << users[un].XAXBlose << endl;
            //break;
        }
    }

    if (!found) 
	{
        cout << "用戶不存在！" << endl;
    }
    
    int returnToMenu;
    do {
        cout << "輸入 0 返回主選單: ";
        cin >> returnToMenu;
    } while (returnToMenu != 0);
}

//=======更變密碼================
void ChangePW_Main(user users[], int user_no, char username[]) {
    bool found = false;
    char oldPassword[20], newPassword[20];

    // Iterate over the users to find the correct one
    for (int un = 0; un < user_no; un++) {
        if (strcmp(username, users[un].username) == 0) {
            found = true;
            
            // Ask for the old password
            cout << "請輸入舊密碼: ";
            cin >> oldPassword;

            // Check if the old password is correct
            if (strcmp(oldPassword, users[un].passwd) == 0) {
                // Old password is correct, ask for a new password
                cout << "請輸入新密碼: ";
                cin >> newPassword;

                // Check if the new password is valid (for example, it should not be the same as the old password)
                if (strcmp(newPassword, oldPassword) == 0) {
                    cout << "新密碼不能與舊密碼相同！" << endl;
                } else {
                    // Update the password
                    strcpy(users[un].passwd, newPassword);
                    cout << "密碼變更成功！" << endl;
                }
            } else {
                cout << "舊密碼錯誤！密碼變更失敗。" << endl;
            }
            
            //break;
            int returnToMenu;
    		do {
   			     cout << "輸入 0 返回主選單: ";
   			     cin >> returnToMenu;
   			} while (returnToMenu != 0);
            
        }
    }

    if (!found) {
        cout << "用戶不存在！" << endl;
    }
    
}
//===================



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
        cout << "[1] XAXB 遊戲\n[2] 聊天室\n[3] 隨機笑話生成器\n[4] 電腦解數獨\n[5]記憶遊戲\n[6]查詢個人資料\n[7]變更密碼\n[0] 離開系統" << endl;
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
                Chatroom_Main(users[un].username);
                break;
            case 3:
                Joke_main(users[un].username);
                break;
            case 4:
                Sudoku_Main(users[un].username);
                break;
            case 5:
                Memory_Main(users[un].username);
                break;
            case 6:
                Query_Main(users, user_no, users[un].username);
                break;
            case 7:
                ChangePW_Main(users, user_no, users[un].username);
                break;
                
        }
        
    } while (select != 0);

    // 保存用戶資料
    //SaveUsers(users, user_no);
    return 0;
}


</pre>
        
為什麼電腦會憂鬱? 因為他有D槽

水餃要去哪裡領? 當鋪 因為當舖領（dumpling）

穿露背裝的原住民叫什麼? 後空番

最會流汗的古代皇帝是誰?汗腺帝

什麼東西可以攔電子?紅橙黃綠
 
達文西密碼上面是什麼? 達文西帳號

王一博在路上拉住一個陌生人的手，那個人會說什麼? 放手一搏！

為什麼不能吃生鮭魚? 因為他會在你胃食道逆流

什麼東西會卡在肺裡?  城市，因為City 卡肺（café）

一個胖子掉進氫氧化鈉裡怎麼辦? 只能看他的皂化了

為什麼神仙不能打手槍? 因為仙人掌有刺

公雞最喜歡什麼品牌? MUJI

14. 哪個殺手只講英文
.
銀翼殺手

15. 奈米屌可以拿來幹嘛
.
幹細胞

16. 那個古人最會游泳
.
孟嘗君，因為他仰式三千

17. 東施效顰，那西施在幹嘛
.
吸濕排汗

18. 小鹿斑比的哥哥是誰
.
大陸尋奇

19. 為什麼孔子微積分很爛
.
因為他知其不可微而微之

20. 為什麼山頂洞人不能吃起司
.
因為他們說食cheese die的人

21. 美國(USA)的弟弟是誰
.
USB
<pre>
#include <iostream>
#include <fstream>  // 用fin: 要讀檔userDB //記得開關檔 
#include <string.h>
#include <cstdlib>
#include<ctime>
#include <vector>
//#include <string>
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


//==================chatroom code=========================
void Chatroom_Main(char username[])
{
	ifstream fin;
	ofstream fout;
	char str[1000];
	char input[100];
	do{
		system("cls");
		fin.open("msg.txt");
		while(fin.getline(str,500))
			cout << str << endl;
		fin.close();
		cout << username << ": ";
		cin.getline(input,100);
		if(strcmp(input,"Exit")!=0 && strcmp(input," ")!=0)
		{
			fout.open("msg.txt",ios::app);
			fout<<username<< ": "<<input<<endl;
			fout.close();
		}
	}while(strcmp(input,"Exit")!=0);
}


//===========================================
//=========隨機笑話===============================


//using namespace std;

void Joke_main(char username[]) {
    ifstream fin("joke.txt");  // 開啟笑話資料檔案
    //if (!fin.is_open()) {
    //    cout << "無法開啟笑話檔案！" << endl;
    //    return;
    //}

    vector<string> jokes;  // 用來儲存檔案中的笑話
    string line;

    // 讀取檔案中的每一行笑話並儲存到 vector 中
    while (getline(fin, line)) {
        jokes.push_back(line);
    }

    fin.close();  // 關閉檔案


    // 設定隨機數種子
    srand(static_cast<unsigned int>(time(0)));

    int jokeIndex = rand() % jokes.size();

    cout << username << "，這是你的隨機笑話：" << endl;
    cout << jokes[jokeIndex] << endl;
    
    cout << endl;
    
    int returnToMenu;
    do {
    	cout << "遊戲結束！輸入 0 返回主選單: ";
        cin >> returnToMenu;
    } while (returnToMenu != 0);
    
}


//=========記憶遊戲============ 

void Memory_Main(char username[])
{
    srand(static_cast<unsigned int>(time(0)));  // 設定隨機數種子

    int numDigits = 5;  // 設定數字長度
    vector<int> randomNumbers;  // 用來儲存隨機數字
    string playerInput;  // 儲存玩家輸入的數字

    
    for (int i = 0; i < numDigits; i++) {
        randomNumbers.push_back(rand() % 10);  // 隨機數字 0-9
    }

    // 顯示隨機數字給玩家
    cout << "記住以下數字，然後按 Enter 開始記憶遊戲!" << endl;
    for (int i = 0; i < numDigits; i++) {
        cout << randomNumbers[i] << " ";
    }
    cout << endl;

    // 給玩家 3 秒時間記住數字
    cout << "你有 3 秒鐘記住數字..." << endl;
    _sleep(3000);  // 讓程式等待 3 秒

    system("cls"); //clear

    cout << "請輸入你記住的數字： ";
    cin >> playerInput;

    // 檢查玩家輸入的數字是否正確
    bool isCorrect = true;
    for (int i = 0; i < numDigits; i++) {
        if (playerInput[i] != ('0' + randomNumbers[i])) {
            isCorrect = false;
            break;
        }
    }

    if (isCorrect) {
        cout << "恭喜你，答對了！" << endl;
    } else {
        cout << "很遺憾，答案錯誤。正確答案是：";
        for (int i = 0; i < numDigits; i++) {
            cout << randomNumbers[i];
        }
        cout << endl;
    }

    int returnToMenu;
    do {
        cout << "遊戲結束！輸入 0 返回主選單: ";
        cin >> returnToMenu;
    } while (returnToMenu != 0);
}


// ====================== 


//===============數獨==========================================

void Print(int Q[][9][10]) 
{
    int r, c;
    for (r = 0; r < 9; r++) 
    {
        if (r % 3 == 0 && r != 0) 
            cout << "------+-------+------" << endl;

        for (c = 0; c < 9; c++) 
        {
            if (c % 3 == 0 && c != 0) 
                cout << "| ";
            if (Q[r][c][0] > 0)
                cout << Q[r][c][0] << " ";
            else
                cout << " . ";  // 空格顯示為 "."
        } 
        cout << endl;
    }
}

void Update(int Q[][9][10], int R, int C, int D) 
{
    int r, c;

    // 更新同一列
    for (c = 0; c < 9; c++) 
        Q[R][c][D] = 0;

    // 更新同一行
    for (r = 0; r < 9; r++) 
        Q[r][C][D] = 0;

    // 更新同一宮格
    for (r = R / 3 * 3; r <= R / 3 * 3 + 2; r++) 
        for (c = C / 3 * 3; c <= C / 3 * 3 + 2; c++) 
            Q[r][c][D] = 0;

    Q[R][C][0] = D; // 正確設定格子中的數字
}

void readQ(int Q[][9][10], const string& filename)
{
    ifstream fin;
    fin.open(filename.c_str());
    int r, c, d;
    for (r = 0; r < 9; r++)
        for (c = 0; c < 9; c++)
            for (d = 1; d <= 9; d++)
                Q[r][c][d] = 1;
    for (r = 0; r < 9; r++) {
        for (c = 0; c < 9; c++) {
            fin >> Q[r][c][0];
            if (Q[r][c][0] != 0) {
                Update(Q, r, c, Q[r][c][0]);
            }
        }
    }
    fin.close();
}


int Test(int Q[][9][10], int R, int C) {
    int count = 0, a, d;
    for (d = 1; d <= 9; d++) {
        count += Q[R][C][d];
        if (Q[R][C][d] == 1)
            a = d;
    }
    if (count == 1)
        return a;
    else
        return 0;
}

void Solve(int Q[][9][10]) {
    int change, r, c, d;
    do {
        change = 0;
        for (r = 0; r < 9; r++) {
            for (c = 0; c < 9; c++) {
                if (Q[r][c][0] == 0) { // If the cell is not solved
                    d = Test(Q, r, c);
                    if (d > 0) { // If there is exactly one valid number
                        Q[r][c][0] = d;
                        Update(Q, r, c, d);
                        change = 1;
                    }
                }
            }
        }
    } while (change == 1);
}


void Sudoku_Main(char username[]) 
{
    int Q1[9][9][10], Q2[9][9][10], Q3[9][9][10], Q4[9][9][10], Q5[9][9][10];
    
    cout << "Reading Sudoku puzzles..." << endl;
    readQ(Q1, "Q1.txt");
    readQ(Q2, "Q2.txt");
    readQ(Q3, "Q3.txt");
	readQ(Q4, "Q4.txt");
	readQ(Q5, "Q5.txt");
    
    cout << "\nPuzzle 1:" << endl;
    Print(Q1);
    cout << "\nPuzzle 2:" << endl;
    Print(Q2);
    cout << "\nPuzzle 3:" << endl;
    Print(Q3);
    cout << "\nPuzzle 4:" << endl;
    Print(Q4);
    cout << "\nPuzzle 5:" << endl;
    Print(Q5);

    cout << "\nEnter the puzzle number you want to solve (1, 2, or 3 or 4 or 5): ";
    int choice;
    cin >> choice;

    if (choice == 1) {
        cout << "\nSolving Puzzle 1..." << endl;
        Solve(Q1);
        Print(Q1);
    } else if (choice == 2) {
        cout << "\nSolving Puzzle 2..." << endl;
        Solve(Q2);
        Print(Q2);
    } else if (choice == 3) {
        cout << "\nSolving Puzzle 3..." << endl;
        Solve(Q3);
        Print(Q3);
    } else if (choice == 4) {
        cout << "\nSolving Puzzle 4..." << endl;
        Solve(Q4);
        Print(Q4);
    } else if (choice == 5) {
        cout << "\nSolving Puzzle 5..." << endl;
        Solve(Q5);
        Print(Q5);
    } else {
        cout << "Invalid choice. Exiting program." << endl;
    }
    
    int returnToMenu;
    do {
        cout << "輸入 0 返回主選單: ";
        cin >> returnToMenu;
    } while (returnToMenu != 0);

    //return 0;
}

//=========查詢個人資料==========================
void Query_Main(user users[], int user_no, char username[]) 
{
    bool found = false;

    // Iterate over the users to find the correct one
    for (int un = 0; un < user_no; un++) 
	{
        if (strcmp(username, users[un].username) == 0) 
		{
            found = true;
            // Print user's personal information
            cout << "用戶名: " << users[un].username << endl;
            cout << "密碼: " << users[un].passwd << endl;
            cout << "登入次數: " << users[un].loginno << endl;
            cout << "XAXB 勝場: " << users[un].XAXBwin << endl;
            cout << "XAXB 輸場: " << users[un].XAXBlose << endl;
            //break;
        }
    }

    if (!found) 
	{
        cout << "用戶不存在！" << endl;
    }
    
    int returnToMenu;
    do {
        cout << "輸入 0 返回主選單: ";
        cin >> returnToMenu;
    } while (returnToMenu != 0);
}

//=======更變密碼================
void ChangePW_Main(user users[], int user_no, char username[]) {
    bool found = false;
    char oldPassword[20], newPassword[20];

    // Iterate over the users to find the correct one
    for (int un = 0; un < user_no; un++) {
        if (strcmp(username, users[un].username) == 0) {
            found = true;
            
            // Ask for the old password
            cout << "請輸入舊密碼: ";
            cin >> oldPassword;

            // Check if the old password is correct
            if (strcmp(oldPassword, users[un].passwd) == 0) {
                // Old password is correct, ask for a new password
                cout << "請輸入新密碼: ";
                cin >> newPassword;

                // Check if the new password is valid (for example, it should not be the same as the old password)
                if (strcmp(newPassword, oldPassword) == 0) {
                    cout << "新密碼不能與舊密碼相同！" << endl;
                } else {
                    // Update the password
                    strcpy(users[un].passwd, newPassword);
                    cout << "密碼變更成功！" << endl;
                }
            } else {
                cout << "舊密碼錯誤！密碼變更失敗。" << endl;
            }
            
            //break;
            int returnToMenu;
    		do {
   			     cout << "輸入 0 返回主選單: ";
   			     cin >> returnToMenu;
   			} while (returnToMenu != 0);
            
        }
    }

    if (!found) {
        cout << "用戶不存在！" << endl;
    }
    
}
//===================



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
        cout << "[1] XAXB 遊戲\n[2] 聊天室\n[3] 隨機笑話生成器\n[4] 電腦解數獨\n[5]記憶遊戲\n[6]查詢個人資料\n[7]變更密碼\n[0] 離開系統" << endl;
        cout << "請選擇: ";
        cin >> select;
        
		
        switch (select) 
		{
            case 1:
                XAXB_Game(users[un]);
                break;
            case 2:
                Chatroom_Main(users[un].username);
                break;
            case 3:
                Joke_main(users[un].username);
                break;
            case 4:
                Sudoku_Main(users[un].username);
                break;
            case 5:
                Memory_Main(users[un].username);
                break;
            case 6:
                Query_Main(users, user_no, users[un].username);
                break;
            case 7:
                ChangePW_Main(users, user_no, users[un].username);
                break;
                
        }
        
    } while (select != 0);

   
    return 0;
}        
</pre>