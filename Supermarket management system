#include<stdio.h>
#include<stdlib.h>
#include<windows.h>
#include<string.h>
#include<conio.h>
#include<ctype.h> 
#include<math.h> 
#include<time.h>
#define Maxamount 10 /*每个超市货物量*/
#define Shopnum 3 /*总超市数量*/  
int A=Maxamount*Shopnum;
struct fORDER  //文件中顾客查询到的付款订单信息 
{
char fcID[11];
char forderID[26];
char fdate[16];
char fitemID[7];
char fitemname[20];
int fitemNum;
float fprice;
float fsumprice;
}forder;

struct fNORDER  //文件中顾客查询到的未付款订单信息 
{
char fcID[11];
char forderID[26];
char fdate[16];
char fitemID[7];
char fitemname[20];
int fitemNum;
float fprice;
float fsumprice;
}fnoorder;

struct customerx       //顾客信息输入 
{
	char cID[11];
	char cname[20];
	char csex[20];
	char cphonenumber[12];
	char cpassword[20];
	char cemail[20];
    char caddress[20];  
    float cbalance;
}customerx1;
struct fcustomer       //文件中顾客信息
{
	char fcID[11];
	char fcname[20];
	char fcsex[20];
	char fcphonenumber[12];
	char fcpassword[20];
	char fcemail[20];
    char fcaddress[20];  
    float fcbalance;
}fcustomer1;

struct customer
{
	char customerID[10];
	char name[20];
	char sex[20];
	char phonenumber[12];
	char password[20];
	char email[20];
    char address[20];  
    float balance[20];//账户余额 
};

struct CUSTOMER
{
	char customerID[10];
	char name[20];
	char sex[20];
	char phonenumber[12];
	char password[20];
	char email[20];
    char address[20]; 
	float money; 
}user[1000];  

struct user//用户输入的用户信息 
{             
	char ucustomerID[10];
	char uname[20];
	char usex[20];
	char uphonenumber[12];
	char upassword[20];
	char uemail[20];
    char uaddress[20];  
    float ubalance[20];
}user1;
struct admi
{              //输入的管理员信息 
		char aid[10];
		char aname[20];
		char achao[20]; 
		char acode[10];
		char amail[30];
}admi1;
 struct order
{
	char orderID[27];
	char date[18];
	char itemID[7];
	char itemname[81];
	int itemNum;
	float price,sumprice,cost;
} ;/*超市订单结构*/


struct fadmi
{                 //文件中管理员信息 
		char faid[10];
		char faname[20];
		char fachao[20];
		char facode[10];
		char famail[30];
}fadmi1;
struct Goods	//商品信息 
{
	char num[7];//ID 
	char name[100];//名称 
	char chaoshi[100];//超市名称 
	float cost;//进价 
	float price;//售价 
	int sale;//销量 
	int kucun;//库存 
	float discount;//折扣价 
	int year1;/*折扣开始时间 */ 
	int month1;
	int day1;
	int hour1;
	int min1;
	int year2;/*折扣结束时间 */ 
	int month2;
	int day2;
	int hour2;
	int min2;
}good;

void findGoodname(char []);/*<商品名称查找>函数原型*/ 
void findShopname(char []);/*<超市名称查找>函数原型*/ 
void findgoodDiscount(char [81],char [11]);/*<商品+折扣过滤>函数*/
void findshopDiscount(char [81],char [11]);/*<超市+折扣过滤>函数*/ 
void findDiscount(char ID[11]);//按是否有折扣筛选商品 
void confirmBuy(char [81],int,int,char [11]);/*写购买物品的系列函数*/
float zhekou(float,float,int,int,int,int,int,int,int,int,int,int);/*判断打不打折的函数*/
void goumai(char ID[11]);//购买商品 
void rankPrice(char ID[11]);//<按价格排序>函数
void rankSale(char ID[11]);//<按销量排序>函数
void rank_tuijian(char ID[11]);//推荐排序商品 
void userlogin(char ID[81]);//用户登录 
int uidverification(char ID[8]);//顾客ID验证 
void userRegister();//顾客注册 
void userchoose(char ID[81]);//用户主页面 
void customer_menu(char ID[11]);//用户信息变更 
void cusSetpassword(char ID[11]); //顾客改密码 
void cusSetphonenumber(char ID[11]);//顾客改电话 
void cusSetemail(char ID[11]);   //顾客改邮箱
void cusSetaddress(char ID[11]);//顾客改地址 
void cusbalancemanage(char ID[11]);//顾客账户充值 
void customer_ordermenu(char ID[11]);//查看顾客订单页面 
void seecustomer_order(char ID[11]);//查看已付款订单
void cancelcustomer_order(char ID[11]);//取消未付款订单 
void checkShoporder(char[]); //查询所属超市商品订单函数 
void yingyee(char []);//统计营业额函数
void paixv(char[]);//排序函数
void lirun(char[]);//输出利润最高和最低的商品 
void change_goods(char[]);//根据销量判断进货和滞销情况 
void jiemian(char[]);//统计用户订单信息 
void admilogin(char ID[81]);  //管理员登录 
int aidverification(char ID[81]);   //管理员ID验证 
void admiSetcode(char ID[81]);  //管理员改密码 
void admiSetmail(char ID[81]);//管理员改邮箱
void admichoose(char ID[81]);  //管理员主页面  
void ainformation(char ID[81]);//管理员改信息 
void addGoods(char[]);//管理员添加商品 
void goodSearch(char[]);//管理员查看商品信息 
void gouwu_jiemian(char[]);//购物界面 

 int main()            //主函数
{

	int i,j=0;
	
do{
	printf("                 ********************************************\n");  
	printf("                 *                                          *\n");
	printf("                 *           欢迎来到网上超市系统           *\n");
	printf("                 *                                          *\n");
	printf("                 *                                          *\n");
	printf("                 *                                          *\n");
	printf("                 ********************************************\n");
	printf("\t\t\t\t1	管理员登录\n\n");
	printf("\t\t\t\t2	用户登录\n\n");
	printf("\t\t\t\t3	用户注册\n\n");
	printf("\t\t\t\t4	退出\n\n");
    printf("                              请输入您的选择：");
	scanf("%d",&i);
    getchar();

	
	if(i==1)
	{
		system("cls");
		int flag;
	    char ID[81];
     	while(1)   //管理员登录 
    	{
	    	system("cls");
	    	printf(""); 
    		printf("\n********************************* 登 录 界 面 *********************************\n\n");
	    	printf("\t\t\t\t请输入您的账号：");
	        scanf("%s",ID);
		    flag = aidverification(ID);
	
		    if (flag == 2)
		    break;
		
		    if(flag == 1) 
  	       {
  		        printf("\n\t\t\t\t账号不存在，请核实后重新输入...\n\n");
     	        system("pause");
	       }
	    }

	    admilogin(ID);//管理员登录 
	    admichoose(ID);//管理员主页面
	    
    }  
    else if(i==2)
	{
		system("cls");
		int flag;
	    char ID[8];
	    while(1)
	    {
		    system("cls");
		    printf("\n********************************* 登 录 界 面 *********************************\n\n");
		    printf("\t\t\t\t请输入您的账号：");
	        scanf("%s",ID);
		    flag = uidverification(ID);
	
		    if (flag == 2)
		       break;
		
		    if(flag == 1) 
  	        {
  		        printf("\n\t\t\t\t账号不存在，请核实后重新输入...\n\n");
     	        system("pause");
	        }
	    }
	
		userlogin(ID);
		userchoose(ID);
		
	}	
	else if(i==3)
	{
		system("cls");
	 	userRegister();
	 	
		int flag;
	    char ID[8];
	    while(1)
	    {
		    system("cls");
		    printf("\n********************************* 登 录 界 面 *********************************\n\n");
		    printf("\t\t\t\t请输入您的账号：");
	        scanf("%s",ID);
		    flag = uidverification(ID);
	
		    if (flag == 2)
		       break;
		
		    if(flag == 1) 
  	        {
  		        printf("\n\t\t\t\t账号不存在，请核实后重新输入...\n\n");
     	        system("pause");
	        }
	    }
	
		userlogin(ID);
	    userchoose(ID);
	}
	
	else if(i==4)  //退出 
	{
		system("cls");
		printf("           ****************************************************\n");
		printf("           *                                                  *\n");
		printf("           *               谢谢使用网上超市系统！             *\n");
		printf("           *                                                  *\n");
		printf("           ****************************************************\n");
		exit(0);
	}	
	else //容错 
	{
		printf("                       输入错误请重新输入！\n");
		system("pause");
		system("cls");
	}
}while((i != 1)&&(i !=2)&&( i != 3)&&(i!=4));
	
}


void admichoose(char ID[81])        //管理员主页面 
 {
 	int choose_flag=1;
 	while(choose_flag)
 	{
	 	system("cls");
	    printf("\n******************************** 管 理 员 界 面 ********************************\n\n");
	    printf("\n\t\t\t\t管理员功能：\n\n");
	 	printf("\t\t\t\t1	查询商品\n\n");
		printf("\t\t\t\t2	添加商品\n\n");
		printf("\t\t\t\t3	查看用户订单\n\n");
		printf("\t\t\t\t4	个人信息管理\n\n");
		printf("\t\t\t\t5	统计用户订单信息\n\n");
		printf("\t\t\t\t6	退出\n\n");
		
		printf("\t\t\t\t请输入您的操作选项：");
		getchar();
		char choice;
		int flag = 1;
	
		scanf("%c", &choice);
	
		switch(choice)
		{
			case '1' :
				{
					goodSearch(ID);
					break; 
				}
			
			case '2' :
				{
					addGoods(ID);
					break; 
				}
				
			case '3':
				{
				  checkShoporder(ID); 
				  break; 
				}
			
			case '4':
				{
					//管理员个人信息修改 
					void ainformation(char ID[81]);
					ainformation(ID);
					break;
				}
			case '5':
				{
					jiemian(ID);
					break; 
				}
			case '6':
			{	
				choose_flag=0;
					exit(1);
						break;
			}
			
			default :
				{
				
					printf("                       输入错误请重新输入！\n");
					system("pause");
					system("cls");
					break;
				}		
		}
	}
} 
int aidverification(char ID[81])    //验证管理员ID 
{
	int flag1; 
	FILE*fadmi;
	fadmi = fopen("admi.txt","r");    //打开储存管理员信息的文件 
	if (fadmi == NULL)
	  printf("无法打开此文件");
	
	while( (fscanf(fadmi,"%s%s%s%s%s",fadmi1.faid, fadmi1.faname, fadmi1.fachao, fadmi1.facode, fadmi1.famail))  !=EOF)
  	{
		if(strcmp(ID, fadmi1.faid)==0)
		{   
			flag1 = 2;
			printf("\n\t\t\t\t账号合法，请继续...\n\n");
			
            system("pause");
			break;
			system("cls");
		}
	
		if(strcmp(ID, fadmi1.faid)!=0)
			flag1 = 1;	
  	}

	return flag1;
}

void admiSetcode(char ID[81])//修改管理员密码
{
    
	system("cls");
	
    FILE *inFile,*p;
	char code1[81],code2[81];
 
 	FILE *fadmi= fopen("admi.txt","a+");      //打开储存管理员信息的文件 
 	FILE *newinfo = fopen("temp.txt","w");
    
		do{
			printf("\t\t\t\t请输入你的新登录密码：\n\n");
			scanf("%s", code1);

			printf("\t\t\t\t请再次确认你的新登录密码：\n\n");
			scanf("%s", code2);

			if(strcmp(code1,code2)!=0)
			{
				printf("\n\t\t\t\t两次输入不相符，请核对后输入...\n\n");
				system("pause");
				system("cls");
			}
			else
				break;
		}while(1);
  				
			if(fadmi==NULL)
	  	    printf("\n\t\t\t\t文件打开失败！\r\n");

			while( (fscanf(fadmi,"%s %s %s %s %s",fadmi1.faid,fadmi1.faname,fadmi1.fachao,fadmi1.facode,fadmi1.famail)) !=EOF)
  			{
				if(strcmp(ID, fadmi1.faid)==0)
			  	  	fprintf(newinfo,"%s %s %s %s %s \n",fadmi1.faid,fadmi1.faname,fadmi1.fachao,code1,fadmi1.famail);
					
				if(strcmp(ID, fadmi1.faid)!=0)
					fprintf(newinfo,"%s %s %s %s %s \n",fadmi1.faid,fadmi1.faname,fadmi1.fachao,fadmi1.facode,fadmi1.famail);
  			}     //将新密码写入对应ID相同的那一行 
  	
	fclose(fadmi);
	fclose(newinfo);
	FILE *ori = fopen("admi.txt","w");
 	FILE *newi = fopen("temp.txt","a+");

	while(fscanf(newi,"%s%s%s%s%s",fadmi1.faid,fadmi1.faname,fadmi1.fachao,fadmi1.facode,fadmi1.famail) != EOF)
  			{
				fprintf(ori,"%s %s %s %s %s\n",fadmi1.faid,fadmi1.faname,fadmi1.fachao,fadmi1.facode,fadmi1.famail);
  			}
  			
  	printf("\t\t\t\t新密码修改成功！\n\n");
  	printf("\t\t\t\t返回上一级~~~~\n") ; 
  			
	fclose(ori);
	fclose(newi);
  	system("pause");
  	void ainformation(char ID[81]);
  	ainformation(ID);

}
  			
void admiSetmail(char ID[81]) //修改管理员邮箱 
{
	 
	system("cls");
	char mail1[81];
 	FILE *fadmi = fopen("admi.txt","a+");
 	FILE *newinfo = fopen("temp.txt","w");	
	int i,a,b,yorn1,yorn2,yorn3;
while (1)
			{
				yorn1 = 0;
				yorn2 = 0;
				yorn3 = 0;
				
				printf("\n\t\t\t\t请输入您的邮箱地址(****@***.***):");
				scanf("%s",mail1);                                //检查邮箱格式是否正确 
				for (i = 0;i < strlen(mail1);i++)
				{
					if (mail1[i] == '@'&&i != 0)
					{
						yorn1 = 1;
						a = i;
					}
					if (mail1[i] == '.'&&i != (strlen(mail1) - 1))
					{
						yorn2 = 1;
						b = i;
					}
				}
				if (b-a>1)
					yorn3 = 1;
		
				if(yorn1 == 1 &&yorn2 == 1&&yorn3 ==1)
					break;
				else 
					printf("\n\t\t\t\t您的邮箱地址格式有误，需重新输入");
			}
  			
			if(fadmi==NULL)
	  	    printf("\n\t\t文件打开失败！\r\n");
			while( (fscanf(fadmi,"%s%s%s%s%s",fadmi1.faid,fadmi1.faname,fadmi1.fachao,fadmi1.facode,fadmi1.famail))  !=EOF)
  			{
				if(strcmp(ID, fadmi1.faid)==0)
			  	  	fprintf(newinfo,"%s %s %s %s %s \n",fadmi1.faid,fadmi1.faname,fadmi1.fachao,fadmi1.facode, mail1);
					
				if(strcmp(ID, fadmi1.faid)!=0)
					fprintf(newinfo, "%s %s %s %s %s \n",fadmi1.faid,fadmi1.faname,fadmi1.fachao,fadmi1.facode,fadmi1.famail);
  			 }
  			 
    fclose(fadmi);
	fclose(newinfo);
	FILE *ori = fopen("admi.txt","w");
 	FILE *newi = fopen("temp.txt","a+");

	while(fscanf(newi,"%s %s %s %s %s",fadmi1.faid, fadmi1.faname, fadmi1.fachao, fadmi1.facode, fadmi1.famail) != EOF)
  			{
				fprintf(ori,"%s %s %s %s %s\n",fadmi1.faid, fadmi1.faname, fadmi1.fachao, fadmi1.facode, fadmi1.famail);
  			}   //将新邮箱写入对应ID相同的那一行 
  			
  	printf("\t\t\t\t新邮箱修改成功！\n\n");
  	
  	printf("\t\t\t\t返回上一级~~~~") ; 		
	fclose(ori);
	fclose(newi);
	system("pause");
  	void ainformation(char ID[81]);
  	ainformation(ID);

}
void ainformation(char ID[81]) //管理员信息修改主界面 
{
	/*信息修改*/
	system("cls");
	int choice;
	
	printf("********************************** 信 息 修 改 *********************************\n\n");
	printf("\t\t\t\t①修改登录密码\n\n"); 
	printf("\t\t\t\t②修改联系邮箱\n\n");
	printf("\t\t\t\t③返回上一级\n\n") ;
	printf("\t\t\t\t请选择修改项目:\n\n");
	scanf("%d",&choice);
	
	switch(choice)
	{
		case 1 :
			{
				admiSetcode(ID);
			    break;
			}
			
        case 2:
        	{
        		admiSetmail(ID);
				break; 	
			}
            
        case 3:
        	{
        		admichoose(ID);
	        	break;
	        }
            
			 
        default:
          printf("\n\t\t\t\t输入不合法，请再次输入...\n"); 
          system("pause");
          //又回到这个函数 
          
       	  void ainformation(char ID[81]);
  	      ainformation(ID);
          
	}
}	 
void admilogin(char ID[81]) //管理员登陆 
{
	system("cls");
	
	int i,j;

	 printf("\n********************************* 欢 迎 登 录 *********************************\n\n");
	printf("\n\t\t\t\t请输入密码：");/*输入密码*/
		//后退键不会显示星号 
    char ch;
	int p;
	p = 0;
	        
    while((ch=getch())!='\r')
    {  
        if(ch==8)
        {  
            putchar('\b');  
            putchar(' ');  
            putchar('\b');  
            if(p>0)
            p--;  
        }  
        if(!isdigit(ch)&&!isalpha(ch))
            continue;  
            putchar('*');
            admi1.acode[p++]=ch;
    }  
        admi1.acode[p]=0;

	/*从文件中查找正确的账号密码*/
	FILE *fadmi;
	fadmi = fopen("admi.txt","r");
	if(fadmi == NULL)
	  printf("\t\t\t\t无法打开此文件！"); 
	fscanf(fadmi,"%s%s%s%s%s",fadmi1.faid,fadmi1.faname,fadmi1.fachao,fadmi1.facode,fadmi1.famail);
	
	int flag = 0;
	while(!feof(fadmi))
	{
		if(strcmp(ID,fadmi1.faid)==0  && strcmp(admi1.acode,fadmi1.facode)==0)
		{
		    flag = 1;
		    printf("\n\n\t\t\t\t成功登录！");
		    break;
	    }
		fscanf(fadmi,"%s%s%s%s%s",fadmi1.faid,fadmi1.faname,fadmi1.fachao,fadmi1.facode,fadmi1.famail);
   }
	
	if (flag == 0)
	{
		printf("\n\n\t\t\t\t账号或密码错误，请重新输入...");
		printf("\n\n\t\t\t\t您将会有3次输入机会...\n\n");
		system("pause"); 
		system("cls");
		
		for(j = 3; j >= 1; j-- )
		{
			printf("\n*********************************欢 迎 登 录*********************************\n\n");/*22个星号*/
	        printf("\n\t\t\t\t密码：");/*输入密码*/
           	char ch;
	        int p;
	        p = 0;
	        
           	while((ch=getch())!='\r')
           {  
            if(ch==8)
                {  
                    putchar('\b');  
                    putchar(' ');  
                    putchar('\b');  
                    if(p>0)
                    p--;  
                }  
            if(!isdigit(ch)&&!isalpha(ch))
                continue;  
            putchar('*');
            admi1.acode[p++]=ch;
           }  
            admi1.acode[p]=0;
	        
        	FILE *fadmi;
         	fadmi = fopen("admi.txt","r");
        	fscanf(fadmi,"%s%s%s%s%s",fadmi1.faid, fadmi1.faname, fadmi1.fachao,fadmi1.facode, fadmi1.famail);
	
        	while(!feof(fadmi))
        	{
        		if(strcmp(ID,fadmi1.faid)==0  && strcmp(admi1.acode,fadmi1.facode)==0)
	          	{
		            printf("\n\n\t\t\t\t成功登录！");
		            flag = 1;
		            break; 
	            }
	            
	           	fscanf(fadmi,"%s%s%s%s%s",fadmi1.faid, fadmi1.faname,fadmi1.fachao, fadmi1.facode, fadmi1.famail);
        	}
            
            if(flag == 1)
              break;	
        	
            if(flag != 1)
            {
		    	printf("\n\n\t\t\t\t账号或密码错误，请重新输入...\n\n");
                printf("\t\t\t\t您还有%d次输入机会...\n\n",j-1);
                system("pause");
                system("cls");
	        }   
	        if (flag == 1) break;
		}
		
		if(flag == 1)
		{
			printf("haha");
		}
		   
		if(flag != 1)
		{
		    printf("\n\n\t\t\t\t您已没有机会再次输入...\n\n");
		    printf("\t\t\t\t系统将自动退出...\n\n");
		    system("pause");
		    exit(1);
		} 
	}
}
void jiemian(char ID[])
{   int a;
system("cls");

printf("\t\t\t\t1	排序\n\n") ;
printf("\t\t\t\t2	输出利润最高和最低的商品\n\n") ;
printf("\t\t\t\t3	输出需要进货和滞销的商品\n\n") ;
printf("\t\t\t\t4	统计营业期间的营业额\n\n") ;
printf("\t\t\t\t5	返回上一级\n\n") ;

	scanf("%d",&a);
	
	switch(a)
	{
		case 1:
			{
				paixv(ID);
				break;
			}
			case 2:
			{
				lirun(ID);
				jiemian(ID);
				break;
			}
			case 3:
			{
				change_goods(ID);
				jiemian(ID);
				break;
			}
			case 4:
			{
				yingyee(ID);
				jiemian(ID);
				break;
			}
			case 5:
			{
				admichoose(ID);
				break;
			}
			
			default :
				{
					printf("                       输入错误请重新输入！\n");
					system("pause");
					jiemian(ID);
					break;
				}				
	}
	system("pause");
}
void addGoods(char ID[81])//添加商品 
{
	int add_flag=1;
	while(add_flag)
	{
			char num[7];
			char name[100];
			char chaoshi[20];
			float cost;//进价 
			float price;//售价 
			int sale;//销量
			int kucun;
			float discount;//折扣价 
			int year1,year2,month1,month2;
			int day1,day2,hour1,hour2,min1,min2;
			char x;
			char s[1024];
			FILE *fp1;
			sprintf(s,"%s.txt",ID);
			fp1=fopen(s,"a+"); 
			system("cls");
			printf("\n\t\t请输入新商品的号码（2字母4数字）：");
		    int flag=1;
		    while(flag)//检查格式 
		    {
			    scanf("%s",num);
		 	 	if(isalpha(num[0])&&isalpha(num[1])&&isdigit(num[2])&&isdigit(num[3])&&isdigit(num[4])&&isdigit(num[5])&&num[6]=='\0')
			    { 
				    fp1=fopen(s,"a+");
					flag=0;
				    while(fscanf(fp1,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d",good.num,good.name,good.chaoshi,&good.cost,&good.price,
					  &good.sale,&good.kucun,&good.discount,&good.year1,&good.month1,&good.day1,&good.hour1,&good.min1,
					  &good.year2,&good.month2,&good.day2,&good.hour2,&good.min2)!=EOF)//检查是否重复 
					{
						if(strcmp(num,good.num)==0)
						{
							printf("\n\t\t商品号码重复	请输入新商品的号码：");
							flag=1;
							break;
						}  
					}
			    	fclose(fp1);
				} 
		        else 
				{ 
					printf("\n\t\t格式错误，请重新输入新商品的号码（2字母4数字）：");
			       	flag=1;
				} 
		    }
			printf("\n\t\t请输入新商品的名称：");
			int a=1;
			while(a==1)
			{
				scanf("%s",name);
				a=0;
				fp1=fopen(s,"a+");
				while(fscanf(fp1,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d",good.num,good.name,good.chaoshi,&good.cost,&good.price,
				  &good.sale,&good.kucun,&good.discount,&good.year1,&good.month1,&good.day1,&good.hour1,&good.min1,
				  &good.year2,&good.month2,&good.day2,&good.hour2,&good.min2)!=EOF)
				{
					if(strcmp(name,good.name)==0)
					{
						printf("\n\t\t商品名重复	请输入新商品的名称：");
						a=1;
						break;
					}  
				}
				fclose(fp1);
			}
			
			printf("\n\t\t请输入商品进价："); 
			scanf("%f",&cost);
			printf("\n\t\t请输入商品售价："); 
			scanf("%f",&price);
			printf("\n\t\t请输入商品销量："); 
			scanf("%d",&sale);
			printf("\n\t\t请输入商品库存：");
			int b=1;
			while(b==1)
			{
			
			scanf("%d",&kucun);
			if(kucun<0)
			{
				printf("\n\t\t库存不能为负数	请重新输入");
				b=1;
		    }
		    else b=0;
		   }
			printf("\n\t\t请输入商品折扣价："); 
			scanf("%f",&discount);
			printf("\n\t\t请输入商品折扣开始时间（年 月 日 小时（24小时制） 分）："); 
			scanf("%d %d %d %d %d",&year1,&month1,&day1,&hour1,&min1);
			printf("\n\t\t请输入商品折扣结束时间（年 月 日 小时（24小时制） 分）："); 
			scanf("%d %d %d %d %d",&year2,&month2,&day2,&hour2,&min2);
			printf("\n\t\t是否还需要重新修改或者直接发布\n");
			printf("\n\t\t1.重新修改\n");
			printf("\n\t\t2.直接发布\n");
			printf("\n\t\t3.取消发布\n");
			printf("\n\t\t请选择:");
			int flag1=1;
			while(flag1)
			{
				getchar();
				scanf("%c",&x);
				if(x=='1')
					flag1=0;
				else if(x=='2')
				{
					fp1=fopen(s,"a+");
				    fprintf(fp1,"%s %s %c %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",num,name,ID[0],cost,price,sale,
					 	kucun,discount,year1,month1,day1,hour1,min1,year2,month2,day2,hour2,min2); 
				    fclose(fp1);
					printf("\n\n\t\t系统将返回上一级...\n\n");
					system("pause");
					flag1=0;
					add_flag=0;
				}
				else if(x=='3')
				{
					printf("\n\t\t将取消发布");
					printf("\n\n\t\t系统将返回上一级...\n\n");
					system("pause");
					add_flag=0;
					flag1=0; 
				} 
			    else
			    {
					printf("\n\t\t没有此选项，请重新输入："); 
				    flag1=1;
				}
		    }
	}
}

void goodSearch(char ID[81])//商品查询 
{
	FILE *fp1;
	char s[1024]; 
	sprintf(s,"%s.txt",ID);  //根据输入的员工ID，打开对应的文件 ，其中包含商品信息 
	fp1=fopen(s,"r"); 
	system("cls");
	printf("商品编号	商品名	  所属超市	进价	售价	销量	库存	折扣价	开始时间		结束时间\n");
	while((fscanf(fp1,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d",good.num,good.name,good.chaoshi,&good.cost,&good.price,
	  &good.sale,&good.kucun,&good.discount,&good.year1,&good.month1,&good.day1,&good.hour1,&good.min1,
	  &good.year2,&good.month2,&good.day2,&good.hour2,&good.min2))!=EOF)
	{
		printf("%s\t\t%-14s%s\t\t%.2f\t%.2f\t%d\t%d\t%.2f\t%d:%d:%d:%d:%d\t\t%d:%d:%d:%d:%d\n",good.num,good.name,good.chaoshi,
			good.cost,good.price,good.sale,good.kucun,good.discount,good.year1,good.month1,good.day1,good.hour1,good.min1,
			good.year2,good.month2,good.day2,good.hour2,good.min2);
	}
	printf("\n\n系统将返回上一级...\n\n");
	system("pause");
	admichoose(ID);
}

void paixv(char ID[])/*排序函数*/ 
{
	
	int i=0,a,j,k,b,h,n;
	struct order order1[1000];
	struct order t1;
	char s[10];
	FILE *outFile;
	sprintf(s,"Shop%c.txt",ID[0]);
	outFile=fopen(s,"r");
	system("cls");
	while(fscanf(outFile,"%s%s%s%s%d%f%f%f",order1[i].orderID,order1[i].date,order1[i].itemID,order1[i].itemname,&order1[i].itemNum,&order1[i].price,&order1[i].sumprice,&order1[i].cost)!=EOF)
		i++;
	printf("\n欢迎来到商品排序页面!\n按销量排序请按“1”\n按营业额排序请按“2”\n");
	scanf("%d",&a); 
	switch(a)
	{
		case 1:
		for(j=0;j<=i-1;j++)
		{
			for(k=0;k<=i-2-j;k++)
			{
				if(order1[k].itemNum<order1[k+1].itemNum)
				{
					t1=order1[k];
					order1[k]=order1[k+1];
					order1[k+1]=t1;
				}
			}
		}
		printf("订单号			购物日期		商品号		商品名称		商品数量	单价	总价\n");
		for(k=0;k<i;k++)
			printf("%s\t%s\t%s\t\t%-18s\t%d\t\t%.2f\t%.2f\n",order1[k].orderID,order1[k].date,order1[k].itemID,order1[k].itemname,order1[k].itemNum,order1[k].price,order1[k].sumprice);
		printf("\n返回上一级请按“3”\n退出请按“4”\n");
		scanf("%d",&n);
		switch(n)
		{
			case 3:
			paixv(ID);
			break;
			case 4:
				{
					
					jiemian(ID);
					break;
				}
		
			default:
			{
				
			printf("\n抱歉！页面走丢了！\n");
			paixv(ID);
			break;
		}
		}
		break;
		case 2:
		for(j=0;j<=i-1;j++)
		{
			for(k=0;k<=i-2-j;k++)
			{
				if(order1[k].sumprice<order1[k+1].sumprice)
				{
					t1=order1[k];
					order1[k]=order1[k+1];
					order1[k+1]=t1;
				}
			}
		}
		printf("订单号			购物日期		商品号		商品名称		商品数量	单价	总价\n");
		for(k=0;k<i;k++)
			printf("%s\t%s\t%s\t\t%-18s\t%d\t\t%.2f\t%.2f\n",order1[k].orderID,order1[k].date,order1[k].itemID,order1[k].itemname,order1[k].itemNum,order1[k].price,order1[k].sumprice);
		printf("\n返回上一级请按“3”\n退出请按“4”\n");
		scanf("%d",&n);
		switch(n)
		{
			case 3:
			paixv(ID);
			break;
			case 4:
			{
				jiemian(ID);
				break;
			}
			default:
			{
				
			printf("\n抱歉！页面走丢了！\n");
			paixv(ID);
			break;
		}
		}
		break;
	default:
			{
				
			printf("\n抱歉！页面走丢了！\n");
			paixv(ID);
			break;
		}
	}
	fclose(outFile);
	system("pause");
}

void lirun(char ID[])/*输出利润最高和最低的商品*/
{
	struct order order1[1000];
	int i=0,j,maxb,minb; 
	float max,min;
	float li[1000];
	FILE *inFile;
	char s[10];
	sprintf(s,"Shop%c.txt",ID[0]);
	inFile=fopen(s,"r");
system("cls");
	while(fscanf(inFile,"%s %s %s %s %d %f %f %f",order1[i].orderID,order1[i].date,order1[i].itemID,order1[i].itemname,&order1[i].itemNum,&order1[i].price,&order1[i].sumprice,&order1[i].cost)!=EOF)
	{
		li[i]=order1[i].itemNum*(order1[i].price-order1[i].cost);	
		i++;
	}
	
	max=li[0];
	maxb=0;
	for(j=0;j<i;j++)//找最高利润商品 
	{
		if(li[j]>max)
		{
			max=li[j];
			maxb=j;
		}
	}
	printf("\n输出利润最高的商品:\n");
	printf("商品号	商品名称		商品数量	单价	利润\n"); 
	printf("%s\t%-20s\t%d\t\t%-.2f\t%-.2f\n",order1[maxb].itemID,order1[maxb].itemname,order1[maxb].itemNum,order1[maxb].price,li[maxb]); 
	for(j=0;j<i;j++)
	{
		if(li[j]==li[maxb]&&j!=maxb)
			printf("%s\t%-20s\t%d\t\t%-.2f\t%-.2f\n",order1[j].itemID,order1[j].itemname,order1[j].itemNum,order1[j].price,li[j]);
	}
	min=li[0];
	minb=0;
	for(j=0;j<i;j++)//找最低利润商品 
	{
		if(li[j]<min)
		{
			min=li[j];
			minb=j;
		}
	}
 	printf("\n输出利润最低的商品:\n");
	printf("商品号	商品名称		商品数量	单价	利润\n"); 
	printf("%s\t%-20s\t%d\t\t%-.2f\t%-.2f\n",order1[minb].itemID,order1[minb].itemname,order1[minb].itemNum,order1[minb].price,li[minb]); 
 	int q;
 	for(q=0;q<i;q++)
	{
		if(li[q]==li[minb]&&q!=minb)
			printf("%s\t%-20s\t%d\t\t%-.2f\t%-.2f\n",order1[q].itemID,order1[q].itemname,order1[q].itemNum,order1[q].price,li[q]);
	}
	fclose(inFile);
	system("pause");
}
void checkShoporder(char ID[])/*查询所属超市商品订单函数(需要诗语订单名称）*/ 
{
	int i=0;
	char s[10];
	FILE *outFile;
	sprintf(s,"Shop%c.txt",ID[0]);
	outFile=fopen(s,"r");
	struct order order[1000];
system("cls");
	if(outFile==NULL)
	{	
		printf("\n抱歉！页面走丢了！\n");
		exit(1);
	}
	printf("订单号			购物日期		商品号		商品名称		商品数量	单价	总价\n");
	while(fscanf(outFile,"%s %s %s %s %d %f %f %f",order[i].orderID,order[i].date,order[i].itemID,order[i].itemname,&order[i].itemNum,&order[i].price,&order[i].sumprice,&order[i].cost)!=EOF)
	{
		printf("%s\t%s\t\t%s\t\t%-18s\t%d\t\t%.2f\t%.2f\n",order[i].orderID,order[i].date,order[i].itemID,order[i].itemname,order[i].itemNum,order[i].price,order[i].sumprice);
		i++;
	}
	fclose(outFile);
	system("pause");
} 
void change_goods(char ID[])//根据销量判断进货和滞销情况 
{
	struct Goods good[1000];
	int a,i=0,j,k,b=0,c=0;
	int sum[1000];//初始库存 
	char s[10];
	FILE *outFile;
	sprintf(s,"%s.txt",ID);
	outFile=fopen(s,"r");
	system("cls");
	
	while(fscanf(outFile,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,&good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,&good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
	{
		sum[i]=good[i].sale+good[i].kucun;
		i++;
	}

	
	printf("\n滞销的商品有：\n"); 
	printf("\n商品号	商品名称	商品销量	单价\n");
	for(j=0;j<i;j++)
	{
		if(good[j].sale<=(sum[j]*1/3))
		{
			printf("%s\t%s\t\t%d\t\t%-.2f\n",good[j].num,good[j].name,good[j].sale,good[j].price);
			c=1;
		}
	}
	if(c!=1)
		printf("\n无滞销商品\n");
	printf("\n需进货的商品有：\n"); 
	printf("\n商品号	商品名称	商品销量	单价\n"); 
	for(k=0;k<i;k++)
	{
		if(good[k].sale>=(sum[k]*2/3))
		{
			printf("%s\t%s\t\t%d\t\t%-.2f\n",good[k].num,good[k].name,good[k].sale,good[k].price);
			b=1;
		}
	}
	if(b!=1)
		printf("\n无脱销商品\n");
	fclose(outFile);
	system("pause");
} 
void yingyee(char ID[])/*统计营业额函数*/
{
	int i=0;
	float sum=0;
	struct 
	{
		char orderID[27];
		char date[18];
		char itemID[7];
		char itemname[81];
		int itemNum;
		float price,sumprice,cost;
	} order[1000];
	char s[10];
	FILE *outFile;
	sprintf(s,"Shop%c.txt",ID[0]);
	outFile=fopen(s,"r");
	system("cls");
	if(outFile==NULL)
	{	
		printf("\n抱歉！页面走丢了！\n");
		exit(1);
	}
	printf("\n营业期间营业额为：\n");
	while(fscanf(outFile,"%s%s%s%s%d%f%f%f",order[i].orderID,order[i].date,order[i].itemID,order[i].itemname,&order[i].itemNum,&order[i].price,&order[i].sumprice,&order[i].cost)!=EOF)
	{
		sum=sum+order[i].sumprice;
		i++;
	}
	printf("%.2f",sum);
	fclose(outFile);
	system("pause");
}
void userlogin(char ID[81]) //用户登录 
{
	system("cls");
	struct customer user; 
	int i,j;
	printf("\n********************************** 欢 迎 登 录 ********************************\n\n");/*22个星号*/

	printf("\n\t\t请输入密码：");/*输入密码*/
	//后退键不会显示星号 
    char ch;
	int p;
	p = 0;
	        
    while((ch=getch())!='\r')
    {  
        if(ch==8)
        {  
            putchar('\b');  
            putchar(' ');  
            putchar('\b');  
            if(p>0)
            p--;  
        }  
        if(!isdigit(ch)&&!isalpha(ch))
            continue;  
            putchar('*');
            user1.upassword[p++]=ch;
    }  
        user1.upassword[p]=0;

	/*从文件中查找正确的账号密码*/
	FILE *fuser;
	fuser = fopen("顾客信息管理.txt","r");
	if(fuser == NULL)
	  printf("\t\t\t\t无法打开此文件！\n\n");
	  
	fscanf(fuser,"%s%s%s%s%s%s%s%f",user.customerID,user.name,user.sex,user.phonenumber,user.password,user.email,user.address,&user.balance);
	
	int flag = 0;
	while(!feof(fuser))
	{
		if(strcmp(ID,user.customerID)==0  && strcmp(user1.upassword,user.password)==0)
		{
		    flag = 1;
		    printf("\n\n\t\t\t\t成功登录！");
		    break;
	    }
        fscanf(fuser,"%s%s%s%s%s%s%s%f",user.customerID,user.name,user.sex,user.phonenumber,user.password,user.email,user.address,&user.balance);
   }
	
	if (flag == 0)
	{
		printf("\n\n\t\t\t\t账号或密码错误，请重新输入...\n\n");
		printf("\t\t\t\t您将会有3次输入机会...\n\n");
		system("pause"); 
		system("cls");
		
		
		for(j = 3; j >= 1; j-- )
		{
			printf("\n********************************* 欢 迎 登 录 ********************************\n\n");/*22个星号*/
        	
	        printf("\n\t\t\t\t请输入密码：");/*输入密码*/
           	char ch; 
	        int p;
	        p = 0;
	        
           	while((ch=getch())!='\r')
           {  
            if(ch==8)
                {  
                    putchar('\b');  
                    putchar(' ');  
                    putchar('\b');  
                    if(p>0)
                    p--;  
                }  
            if(!isdigit(ch)&&!isalpha(ch))
                continue;  
            putchar('*');
            user1.upassword[p++]=ch;
           }  
            user1.upassword[p]=0;
	        
        	FILE *fuser;
         	fuser = fopen("顾客信息管理.txt","r");
            fscanf(fuser,"%s%s%s%s%s%s%s%f",user.customerID,user.name,user.sex,user.phonenumber,user.password,user.email,user.address,&user.balance);
	
        	while(!feof(fuser))
        	{
        		if(strcmp(ID,user.customerID)==0  && strcmp(user1.upassword,user.password)==0)
	          	{
		            printf("\n\n\t\t\t\t成功登录！");
		            flag = 1;
		            break; 
	            }
	            
	           	fscanf(fuser,"%s%s%s%s%s%s%s%f",user.customerID,user.name,user.sex,user.phonenumber,user.password,user.email,user.address,&user.balance);
            }

	        if(flag == 1)
              break;
	        
            if(flag != 1)
            {
		    	printf("\n\n\t\t\t\t账号或密码错误，请重新输入...\n\n");
                printf("\t\t\t\t您还有%d次输入机会...\n\n",j-1);
                system("pause");
                system("cls");
	        }
		}
		
		if(flag != 1)
		{
		    printf("\n\n\t\t\t\t您已没有机会再次输入...\n\n");
		    printf("\t\t\t\t系统将自动退出...\n\n");
		    system("pause");
		    exit(1);
		} 	
	}
}
int uidverification(char ID[81])     //用户ID验证 
{
	struct customer user;
	int flag1; 
	FILE*fuser;
	fuser = fopen("顾客信息管理.txt","r");  //打开储存用户信息的文件 
	if (fuser == NULL)
	  printf("无法打开此文件");
	
	while( (fscanf(fuser,"%s%s%s%s%s%s%s%f",user.customerID,user.name,user.sex,user.phonenumber,user.password,user.email,user.address,&user.balance))  !=EOF)
  	{
		if(strcmp(ID, user.customerID)==0)
		{   
			flag1 = 2;
			printf("\n\n\t\t\t\t账号合法，请继续...\n\n");
			
            system("pause");
			break;
			system("cls");
		}
	
		if(strcmp(ID, user.customerID)!=0)
			flag1 = 1;	
  	}

	return flag1;
} 
  void userchoose(char ID[11])            //顾客主页面 
{
		int choose_flag=1;
 	while(choose_flag)
 	{
 	system("cls");
 	printf("\n********************************* 顾 客 界 面 *********************************\n\n");
 	printf("\n\t\t\t\t顾客功能：\n\n");
    printf("\t\t\t\t①个人信息管理\n\n");
    printf("\t\t\t\t②购物界面\n\n");
    printf("\t\t\t\t③查看历史订单\n\n");
	printf("\t\t\t\t④退出\n\n"); 
	printf("\t\t\t\t请输入您的选择：");
	int choice;
	int flag = 1;
	scanf("%d", &choice);
	 	
	switch(choice)
	{
    	case 1:
               customer_menu(ID); 			
   			    break; 
   		case 2:
    	        gouwu_jiemian(ID);   
		    	break;
   		case 3:
   			{
				customer_ordermenu(ID); 
		    	break;
		    } 
        case 4:
		{ 
        	choose_flag=0;
			exit(1);
	        break;
		}
	     default :
	
				flag = 0;
				printf("\t\t\t\t输入不合法，请重新输入:");
				userchoose(ID);
			    break;		
	}
	}

} 
 
void userRegister()		//注册新用户 
{
	system("cls");
	struct customer user; 
	char id[11],fID[11],name[20],sex[20],code1[20],code2[20],email[30],phone[12],addr[20],line[201];
	int i,x=0,y=0,yorn1,yorn2,yorn3;
	float balance;
	FILE*f1;
	f1=fopen("顾客信息管理.txt","a+");
	
	while(1)
	{
		yorn1 = 0;
		yorn2 = 0;
		yorn3 = 0;
		
		printf("\n请输入用户ID:");
		scanf("%s",id);
		rewind(f1);
		while (fgets(line,81,f1) != NULL)        //检查ID是否已经存在 
		{
			sscanf(line,"%s",fID);
			if(strcmp(id,fID) == 0)
			{
				yorn1 = 1;
				printf("\n用户ID已被注册");
				break;
			}
		}
		if (strlen(id) < 6 || strlen(id) > 10)          //检查ID长度是否正确 
		{
			printf("\n用户ID格式有误");
			yorn2 = 1;
		}
		for (i = 0;i < strlen(id);i++)                   //检查ID是否仅由数字和字母构成 
		{
			if(isalpha(id[i]) == 0 && isdigit(id[i]) == 0)
			{
				printf("\n用户ID只能包含字母和数字");
				yorn3 = 1;
				break;
			}
		}
		if (yorn1 == 0 && yorn2 == 0 && yorn3 == 0)
	    	break;
	}
	
	printf("请输入顾客名称：");
	scanf("%s",name);
	do{
	printf("请输入性别:\n");
	scanf("%s",sex);
	if(strcmp(sex,"女")==0||strcmp(sex,"男")==0)
	  break;
	else 
	    {
	     printf("性别输入有误！\n"); 
	     
	    }
    }while(1);
    while(1)
    {
	
	printf("请输入电话：\n");
	scanf("%s",phone);
	if(strlen(phone)==11)
	break;
	else
	printf("\n输入错误 号码为11位\n"); 
    }
	while(1)                                            //检查两次密码输入是否正确 
	{
		printf("\n请输入您的密码:");
		scanf("%s",code1);
		printf("\n请再次输入您的密码:");
		scanf("%s",code2);
		if(strcmp(code1,code2) == 0)
			break;
		else
			printf("\n两次密码输入不同!请重新输入!");
			
	}	
	int a,b;            
	
	while (1)
	{
		int yorn1 = 0,yorn2 = 0,yorn3 = 0;
		
		printf("\n请输入您的邮箱地址(****@***.***):");
		scanf("%s",email);                                //检查邮箱格式是否正确 
		for (i = 0;i < strlen(email);i++)
		{
			if (email[i] == '@'&&i != 0)
			{
				yorn1 = 1;
				a = i;
			}
			if (email[i] == '.'&&i != (strlen(email) - 1))
			{
				yorn2 = 1;
				b = i;
			}
		}
		if (b - a > 1)
			yorn3 = 1;
		
		if(yorn1 == 1 &&yorn2 == 1&&yorn3 ==1)
			break;
		else printf("\n您的邮箱地址格式有误，需重新输入\n");	
	}
	printf("请输入您的地址\n");
	scanf("%s",addr);
	f1=fopen("顾客信息管理.txt","a+");
	fprintf(f1,"%s %s %s %s %s %s %s %f\n",id,name,sex,phone,code1,email,addr,0);
	printf("\n注册成功......\n");
	fclose(f1);			
}

        //查看用户订单页面 
        void customer_ordermenu(char ID[11])
{
	     system("cls");
	     printf("%15s%s"," ","************************************************\n");
         printf("%15s%s"," ","*                 1.取消未付款订单              *\n");
         printf("%15s%s"," ","*                 2.查看已付款订单              *\n");
         printf("%15s%s"," ","*                 3.退出                        *\n");
         printf("%15s%s"," ","************************************************\n");
        
    	
	    printf("%请选择服务:%");
	   
	    int n;
		int flag = 1;
         
	    scanf("%d",&n);
	   switch(n)
	{
	case 1:
		   cancelcustomer_order(ID);//取消未付款订单
		   
	       break;
		   
    case 2:
		   
   			seecustomer_order(ID);//查看已付款订单 
   		    break;  
		  
    case 3:
    	  userchoose(ID);
    	  system("pause");
          break;
		  default :
			
				flag = 0;
				printf("\t\t\t\t输入不合法，请重新输入:");
			break;	
	 }
    system("pause");
     
}
    

void seecustomer_order(char ID[11])//查看已付款订单 
{
	system("cls");

	FILE *fcorder;
	char paidname[81];
	sprintf(paidname,"paidorderID%s.txt",ID);
	fcorder = fopen(paidname,"r");  //打开所有已付款订单文件  
	//if(fcorder == NULL)
	  //printf("\t\t\t\t无法打开此文件！"); 
	fscanf(fcorder,"%s %s %s %s %d %f %f",forder.forderID,forder.fdate,forder.fitemID,forder.fitemname,&forder.fitemNum,&forder.fprice,&forder.fsumprice);
	
	printf("\t\t\t\t您的历史付款订单如下：\n\n");
	printf("订单编号    		日期      	商品编号  商品名称  商品数量   商品价格     商品总价 \n\n");
	

	fclose(fcorder);
	fcorder = fopen(paidname,"r"); 
	
	while(fscanf(fcorder,"%s %s %s %s %d %f %f",forder.forderID,forder.fdate,forder.fitemID,forder.fitemname,&forder.fitemNum,&forder.fprice,&forder.fsumprice)
   !=EOF)
 
	 {
        
		 printf("%s   %s    %s   %-14s%d\t%.2f     %.2f\n",forder.forderID,forder.fdate, forder.fitemID,  forder.fitemname, forder.fitemNum, forder.fprice,forder.fsumprice);
         //break;
    }
    rewind(fcorder);
    fclose(fcorder);
	 
	 system("pause");
	customer_ordermenu(ID); 
} 
   
  void cancelcustomer_order(char ID[11])//取消未付款订单
{
	system("cls");

	FILE *fcnorder;
	char notpaidname[81];
	char dingdanhao[26];
	sprintf(notpaidname,"notpaidorderID%s.txt",ID);
	fcnorder = fopen(notpaidname,"r");  //打开所有未付款订单文件  
	if(fcnorder == NULL)
	{
		printf("\t\t\t\t无法打开此文件！"); 
	
	}
	  

	fscanf(fcnorder,"%s %s %s %s %d %f %f",fnoorder.forderID,fnoorder.fdate,fnoorder.fitemID,fnoorder.fitemname,&fnoorder.fitemNum,&fnoorder.fprice,&fnoorder.fsumprice);
	
	printf("\t\t\t\t您的历史未付款订单如下：\n\n");
	 printf("订单编号    		日期      	商品编号  商品名称  商品数量   商品价格     商品总价 \n");
	 
	 
	 fclose(fcnorder);
	
	fcnorder = fopen(notpaidname,"r"); 
	 
	 while( fscanf(fcnorder,"%s %s %s %s %d %f %f",fnoorder.forderID,fnoorder.fdate,fnoorder.fitemID,fnoorder.fitemname,&fnoorder.fitemNum,&fnoorder.fprice,&fnoorder.fsumprice)!=EOF)
 
		{
		    printf("%s   %s    %s   %-14s%d\t%.2f     %.2f\n",fnoorder.forderID,fnoorder.fdate,fnoorder.fitemID,fnoorder.fitemname,fnoorder.fitemNum,fnoorder.fprice,fnoorder.fsumprice);
	    }
	    
    	rewind(fcnorder);
        fclose(fcnorder);
printf("\n\t\t\t\t1:删除订单"); 
printf("\n\t\t\t\t2:不删除订单"); 
int f;
scanf("%d",&f);
if(f==1)
{
		
	printf("请输入您要删除的订单的订单编号： ");
	scanf("%s",dingdanhao);
	
	sprintf(notpaidname,"notpaidorder%s.txt",ID);
	//fcnorder = fopen(notpaidname,"r");  //打开所有未付款订单文件  
	
	        FILE *fcnoder=fopen(notpaidname,"r");   
            FILE *newinfo=fopen("temp.txt","w");
            
			if(fcnoder==NULL)
	  	    printf("\n\t\t\t\t文件打开失败！\r\n");

			while( (fscanf(fcnoder,"%s %s %s %s %d %f %f",fnoorder.forderID,fnoorder.fdate,fnoorder.fitemID,fnoorder.fitemname,&fnoorder.fitemNum,&fnoorder.fprice,&fnoorder.fsumprice))!=EOF)
   
  			{
				//if(strcmp(dingdanhao,fnoorder.forderID)==0)
                //    fprintf(newinfo," ");
    				
				if(strcmp(dingdanhao,fnoorder.forderID)!=0)
					fprintf(newinfo, "%s %s %s %s %d %f %f \n",fnoorder.forderID,fnoorder.fdate,fnoorder.fitemID,fnoorder.fitemname,fnoorder.fitemNum,fnoorder.fprice,fnoorder.fsumprice);
  			 }           //将该订单删除 
             
    fclose(fcnoder);
	fclose(newinfo);
   
   	
    sprintf(notpaidname,"notpaidorder%s.txt",ID);
	FILE *ori = fopen(notpaidname,"w");
 	FILE *newi = fopen("temp.txt","r");

	while(fscanf(newi,"%s %s %s %s %d %f %f",fnoorder.forderID,fnoorder.fdate,fnoorder.fitemID,fnoorder.fitemname,&fnoorder.fitemNum,&fnoorder.fprice,&fnoorder.fsumprice) != EOF)
  			{
				fprintf(ori,"%s %s %s %s %d %f %f\n",fnoorder.forderID,fnoorder.fdate,fnoorder.fitemID,fnoorder.fitemname,fnoorder.fitemNum,fnoorder.fprice,fnoorder.fsumprice);
  			}   
  	printf("\t\t\t\t该订单已删除！\n\n");
  	printf("\t\t\t\t返回上一级~~~~") ; 
  	fclose(ori);
	fclose(newi);
	customer_ordermenu(ID);
}
if(f==2)
customer_ordermenu(ID);
		system("pause");
	
	
}  
 
 
       void customer_menu(char ID[11])
{
	     system("cls");
         printf("%15s%s"," ","***************** 用户信息变更 *****************\n\n");
         printf("%15s%s"," ","*                 1.修改密码                   *\n");
         printf("%15s%s"," ","*                 2.变更电话                   *\n");
         printf("%15s%s"," ","*                 3.变更邮箱                   *\n");
         printf("%15s%s"," ","*                 4.修改收货地址               *\n");
         printf("%15s%s"," ","*                 5.账户余额充值               *\n");
         printf("%15s%s"," ","*                 6.退出                       *\n");
         printf("%15s%s"," ","************************************************\n");
          
 //顾客信息变更操作页面 
       printf("请选择服务: ");
 
	int choice;
	int flag = 1;

	    scanf("%d", &choice);
		switch(choice)
	 {
	case 1:
	       
		   cusSetpassword(ID);//修改顾客密码 
	       break;
		   
	case 2:
 
  		    cusSetphonenumber(ID);//修改顾客电话
  			break;
    	 
	case 3:
	      
     		cusSetemail(ID); //修改顾客邮箱 
     		break;
     	     
    case 4:
 
    	    cusSetaddress(ID); //修改顾客地址 
    		break;
    	
	case 5:
	    
		   cusbalancemanage(ID);//账户余额充值 
	       break; 
			
	case 6:
		userchoose(ID);
	   break;	
		  default :
			{
			
				flag = 0;
				printf("\t\t\t\t输入不合法，请重新输入:");
				customer_menu(ID);
			break;
		}
	 }
     system("pause");
 }
 	   void cusSetpassword(char ID[11])
	   
{   
		system("cls");
      	char password1[20];
        char password2[20];
      	
		    FILE *fcpassword1=fopen("顾客信息管理.txt","a+");//打开储存顾客信息的文件 
            FILE *newinfo=fopen("temp.txt","w");
             
			 printf("请输入新登录密码： \n");
             scanf("%s",password1);
	 	     do
	  	    {
             printf("请再次输入新登录密码： \n");
             scanf("%s",password2);
             
             if(strcmp(password1,password2)==0)
             break;
             else
             printf("两次密码输入不同\n");
            }while(1);
			
			if(fcpassword1==NULL)
	  	    printf("\n\t\t\t\t文件打开失败！\r\n");
 
			while( (fscanf(fcpassword1,"%s%s%s%s%s%s%s%f",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,&fcustomer1.fcbalance))  !=EOF)
  			{
				if(strcmp(ID, fcustomer1.fcID)==0)
			  	  	fprintf(newinfo,"%s %s %s %s %s %s %s %f \n",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,password2,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
					
				if(strcmp(ID, fcustomer1.fcID)!=0)
 					fprintf(newinfo,"%s %s %s %s %s %s %s %f \n",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
  			}           //将新密码写入对应ID相同的那一行 
  	
	fclose(fcpassword1);
	fclose(newinfo);

	FILE *ori = fopen("顾客信息管理.txt","w");
 	FILE *newi = fopen("temp.txt","a+");

	while(fscanf(newi,"%s%s%s%s%s%s%s%f",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,&fcustomer1.fcbalance) != EOF)
  			{
				fprintf(ori,"%s %s %s %s %s %s %s %f \n",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
  			}
  			
  	printf("\t\t\t\t密码修改成功已保存！\n\n");
		
	fclose(ori);
	fclose(newi);	
  	system("pause");
 	customer_menu(ID);
}

void cusSetphonenumber(char ID[11])//修改顾客电话 
{	 
	system("cls");
	char phonenumber[11]; 
 
 	FILE *fcphone1 = fopen("顾客信息管理.txt","a+");  //打开储存顾客信息的文件 
 	FILE *newinfo = fopen("temp.txt","w");
    
		 do{
			printf("请输入您的新电话：\n\n");
			scanf("%s",phonenumber);
			  {
				if(strlen(phonenumber) == 11)
				  break;
				else
				  {
			       	printf("\n电话号码应为11位，请重新输入\n\n");
				    system("pause");
				    system("cls");
			     }
			  }		
		    }while(1);
  				
			if(fcphone1==NULL)
	  	    printf("\n\t\t\t\t文件打开失败！\r\n");

			while( (fscanf(fcphone1,"%s%s%s%s%s%s%s%f",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,&fcustomer1.fcbalance))  !=EOF)
  			{
				if(strcmp(ID, fcustomer1.fcID)==0)
			  	  	fprintf(newinfo,"%s %s %s %s %s %s %s %f \n",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,phonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
					
				if(strcmp(ID, fcustomer1.fcID)!=0)
					fprintf(newinfo, "%s %s %s %s %s %s %s %f \n",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
  			}         //将新电话写入对应ID相同的那一行 

    fclose(fcphone1);
	fclose(newinfo);

	FILE *ori = fopen("顾客信息管理.txt","w");
 	FILE *newi = fopen("temp.txt","a+");

	while(fscanf(newi,"%s%s%s%s%s%s%s%f",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,&fcustomer1.fcbalance) != EOF)
  			{
				fprintf(ori,"%s %s %s %s %s %s %s %f \n",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
  			}
  			
  	printf("\t\t\t\t电话号码修改成功已保存！\n\n");
  	
  	printf("\t\t\t\t系统将返回上一级~~~~") ; 
  			
	fclose(ori);
	fclose(newi);
	
	system("pause");
   customer_menu(ID); 	 
	
}
   
void cusSetemail(char ID[11]) //修改顾客邮箱 
{
	 
	system("cls");
	char mail1[20];
 	FILE *fcemail1 = fopen("顾客信息管理.txt","a+");  //打开储存顾客信息的文件 
 	FILE *newinfo = fopen("temp.txt","w");
    int i,a,b,yorn1,yorn2,yorn3;
while (1)
			{
				yorn1 = 0;
				yorn2 = 0;
				yorn3 = 0;
				
				printf("\n\t\t\t\t请输入您的邮箱地址(****@***.***):");
				scanf("%s",mail1);                                //检查邮箱格式是否正确 
				for (i = 0;i < strlen(mail1);i++)
				{
					if (mail1[i] == '@'&&i != 0)
					{
						yorn1 = 1;
						a = i;
					}
					if (mail1[i] == '.'&&i != (strlen(mail1) - 1))
					{
						yorn2 = 1;
						b = i;
					}
				}
				if (b-a>1)
					yorn3 = 1;
		
				if(yorn1 == 1 &&yorn2 == 1&&yorn3 ==1)
					break;
				else 
					printf("\n\t\t\t\t您的邮箱地址格式有误，需重新输入");
			}
  			 
			if(fcemail1==NULL)
	  	    printf("\n\t\t\t\t文件打开失败！\r\n");

			while( (fscanf(fcemail1,"%s%s%s%s%s%s%s%f",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber, fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,&fcustomer1.fcbalance))  !=EOF)
  			{
				if(strcmp(ID, fcustomer1.fcID)==0)
			  	  	fprintf(newinfo,"%s %s %s %s %s %s %s %f \n",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber, fcustomer1.fcpassword,mail1,fcustomer1.fcaddress,fcustomer1.fcbalance);
					
				if(strcmp(ID, fcustomer1.fcID)!=0)
					fprintf(newinfo, "%s %s %s %s %s %s %s %f \n",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber, fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
  			 }           //将新邮箱写入对应ID相同的那一行 

    fclose(fcemail1);
	fclose(newinfo);
	FILE *ori = fopen("顾客信息管理.txt","w");
 	FILE *newi = fopen("temp.txt","a+");

	while(fscanf(newi,"%s%s%s%s%s%s%s%f",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber, fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,&fcustomer1.fcbalance) != EOF)
  			{
				fprintf(ori,"%s %s %s %s %s %s %s %f \n",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber, fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
  			}
  			
  	printf("\t\t\t\t新邮箱修改成功已保存！\n\n");
  	
  	printf("\t\t\t\t返回上一级~~~~") ; 
  			
	fclose(ori);
	fclose(newi);
	
 	system("pause");
  	 
     customer_menu(ID);	
  } 
 //修改顾客地址 
   void cusSetaddress(char ID[11]) 
{
	 
	system("cls");
	char address[20];
 	FILE *fcaddress1 = fopen("顾客信息管理.txt","a+");  //打开储存顾客信息的文件 
 	FILE *newinfo = fopen("temp.txt","w");
  
			printf("\t\t\t\t请输入您的新地址：");
			scanf("%s",address);
  			
			if(fcaddress1==NULL)
	  	    printf("\n\t\t\t\t文件打开失败！\r\n");

			while( (fscanf(fcaddress1,"%s%s%s%s%s%s%s%f",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber, fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,&fcustomer1.fcbalance))  !=EOF)
  			{
				if(strcmp(ID, fcustomer1.fcID)==0)
			  	  	fprintf(newinfo,"%s %s %s %s %s %s %s %f \n",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,address,fcustomer1.fcbalance);
					
				if(strcmp(ID, fcustomer1.fcID)!=0)
					fprintf(newinfo, "%s %s %s %s %s %s %s %f \n",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
  			 }           //将新地址写入对应ID相同的那一行 
    fclose(fcaddress1);
	fclose(newinfo);
	FILE *ori = fopen("顾客信息管理.txt","w");
 	FILE *newi = fopen("temp.txt","a+");

	while(fscanf(newi,"%s%s%s%s%s%s%s%f",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,&fcustomer1.fcbalance) != EOF)
  			{
				fprintf(ori,"%s %s %s %s %s %s %s %f \n",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
  			}
  			
  	printf("\t\t\t\t新地址修改成功已保存！\n\n");
  	
  	printf("\t\t\t\t返回上一级~~~~") ; 
  			
	fclose(ori);
	fclose(newi); 
	system("pause");
  	customer_menu(ID);

  }
  
void cusbalancemanage(char ID[11])
{
  	
	  float money;
	  float x;	
       system("cls");
            FILE *fcbalance1=fopen("顾客信息管理.txt","a+");//打开储存顾客账户余额的文件 
            FILE *newinfo=fopen("temp.txt","w");
			printf("充值金额： \n");
			scanf("%f",&money); 
	 	//将变化后余额写入原文件中 
			if(fcbalance1==NULL)
	  	    printf("\n\t\t\t\t文件打开失败！\r\n");

			while( (fscanf(fcbalance1,"%s%s%s%s%s%s%s%f",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber, fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,&fcustomer1.fcbalance))  !=EOF)
  			{
				if(strcmp(ID, fcustomer1.fcID)==0)
				    {
					x=fcustomer1.fcbalance+money;
			  	  	fprintf(newinfo,"%s %s %s %s %s %s %s %f \n",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber, fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,x);
				    }
				if(strcmp(ID, fcustomer1.fcID)!=0)
					fprintf(newinfo, "%s %s %s %s %s %s %s %f \n",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber, fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
  			 }           //将当前余额写入对应ID相同的那一行 
             
			  fclose(fcbalance1);
	fclose(newinfo);

	FILE *ori = fopen("顾客信息管理.txt","w");
 	FILE *newi = fopen("temp.txt","a+");

	while(fscanf(newi,"%s%s%s%s%s%s%s%f",fcustomer1.fcID, fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber,fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,&fcustomer1.fcbalance) != EOF)
  			{
				fprintf(ori,"%s %s %s %s %s %s %s %f\n",fcustomer1.fcID,fcustomer1.fcname,fcustomer1.fcsex,fcustomer1.fcphonenumber, fcustomer1.fcpassword,fcustomer1.fcemail,fcustomer1.fcaddress,fcustomer1.fcbalance);
  			}   
  
  	printf("\t\t\t\t账户余额充值成功！\n\n");
  	
  	printf("\t\t\t\t返回上一级~~~~") ; 
  			
	fclose(ori);
	fclose(newi);
	
	system("pause");
	customer_menu(ID);
  }
  
void gouwu_jiemian(char ID[11])
  {
  	system("cls");
  	int a;
  	int flag = 1;
  	printf("\n\n\t\t\t\t1	商品排序\n\n"); 
  	printf("\t\t\t\t2	商品推荐\n\n"); 
  	printf("\t\t\t\t3	商品购买\n\n");
  	printf("\t\t\t\t4	商品折扣筛选\n\n");
  	printf("\t\t\t\t5	商品查询\n\n");
  	printf("\t\t\t\t6	退出\n\n");
	printf("\t\t\t\t7	返回上一级\n\n"); 
  	scanf("%d",&a);
  	switch(a)
  	{
	  	case 1:
	  		{
	  			system("cls"); 
			  	printf("\n\n\t\t\t\t1	按价格排序\n\n"); 
	  			printf("\t\t\t\t2	按销量排序\n\n");
	  			printf("\t\t\t\t3	退出\n\n");
	  			int b;
				scanf("%d",&b);
				switch(b)
				{
					case 1:
						rankPrice(ID);/*调用<按价格排序>函数*/
						break;
					case 2:
						rankSale(ID);/*调用<按销量排序>函数*/
						break;
					case 3:
						flag=0;
						exit(1);
						break;	
				 } 
				 system("pause");
  				break;
  			} 
  		case 2:
  			rank_tuijian(ID);
  			break;
  		case 3:
  			goumai(ID);
  			break;
  		case 4:
  			findDiscount(ID);
  			break;
  		case 5:
			printf("\n\t\t\t1 按商品名称查找"); 
			printf("\n\t\t\t2 按超市名称查找\n");
			int e;
			scanf("%d",&e);
			switch(e)
			{
				case 1:
					findGoodname(ID);
					break;
				case 2:
					findShopname(ID);
					break;
				default:
					gouwu_jiemian(ID); 
					break;
			 } 
  		case 6:
  			flag=0;
			exit(1);
			break;
		case 7:
		     userchoose(ID);
		     break;
  		default:
  		{
			flag = 0;	
			printf("                       输入错误请重新输入！\n");
		 	system("pause");
			gouwu_jiemian(ID);
			break;
		}
  	}
	system("pause");	
   } 
   void  rankPrice(char ID[11]) /*<按价格排序>函数*/
{
	system("cls"); 
  	FILE *list;
	char listFile[20];
		
	struct Good 
{
	char num[7];
	char name[20];
	char chaoshi[20];
	float cost;
	float price;
	int sale;
	int kucun;
	float discount;
	int year1;/*折扣开始时间 */ 
	int month1;
	int day1;
	int hour1;
	int min1;
	int year2;/*折扣结束时间 */ 
	int month2;
	int day2;
	int hour2;
	int min2;
}good[1000];
	
	
	int j;
	int i=0;
	
	for(j=1;j<4;j++)
	{
		sprintf(listFile,"%c%c000%d.txt",j+64,j+64,j);/*文件名后期统一*/ 
		list=fopen(listFile,"r");
		if(list==NULL)/*文件是否打开*/ 
		printf("\t\t\t\t无法查询。\t\n");
		else/*读取超市j的商品目录*/
		{
		while(fscanf(list,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,
	  					&good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,
	  					&good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
	  	i++;
		
		}
		
	}
		/*冒泡排序法*/
		int m,n; 
		struct Good t2;
		for(m=0;m<=i-1;m++)
		{  
		    for(n=0;n<=i-2-m;n++) 
		    {
	    		if(good[n].price>good[n+1].price)
	    		{  
				    t2=good[n];       
				    good[n]=good[n+1];
					good[n+1]=t2;    	//给商品价格由小到大排序	    
	       		}
		    }
		}
		
		int p=0;
			
			printf("商品按价格由低到高排序如下：\n");
			printf("商品编号	商品名	所属超市	进价	售价	销量	库存	折扣价	开始时间		结束时间\n"); 
		
		 
		for (;p<i;p++)
		{	
			
			printf("%s\t\t%-10s%s\t\t%.2f\t%.2f\t%d\t%d\t%.2f\t%d:%d:%d:%d:%d\t\t%d:%d:%d:%d:%d\n",good[p].num,good[p].name,good[p].chaoshi,good[p].cost,good[p].price,
	  					good[p].sale,good[p].kucun,good[p].discount,good[p].year1,good[p].month1,good[p].day1,good[p].hour1,good[p].min1,
	  					good[p].year2,good[p].month2,good[p].day2,good[p].hour2,good[p].min2);
		}
		 
	fclose(list);
	printf("\n按销量排序请按“1”\n");
	printf("退出请按“2”\n");
	printf("购买请按“3”\n"); 
	int r;
	scanf("%d",&r);
	switch(r)
	{
		case 1:
			rankSale(ID);
			break;
		case 2:
		 	gouwu_jiemian(ID);
			break;
		case 3:
			goumai(ID);
			break;
		default: 
			rankPrice(ID);
			break;
	}
	system("pause");	 
}

void  rankSale(char ID[11]) /*<按销量排序>函数*/
 {
   	system("cls");
   	FILE *list;
	char listFile[20];
		
	struct Good 
{
	char num[7];
	char name[20];
	char chaoshi[20];
	float cost;
	float price;
	int sale;
	int kucun;
	float discount;
	int year1;/*折扣开始时间 */ 
	int month1;
	int day1;
	int hour1;
	int min1;
	int year2;/*折扣结束时间 */ 
	int month2;
	int day2;
	int hour2;
	int min2;
}good[1000];
	
	
	int j=3;
	int i=0;
	
	for(j=1;j<4;j++)
	{
		sprintf(listFile,"%c%c000%d.txt",j+64,j+64,j);/*文件名后期统一*/ 
		list=fopen(listFile,"r");
		if(list==NULL)/*文件是否打开*/ 
		printf("\t\t\t\t无法查询。\t\n");
		else/*读取超市j的商品目录*/
		{
		
		while(fscanf(list,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,
	  					&good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,
	  					&good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
	  	i++;
		
		}	
	}
	
	 int k=0;  	
	/*冒泡排序法*/
		int m,n; 
		struct Good t2;
		for(m=0;m<=i-1;m++)
		{  
		    for(n=0;n<=i-2-m;n++) 
		    {
	    		if(good[n].sale<good[n+1].sale)
	    		{  
				    t2=good[n];       
				    good[n]=good[n+1];
					good[n+1]=t2;    	//给商品价格由小到大排序	    
	       		}
		    }
		}
		
		int p=0;
			
			printf("商品按销量由高到低排序如下：\n");
			printf("商品编号	商品名	所属超市	进价	售价	销量	库存	折扣价	开始时间		结束时间\n"); 
		for (;p<i;p++)
		{	
			
			printf("%s\t\t%-10s%s\t\t%.2f\t%.2f\t%d\t%d\t%.2f\t%d:%d:%d:%d:%d\t\t%d:%d:%d:%d:%d\n",good[p].num,good[p].name,good[p].chaoshi,good[p].cost,good[p].price,
	  					good[p].sale,good[p].kucun,good[p].discount,good[p].year1,good[p].month1,good[p].day1,good[p].hour1,good[p].min1,
	  					good[p].year2,good[p].month2,good[p].day2,good[p].hour2,good[p].min2);
		}	
	fclose(list);
	printf("\n按价格排序请按“1”\n");
	printf("退出请按“2”\n"); 
	printf("购买请按“3”\n"); 
	int r;
	scanf("%d",&r);
	switch(r)
	{
		case 1:
			rankPrice(ID);
			break;
		case 2:
		 	gouwu_jiemian(ID);
			break;
		case 3:
			goumai(ID);
			break;
		default: 
			rankSale(ID);
			break;
	}
	system("pause");	

		
}
void  rank_tuijian(char ID[11]) /*<按价格排序>函数*/
{
	system("cls"); 
  	FILE *list;
	char listFile[20];
	float chajia[1000];	
	struct Good 
{
	char num[7];
	char name[20];
	char chaoshi[20];
	float cost;
	float price;
	int sale;
	int kucun;
	float discount;
	int year1;/*折扣开始时间 */ 
	int month1;
	int day1;
	int hour1;
	int min1;
	int year2;/*折扣结束时间 */ 
	int month2;
	int day2;
	int hour2;
	int min2;
}good[1000];

	system("cls"); 
	int j;
	int i=0;
	for(j=1;j<4;j++)
	{
		
	
		sprintf(listFile,"%c%c000%d.txt",j+64,j+64,j);/*文件名后期统一*/ 
	
		list=fopen(listFile,"r");
		if(list==NULL)/*文件是否打开*/ 
		printf("\t\t\t\t无法查询。\t\n");
		else/*读取超市j的商品目录*/
		{
			while(fscanf(list,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,
	  					&good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,
	  					&good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
			{
  				chajia[i]=good[i].price-good[i].discount;
	  			i++;
  			} 
		
		}
		
	}
		/*冒泡排序法*/
		int m,n; 
		struct Good t2;
		float a;
		for(m=0;m<=i-1;m++)
		{  
		    for(n=0;n<=i-2-m;n++) 
		    {
	    		if(chajia[n]<chajia[n+1])
	    		{  
				    t2=good[n];       
				    good[n]=good[n+1];
					good[n+1]=t2;
					a=chajia[n];
					chajia[n]=chajia[n+1];
					chajia[n+1]=a;
					    	 
	       		}
		    }
		}
		
		int p=0;
			/*按折扣差价多少推荐的*/ 
			printf("商品推荐如下：\n");
			printf("商品编号 商品名	    所属超市	进价	售价	销量	库存	折扣价	开始时间	 结束时间	折扣前后差价\n"); 
	for (;p<i;p++)
		{	
			printf("%s\t %-10s    %s\t\t%.2f\t%.2f\t%d\t%d\t%.2f\t%-4d:%-2d:%-2d:%-2d:%-2d %-4d:%-2d:%-2d:%-2d:%-2d %.2f\n",good[p].num,good[p].name,good[p].chaoshi,good[p].cost,good[p].price,
	  					good[p].sale,good[p].kucun,good[p].discount,good[p].year1,good[p].month1,good[p].day1,good[p].hour1,good[p].min1,
	  					good[p].year2,good[p].month2,good[p].day2,good[p].hour2,good[p].min2,chajia[p]);
	  					
		}
	 fclose(list);
 
	printf("\n返回上一级请按“1”\n"); 
	printf("退出请按“2”\n");
	int r;
	scanf("%d",&r);
	switch(r)
	{
		case 1:
			gouwu_jiemian(ID);
			break;
		case 2:
		 	exit(1);
			break;
	}
	 system("pause");
}

/*根据时间判断折扣函数*/
float zhekou(float pri,float dis,int n1,int y1,int r1,int s1,int f1,int n2,int y2,int r2,int s2,int f2)
{
    float t;
    int a1,a2,a3;
    
    time_t nowtime;
    struct tm *timeinfo;
    time( &nowtime );
    timeinfo = localtime( &nowtime );
    
    int xtn = timeinfo->tm_year + 1900;
    int xty = timeinfo->tm_mon + 1;
    int xtr = timeinfo->tm_mday;
    int xts = timeinfo->tm_hour;
    int xtf = timeinfo->tm_min;
    a3=365*24*60*xtn+30*24*60*xty+24*60*xtr+60*xts+xtf;
    
    a1=365*24*60*n1+30*24*60*y1+24*60*r1+60*s1+f1;
    a2=365*24*60*n2+30*24*60*y2+24*60*r2+60*s2+f2;
    
    if(a3<=a2&&a3>=a1)
        t=dis;
    else
        t=pri;
    
    return(t);
    
    
}

void confirmBuy(char goodsnum[],int n,int m,char ID[11]) /*n代表购买的第几件商品，m代表购买几件*/
{
    char custID[11];
    struct order order;
    strcpy(custID,ID);
   struct Goods good[1000];
   FILE *Idorder;
    char orderFile[81];
    sprintf(orderFile,"orderID%s.txt",custID);/*为每个ID创建自己的订单文件*/
    Idorder=fopen(orderFile,"a+");
    
    FILE *paid;
    char paidname[81];
    sprintf(paidname,"paidorderID%s.txt",custID);
    paid=fopen(paidname,"a+");/*每个ID的支付订单*/
    
    FILE *notpaid;
    char notpaidname[81];
    sprintf(notpaidname,"notpaidorderID%s.txt",custID);
    notpaid=fopen(notpaidname,"a+");/*每个ID的未支付订单*/
    
    FILE *goodshop;
    char Gshop[81];/*超市订单*/
    
    
    
    int i=0,j,t=0,d=0;
    int zhaodao=0;
    int pre,aft;
    FILE *new1;
    FILE *new2;
    new2=fopen("temp2.txt","a+");
    
    FILE *guke;/*打开顾客信息文件的文件流*/
    
    
    time_t nowtime;
    struct tm *timeinfo;
    time( &nowtime );
    timeinfo = localtime( &nowtime );
    
    int xtn = timeinfo->tm_year + 1900;
    int xty = timeinfo->tm_mon + 1;
    int xtr = timeinfo->tm_mday;
    int xts = timeinfo->tm_hour;
    int xtf = timeinfo->tm_min;
    
    
    
    /*找相应商品号，并存入订单信息结构*/
    for(j=1;j<4;j++)
    {
        /*for循环中的参数*/
        FILE *list;
        char listFile[20];
        int choice;
        sprintf(listFile,"%c%c000%d.txt",j+64,j+64,j);

        
        list=fopen(listFile,"r");
        if(list==NULL)/*文件是否打开*/
            printf("\t\t\t\t无法查询。\t\n");
        else/*读取超市j的商品目录*/
        {
            pre=i;
            
            while(fscanf(list,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,
                         &good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,
                         &good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
            {
              
                if (strcmp(goodsnum,good[i].num) == 0)
                {
                    
                    zhaodao++;
                    
                    sprintf(Gshop,"Shop%s.txt",good[i].chaoshi);
                    goodshop=fopen(Gshop,"a+");
                    
                    
                    strcpy(order.itemID,good[i].num);
                    strcpy(order.itemname,good[i].name);
                    order.itemNum=m;

                    order.price=zhekou(good[i].price,good[i].discount,good[i].year1,good[i].month1,good[i].day1,good[i].hour1,good[i].min1,
                                       good[i].year2,good[i].month2,good[i].day2,good[i].hour2,good[i].min2);
                    

                    order.sumprice=order.price*order.itemNum;
                    
                    sprintf(order.date,"%d:%d:%d:%d:%d",xtn,xty,xtr,xts,xtf);
                    sprintf(order.orderID,"%s%s",custID,order.date);
                    fprintf(Idorder,"%s %s %s %s %d %f %f\n",order.orderID,order.date,order.itemID,order.itemname,order.itemNum,order.price,order.sumprice);
                    fclose(Idorder);
                    
                    printf("商品已加入订单\n");
                    
                    printf("您现在要付款吗：1.付款  2.不付款\n");
                    
                    scanf("%d",&choice);
                    switch (choice){ 
                        case 1:
                            
                            
                            guke=fopen("顾客信息管理.txt","r");
                            
                            
                            if(guke==NULL)
							{
                                printf("信息查询失败。");
                                exit(1);
                            }
                              new1 = fopen("temp1.txt","w");
                            while(fscanf(guke,"%s %s %s %s %s %s %s %f",user[t].customerID,user[t].name,user[t].sex,user[t].phonenumber,user[t].password,user[t].email,user[t].address,&user[t].money)!=EOF)
							{								
                
								if(strcmp(custID,user[t].customerID)==0)
								{
									d++;
                                    if(user[t].money>=order.sumprice)
									{
                                        user[t].money=user[t].money-order.sumprice;
                                        
                                        fprintf(paid,"%s %s %s %s %d %f %f\n",order.orderID,order.date,order.itemID,order.itemname,order.itemNum,order.price,order.sumprice);
                                        fclose(paid);
                                        
                                        
                                        fprintf(goodshop,"%s %s %s %s %d %f %f %f\n",order.orderID,order.date,order.itemID,order.itemname,order.itemNum,order.price,order.sumprice,good[i].cost);
                                        fclose(goodshop);
                                        good[i].kucun =good[i].kucun-order.itemNum;
                                        good[i].sale=good[i].sale+order.itemNum;

                                    }else
									{
                                        printf("余额不够，请充值。");
                                        //void notBuy();
                                    }
                                }
                             
                              fprintf(new1,"%s %s %s %s %s %s %s %f\n",user[t].customerID,user[t].name,user[t].sex,user[t].phonenumber,user[t].password,user[t].email,user[t].address,user[t].money);
                                t++;
                            }
                            fclose(new1);
                            fclose(guke);
                            if(d==0)
                            printf("未找到顾客信息");
                            
                            break;
                            
                            
                            case 2:/*下单不付款函数*/
								/*到顾客文件中找此顾客信息*/
								/*改顾客未支付订单信息*/
								 guke=fopen("顾客信息管理.txt","r");
                            
								printf("1"); 
								fclose(notpaid);
								notpaid=fopen(notpaidname,"a+");
								fprintf(notpaid,"%s %s %s %s %d %f %f\n",order.orderID,order.date,order.itemID,order.itemname,order.itemNum,order.price,order.sumprice);
								fclose(notpaid);
	
								new1 = fopen("temp1.txt","w");
								while(fscanf(guke,"%s %s %s %s %s %s %s %f",user[t].customerID,user[t].name,user[t].sex,user[t].phonenumber,user[t].password,user[t].email,user[t].address,&user[t].money)!=EOF)
							    {
									fprintf(new1,"%s %s %s %s %s %s %s %f\n",user[t].customerID,user[t].name,user[t].sex,user[t].phonenumber,user[t].password,user[t].email,user[t].address,user[t].money);  
									t++;
								}
								fclose(new1);
							fclose(guke);
							break;

                    }
                    
                    fclose(goodshop);
                    
                    
                }
 
                
                fprintf(new2,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",good[i].num,good[i].name,good[i].chaoshi,good[i].cost,good[i].price,good[i].sale,good[i].kucun,good[i].discount,good[i].year1,good[i].month1,good[i].day1,good[i].hour1,good[i].min1,
                        good[i].year2,good[i].month2,good[i].day2,good[i].hour2,good[i].min2);
                
                
                i++;
            }/*while的括号*/
            
            aft=i;
           
            fclose(list);
            
        }/*else的括号*/
        
        /*商品信息重新录入*/
        FILE *ori2=fopen(listFile,"w");

		 int p=pre;
         while(p<aft&&p>=pre)
         {
         fprintf(ori2,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",good[p].num,good[p].name,good[p].chaoshi,good[p].cost,good[p].price,
         good[p].sale,good[p].kucun,good[p].discount,good[p].year1,good[p].month1,good[p].day1,good[p].hour1,good[p].min1,
         good[p].year2,good[p].month2,good[p].day2,good[p].hour2,good[p].min2);
         p++;
         }
         
         fclose(ori2);   
      
        
    }/*for的括号*/
    
    fclose(new2);
    
	if (zhaodao==0)
        printf("未找到相应编号商品\n");
    /*顾客信息重新录入*/
     
     fclose(new1);
     int p=0;
     FILE *new3=fopen("temp1.txt","r"); 
     FILE *ori1 = fopen("顾客信息管理.txt","w");
     while(fscanf(new3,"%s %s %s %s %s %s %s %f",user[p].customerID,user[p].name,user[p].sex,user[p].phonenumber,user[p].password,user[p].email,user[p].address,&user[p].money)!=EOF)
     {
     fprintf(ori1,"%s %s %s %s %s %s %s %f\n",user[p].customerID,user[p].name,user[p].sex,user[p].phonenumber,user[p].password,user[p].email,user[p].address,user[p].money);
     p++;
     }
     fclose(ori1);
    fclose(new3);
    
}

/*购买函数*/ 
 void goumai(char ID[11])
{
		int choice2=1; 
	char searchNum[7];
	int a,j,i;
	struct Goods good[1000];
	
		while(choice2!=2)
	{
	    
		printf("请输入你想购买的商品编号：\n");
		scanf("%s",searchNum);
		
		system("cls");
		int n=0,m=0;/*查找到/购买的商品个数*/
		int choice,choice1;
		int jianshu; 
		i=0;
		j=1;
	    
		for(j=1;j<4;j++)
		{ 
			
			FILE *list;
			char listFile[20];
			sprintf(listFile,"%c%c000%d.txt",j+64,j+64,j);/*文件名后期统一*/ 
		
			list=fopen(listFile,"r");
			if(list==NULL)/*文件是否打开*/ 
			printf("\t\t\t\t无法查询。\t\n");
			else/*读取超市j的商品目录*/
			{
				    while(fscanf(list,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,&good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,
		  					&good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
				{
	
					if (strcmp(searchNum,good[i].num) == 0)
					{
						printf("商品编号	商品名	所属超市	进价	售价	销量	库存	折扣价	开始时间		结束时间\n");
						printf("%s\t\t%s\t%s\t\t%.2f\t%.2f\t%d\t%d\t%.2f\t%d:%d:%d:%d:%d\t\t%d:%d:%d:%d:%d\n\n",good[i].num,good[i].name,good[i].chaoshi,good[i].cost,good[i].price,
		  						good[i].sale,good[i].kucun,good[i].discount,good[i].year1,good[i].month1,good[i].day1,good[i].hour1,good[i].min1,
		  						good[i].year2,good[i].month2,good[i].day2,good[i].hour2,good[i].min2);
					    n++;
					    printf("你确定购买此商品吗：1.确定 2.不买\n");
						scanf("%d",&choice);
						
						switch(choice)
						{
							case 1:
							do
							{
								printf("\n\n请输入购买数量(不要超过库存量：%d):\n",good[i].kucun);
								scanf("%d",&jianshu); 
								if(jianshu>good[i].kucun)
								{
								
									printf("\n\n您输入数量超过库存量。您可以选择：1. 更改数量  2.放弃购买 \n");
									scanf("%d",&choice1);
									
									if(choice1==1)
										{
										system("cls");
										continue;}
										
										
									if(choice1==2)
									break;	//notBuy();/*返回主界面*/ 
									
										
								}
								
							} while(jianshu>good[i].kucun);
							
							 
							confirmBuy(searchNum,m,jianshu,ID);/*写购买物品的系列函数*/ 
							break;
							
							case 2:
							//void notBuy(); /*选择不买的返回函数*/ /*返回主页面*/ 
							break;
							
						} 
					}
		 		
				 	i++;
				 }
			 }
				
				fclose(list);

			} 
						
			if(n==0)
			{
				printf("没有找到对应编号的商品。\n");
				//void notBuy();/*返回搜索页面*/ 
			}
					
			
			printf("继续购买请按 1 完成购买请按 2 \n");
			scanf("%d",&choice2);
	
	}
 	
 gouwu_jiemian(ID);	
 system("pause");
	 
}
void findDiscount(char ID[11])
{
	system("cls");
	struct Good 
	{
		char num[7];
		char name[20];
		char chaoshi[20];
		float cost;
		float price;
		int sale;
		int kucun;
		float discount;
		int year1;/*折扣开始时间 */ 
		int month1;
		int day1;
		int hour1;
		int min1;
		int year2;/*折扣结束时间 */ 
		int month2;
		int day2;
		int hour2;
		int min2;
	}good[1000];
	
	FILE *list; 
	char listFile[81];
	int j,t;
	int i=0;
	
	for(j=1;j<4;j++)
	{
		sprintf(listFile,"%c%c000%d.txt",j+64,j+64,j);/*文件名后期统一*/ 
		list=fopen(listFile,"r");
		if(list==NULL)/*文件是否打开*/ 
		printf("\t\t\t\t无法查询。\t\n");
		else/*读取超市j的商品目录*/
		{
		while(fscanf(list,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,
	  					&good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,
	  					&good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
	  	i++;
		
		}
		
	}
	printf("商品折扣筛选如下：\n");
	printf("商品编号	商品名	所属超市	进价	售价	销量	库存	折扣价	开始时间		结束时间\n"); 
	   
	for(t=0;t<i;t++)
	{
		if(good[t].discount<good[t].price)
	   	printf("%s\t\t%s\t%s\t\t%.2f\t%.2f\t%d\t%d\t%.2f\t%d:%d:%d:%d:%d\t\t%d:%d:%d:%d:%d\n",good[t].num,good[t].name,good[t].chaoshi,good[t].cost,good[t].price,
	  					good[t].sale,good[t].kucun,good[t].discount,good[t].year1,good[t].month1,good[t].day1,good[t].hour1,good[t].min1,
	  					good[t].year2,good[t].month2,good[t].day2,good[t].hour2,good[t].min2);
	}
	printf("\n返回上一级界面请按“1”\n退出请按“2”\n");
	int e;
	scanf("%d",&e);
	switch(e)
	{
		case 1:
			gouwu_jiemian(ID);
			break;
		case 2:
			exit(1);
			break;
		default:
			break;
	}
}
	
 void  findShopname(char ID[11])/*按超市名称查找函数*/ 
{
	FILE *list;
	struct Goods good[1000];
	char searchName[81];
	system("cls");
    printf("\t\t\t\t请输入您想要查询的超市名称：");
    scanf("%s",searchName);
    printf("商品编号	商品名	所属超市	进价	售价	销量	库存	折扣价	开始时间		结束时间\n");

	int j;
	int i=0,k=0,p=0;
	
	for(j=1;j<4;j++)
	{
		
		char listFile[20];
		sprintf(listFile,"%c%c000%d.txt",j+64,j+64,j);/*文件名后期统一*/ 
	
		list=fopen(listFile,"r");
		if(list==NULL)/*文件是否打开*/ 
		printf("\t\t\t\t无法查询。\t\n");
		else/*读取超市j的商品目录*/
		{
			
			
            
			 while(fscanf(list,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,
	  					&good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,
	  					&good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
				
			{
					
	  					
	  			if(strcmp(searchName, good[i].chaoshi) == 0)
				printf("%s\t\t%s\t%s\t\t%.2f\t%.2f\t%d\t%d\t%.2f\t%d:%d:%d:%d:%d\t\t%d:%d:%d:%d:%d\n",good[i].num,good[i].name,good[i].chaoshi,good[i].cost,good[i].price,
	  					good[i].sale,good[i].kucun,good[i].discount,good[i].year1,good[i].month1,good[i].day1,good[i].hour1,good[i].min1,
	  					good[i].year2,good[i].month2,good[i].day2,good[i].hour2,good[i].min2);
	  					
	  					i++;
			
			}
				
			 	
			
		
		}
	} 
	

		 
		 printf("\n已显示超市全部商品。若超市名错误，则无法显示信息。\n\n");
		 
		 
		 /*根据折扣过滤*/ 
		 int choice;
		 printf("请输入选项序号：\n");
		 printf("1. 过滤以上商品折扣信息\n");
		 printf("2. 返回购物界面(可购买)\n\n");
		 scanf("%d",&choice);
		 
		 switch(choice)
		 {
 		 	case 1:
			system("cls");
			findshopDiscount(searchName,ID);
			break;
			
			case 2:
			gouwu_jiemian(ID);
			break;
			default:
				findShopname(ID); 
				break;
			 	
 		 }
		 
	 
		fclose(list);
		system("pause");
}

void findshopDiscount(char x[81],char ID[11])
{
	FILE *list;
	system("cls");
    struct Goods good[1000];
    printf("商品编号	商品名	所属超市	进价	售价	销量	库存	折扣价	开始时间		结束时间\n");

	int j;
	int i=0,k=0,p=0;
	
	for(j=1;j<4;j++)
	{
		
		char listFile[20];
		sprintf(listFile,"%c%c000%d.txt",j+64,j+64,j);/*文件名后期统一*/ 
	
		list=fopen(listFile,"r");
		if(list==NULL)/*文件是否打开*/ 
		printf("\t\t\t\t无法查询。\t\n");
		else/*读取超市j的商品目录*/
		{
			
			
            
			 while(fscanf(list,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,
	  					&good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,
	  					&good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
				
			{
					
	  					
	  			if(strcmp(x, good[i].chaoshi) == 0&&(good[i].discount<good[i].price))
				printf("%s\t\t%s\t%s\t\t%.2f\t%.2f\t%d\t%d\t%.2f\t%d:%d:%d:%d:%d\t\t%d:%d:%d:%d:%d\n",good[i].num,good[i].name,good[i].chaoshi,good[i].cost,good[i].price,
	  					good[i].sale,good[i].kucun,good[i].discount,good[i].year1,good[i].month1,good[i].day1,good[i].hour1,good[i].min1,
	  					good[i].year2,good[i].month2,good[i].day2,good[i].hour2,good[i].min2);
	  					
	  					i++;
			
			}
				
			 	
			
		
		}
	} 
	

		 
		 printf("\n已显示超市全部有折扣商品。若信息错误，则无法显示。\n");
		 printf("\n\t\t\t\t购买请按1\n\t\t\t\t退出请按2\n");
		 int u;
		 scanf("%d",&u);
		 switch(u)
		 {
		 	case 1:
		 		goumai(ID);
		 		break;
		 	case 2:
		 		gouwu_jiemian(ID);
			break;
			default:
			break;		
		 }
		 system("pause");
}



void  findGoodname(char ID[11])/*按超市名称查找函数*/ 
{
	FILE *list;
	struct Goods good[1000];
	char searchName[81];
	system("cls");
    printf("\t\t\t\t请输入您想要查询的商品名称：");
    scanf("%s",searchName);
    printf("商品编号	商品名	所属超市	进价	售价	销量	库存	折扣价	开始时间		结束时间\n");

	int j;
	int i=0,k=0,p=0;
	
	for(j=1;j<4;j++)
	{
		
		char listFile[20];
		sprintf(listFile,"%c%c000%d.txt",j+64,j+64,j);/*文件名后期统一*/ 
	
		list=fopen(listFile,"r");
		if(list==NULL)/*文件是否打开*/ 
		printf("\t\t\t\t无法查询。\t\n");
		else/*读取超市j的商品目录*/
		{
			
			
            
			 while(fscanf(list,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,
	  					&good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,
	  					&good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
				
			{
					
	  					
	  			if(strcmp(searchName, good[i].name) == 0)
				printf("%s\t\t%s\t%s\t\t%.2f\t%.2f\t%d\t%d\t%.2f\t%d:%d:%d:%d:%d\t\t%d:%d:%d:%d:%d\n",good[i].num,good[i].name,good[i].chaoshi,good[i].cost,good[i].price,
	  					good[i].sale,good[i].kucun,good[i].discount,good[i].year1,good[i].month1,good[i].day1,good[i].hour1,good[i].min1,
	  					good[i].year2,good[i].month2,good[i].day2,good[i].hour2,good[i].min2);
	  					
	  					i++;
			
			}
				
			 	
			
		
		}
	} 
	

		 
		 printf("\n已显示所有商品。若商品名错误，则无法显示信息。\n\n");
		 
		 
		 /*根据折扣过滤*/ 
		 int choice;
		 printf("请输入选项序号：\n");
		 printf("1. 过滤以上商品折扣信息\n");
		 printf("2. 返回购物界面(可购买)\n\n");
		 scanf("%d",&choice);
		 
		 switch(choice)
		 {
 		 	case 1:
			  system("cls");
				findgoodDiscount(searchName,ID);
			  break;
			
			
			case 2:
			gouwu_jiemian(ID);
			break;
			default:
			findGoodname(ID); 
			break; 	
 		 }
		 
	 
		fclose(list);
		system("pause");
}



void findgoodDiscount(char x[81],char ID[11])
{
	FILE *list;
	struct Goods good[1000];
	system("cls");
    printf("商品编号	商品名	所属超市	进价	售价	销量	库存	折扣价	开始时间		结束时间\n");

	int j;
	int i=0,k=0,p=0;
	
	for(j=1;j<4;j++)
	{
		
		char listFile[20];
		sprintf(listFile,"%c%c000%d.txt",j+64,j+64,j);/*文件名后期统一*/ 
	
		list=fopen(listFile,"r");
		if(list==NULL)/*文件是否打开*/ 
		printf("\t\t\t\t无法查询。\t\n");
		else/*读取超市j的商品目录*/
		{
			
			
            
			 while(fscanf(list,"%s %s %s %f %f %d %d %f %d %d %d %d %d %d %d %d %d %d\n",good[i].num,good[i].name,good[i].chaoshi,&good[i].cost,&good[i].price,
	  					&good[i].sale,&good[i].kucun,&good[i].discount,&good[i].year1,&good[i].month1,&good[i].day1,&good[i].hour1,&good[i].min1,
	  					&good[i].year2,&good[i].month2,&good[i].day2,&good[i].hour2,&good[i].min2)!=EOF)
				
			{
					
	  					
	  			if(strcmp(x, good[i].name) == 0&&(good[i].discount<good[i].price))
				printf("%s\t\t%s\t%s\t\t%.2f\t%.2f\t%d\t%d\t%.2f\t%d:%d:%d:%d:%d\t\t%d:%d:%d:%d:%d\n",good[i].num,good[i].name,good[i].chaoshi,good[i].cost,good[i].price,
	  					good[i].sale,good[i].kucun,good[i].discount,good[i].year1,good[i].month1,good[i].day1,good[i].hour1,good[i].min1,
	  					good[i].year2,good[i].month2,good[i].day2,good[i].hour2,good[i].min2);
	  					
	  					i++;
			
			}
				
			 	
			
		
		}
	} 
	

		 
		 printf("\n已显示全部有折扣商品。若信息错误，则无法显示。\n");
		 printf("\n购买请按1\n退出请按2\n");
		 int u;
		 scanf("%d",&u);
		 switch(u)
		 {
		 	case 1:
		 		goumai(ID);
		 		break;
		 	case 2:
		 		gouwu_jiemian(ID);
			break;
			default:
			break;		
		 }
		 system("pause");
}
 
 

