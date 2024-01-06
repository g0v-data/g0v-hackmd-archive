/*30_2.UVa-1-分割 (Division of Nlogonia)(10.0)*/
#include <stdio.h>

void test(int n,int m,int n1,int n2){
    if(n1==n || n2==m) printf("divisa\n");
    else{
        if(n<n1){
            //右上
            if(n2>m) printf("NE\n");
            //右下
            else    printf("SE\n");
        }
        else{
            //左上
            if(n2>m) printf("NO\n");
            //左下
            else    printf("SO\n");
        }
    }
}

int main(){
    int K; scanf("%d",&K);
    while(K!=0){
        int n1,n2,N,M; scanf("%d %d",&N,&M);
        for(int i=1;i<=K;i++){
            scanf("%d %d",&n1,&n2);
            test(N,M,n1,n2);
        }
        scanf("%d",&K);
    }
    return 0;
}

/*30_4.UVa-1-降低成本 (Cost Cutting)(10.0)*/
#include <stdio.h>

int test(int s1,int s2,int s3){
    int result;
    if(s1>s2){
        if(s1<s3) result=s1; //s3>s1>s2
        else{
            if(s2>s3) result=s2; //s1>s2>s3
            else result=s3; //s1>s3>s2
        }
    }
    else{
        if(s2<s3) result=s2; //s3>s2>s1
        else{
            if(s3>s1) result=s3; //s2>s3>s1
            else result=s1; //s2>s1>s3
        }
    }
    return result;
}

int main(){
    int T; scanf("%d",&T);
    int s1,s2,s3;
    for(int i=1;i<=T;i++){
        scanf("%d %d %d",&s1,&s2,&s3);
        if((s1>=1000)&&(s1<=10000)&&(s2>=1000)&&(s2<=10000)&&(s3>=1000)&&(s3<=10000)){
            printf("Case %d: %d\n",i,test(s1,s2,s3));   
        }
    }
    return 0;
}

/*30_5.UVa-1-跳躍馬力歐 (Jumping Mario)(10.0)*/
#include <stdio.h>
int main(){
    int T;scanf("%d",&T);
    for(int i=1;i<=T;i++){
        int wall,low=0,high=0; scanf("%d",&wall);
        int jump1,jump2; scanf("%d",&jump1);
        for(int i=1;i<wall;i++){
            scanf("%d",&jump2);
            if(jump1>jump2) low++;
            else if(jump1<jump2) high++;
            jump1=jump2;
        }
        printf("Case %d: %d %d\n",i,high,low);
    }
    return 0;
}

/*30_6.UVa-1-恐怖衝刺 (Horror Dash)(10.0)*/
#include <stdio.h>
int main(){
    int t;scanf("%d\n",&t);
    for(int i=1;i<=t;i++){
        char n,max=0;
        while(1){
            scanf("%c",&n);
            if(n>max) max=n;
            if(n=='\n') break;
        }
        printf("Case %d: %c\n",i,max);
    }
    return 0;
}

/*30_7.UVa-1-伐木工排序 (Lumberjack Sequencing)(10.0)*/
#include <stdio.h>
int main(){
    int N;scanf("%d",&N);
    printf("Lumberjacks:\n");
    for(int i=1;i<=N;i++){
        int prenum,nownum;
        int Min_Max=1;
        int Max_Min=1;
        for(int i=1;i<=10;i++){
            if(i==1) scanf("%d",&prenum);
            else {
                scanf("%d",&nownum);
                if(nownum>prenum) Min_Max++;
                else if(nownum<prenum) Max_Min++;
                prenum=nownum;   
            }
        }
        if(Min_Max==10 || Max_Min==10) printf("Ordered\n");
        else printf("Unordered\n");
    }
    return 0;
}

/*30_8.UVa-1-調皮的孩子 (Mischievous Children)(10.0)*/
#include <stdio.h>

int fac(int n){
    int sum=1;
    for(int i=1;i<=n;i++){
        sum*=i;
    }
    return sum;
}

int data(char array[],int sum){
    int divid=1;
    for(int i=0;i<sum;i++){   //計算字母重複字數
        int renum=0;
        if(array[i]=='0') continue;
        for(int j=i+1;j<sum;j++){
            if(array[i]==array[j]){
                if(renum==0) renum=2;
                else renum++;
                array[j]='0';
            }
        }
        if (renum!=0)divid*=fac(renum);
    }
    return fac(sum)/divid;
}

int main(){
    int n;scanf("%d\n",&n);
    for(int i=1;i<=n;i++){
        char array[20];
        int index=0;
        while(1){
            char letter;
            scanf("%c",&letter);
            array[index]=letter;
            if(letter=='\n') break;
            index++;
        }
        printf("Data set %d: %d\n",i,data(array,index));
    }
    return 0;
}

/*30_9.UVa-1-密碼鎖 (Combination Lock)(20.0)*/
#include <stdio.h>
int main(){
    int first,n1,n2,n3;
    scanf("%d %d %d %d\n",&first,&n1,&n2,&n3);
    while((first!=n1 || n1!=n2 || n2!=n3)){
        if(first+n1+n2+n3==0) break;
        int cost=120;
        cost += (40+first-n1)%40;
		cost += (40+n2-n1)%40;
		cost += (40+n2-n3)%40;
		printf("%d\n",cost*9);
		scanf("%d %d %d %d\n",&first,&n1,&n2,&n3);
    }
    return 0;
}

/*31_1.UVa-2-幼稚園數數遊戲 (Kindergarten Counting Game)(10.0)*/
#include <stdio.h>
#include <string.h>

int main(){
    char input[100];
    while(scanf("%[^\n]",input)){
        int space=0;
        for(int i=0;i<strlen(input);i++){
            if(input[i]==' ') space++;
        }
        printf("%d\n",space+1);
    }
}