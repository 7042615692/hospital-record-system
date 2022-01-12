# hospital-record-system
This is very useful project. This project is used for any Hospital, Nursing home.
#include<stdio.h>//use for standard i/o operation
#include<windows.h>
#include<conio.h>//use for delay(),getch(),gotoxy(),etc.
#include<ctype.h>//se for toupper(), tolower(),etc
#include<string.h>//use for strcmp(),strcpy(),strlen(),etc
#include<stdlib.h>

char ans=0; 
int ok;
int b, valid=0;

void welcomescreen(void);
void title(void);
void mainmenu(void);
void loginscreen(void);
void add_rec(void);
void func_list();
void search_rec(void);
void edit_rec(void);
void dlt_rec(void);
void ex_it(void);

void gotoxy(short x, short y) {
coord pos = {x, y};
setconsolecursorposition(getstdhandle(std_output_handle), pos);
}

struct patient
{
	int age;
	char gender;
	char first_name[20];
	char last_name[20]; 
	char contact_no[15];
	char address[30];
	char email[30];
	char doctor[20];
	char problem[20];
};

struct patient  p,temp_c;



main(void)
{
	
    welcomescreen();
	title();
	loginscreen();
	
	
	

}

void welcomescreen(void) 
{
	
	printf("\n\n\n\n\n\n\n\t\t\t\t#########################################");
	printf("\n\t\t\t\t#\t\t welcome to\t\t#");
	printf("\n\t\t\t\t#          hospital record system       #");
	printf("\n\t\t\t\t#########################################");
	printf("\n\n\n\n\n press any key to continue......\n");
	getch();
	system("cls");
	
}

void title(void)
{
	printf("\n\n\t\t----------------------------------------------------------------------------------");
	printf("\n\t\t\t\t               hospital record        ");
	printf("\n\t\t----------------------------------------------------------------------------------");
}

void mainmenu(void)
{
	system("cls");
	int choose;
	title();
	printf("\n\n\n\n\n\t\t\t\t1. add patients record\n");
	printf("\n\t\t\t\t2. list patients record\n");
	printf("\n\t\t\t\t3. search patients record\n");
	printf("\n\t\t\t\t4. edit patients record\n");
	printf("\n\t\t\t\t5. delete patients record\n");
	printf("\n\t\t\t\t6. exit\n");
	printf("\n\n\n \n\t\t\t\tchoose from 1 to 6:");
	scanf("%i", &choose);
	
	switch(choose)
	{
	
	case 1:
	add_rec();
    	break;
    case 2:
    	func_list();
    	break;
	case 3:
	search_rec();
    	break;
	case 4:
		edit_rec();
		break;
	case 5:
		dlt_rec();
		break;
	case 6:
		ex_it();
    	break;

	default:
		printf("\t\t\tinvalid entry. please enter right option :)");
		getch();
	}
		
	
}

void ex_it(void)
{
	system("cls");
	title();
	printf("\n\n\n\n\n\t\t\tthank you for visiting :)");
	getch();
	
}

void loginscreen(void)
{

int e=0	;
char username[15];
char password[15];
char original_username[25]="admin";
char original_password[15]="12345";

do
{
	printf("\n\n\n\n\t\t\t\tenter your username and password :)");
	printf("\n\n\n\t\t\t\t\tusername:");
	scanf("%s",&username);
	
	printf("\n\n\t\t\t\t\tpassword:");
	scanf("%s",&password);
	
	if (strcmp(username,original_username)==0 && strcmp(password,original_password)==0)
	{
		printf("\n\n\n\t\t\t\t\t...login successfull...");
		
		
		getch();
		mainmenu();
		break;
	}
	else
	{
		printf("\n\t\t\tpassword in incorrect:( try again :)");
		e++;
		getch();
	}

}
while(e<=2);
	if(e>2)
	{
	printf("you have cross the limit. you cannot login. :( :(");
	getch();
    ex_it();
	}
 
system("cls");
}





void add_rec(void)
{
	system("cls");
	title();
	
	char ans;
	file*ek;
	ek=fopen("record2.dat","a");
	printf("\n\n\t\t\t!!!!!!!!!!!!!! add patients record !!!!!!!!!!!!!\n");
	
	
	a:
	printf("\n\t\t\tfirst name: ");
	scanf("%s",p.first_name);
	p.first_name[0]=toupper(p.first_name[0]);
	if(strlen(p.first_name)>20||strlen(p.first_name)<2)
	{
		printf("\n\t invalid :( \t the max range for first name is 20 and min range is 2 :)");
		goto a;
	}
	else
	{
		for (b=0;b<strlen(p.first_name);b++)
		{
			if (isalpha(p.first_name[b]))
			{
				valid=1;
			}
			else
			{
				valid=0;
				break;
			}
		}
		if(!valid)
		{
			printf("\n\t\t first name contain invalid character :(  enter again :)");
			goto a;
		}
	}
	
	
	b:
	printf("\n\t\t\tlast name: ");
    scanf("%s",p.last_name);
    p.last_name[0]=toupper(p.last_name[0]);
    if(strlen(p.last_name)>20||strlen(p.last_name)<2)
	{
		printf("\n\t invalid :( \t the max range for last name is 20 and min range is 2 :)");
		goto b;
	}
	else
	{
		for (b=0;b<strlen(p.last_name);b++)
		{
			if (isalpha(p.last_name[b]))
			{
				valid=1;
			}
			else
			{
				valid=0;
				break;
			}
		}
		if(!valid)
		{
			printf("\n\t\t last name contain invalid character :(  enter again :)");
			goto b;
		}
	}
   
	do
	{
	    printf("\n\t\t\tgender[f/m]: ");
		scanf(" %c",&p.gender);
		if(toupper(p.gender)=='m'|| toupper(p.gender)=='f')
		{
			ok =1;
		}
		else 
		{
		ok =0;
		}
        if(!ok)
	    {
	    	printf("\n\t\t gender contain invalid character :(  enter either f or m :)");
    	}
	 }	while(!ok);

    printf("\n\t\t\tage:");
    scanf(" %i",&p.age);
   
    do
    {
    c:
    printf("\n\t\t\taddress: ");
    scanf("%s",p.address);
    p.address[0]=toupper(p.address[0]);
    if(strlen(p.address)>20||strlen(p.address)<4)
	{
		printf("\n\t invalid :( \t the max range for address is 20 and min range is 4 :)");
		goto c;
	}
	
}while(!valid);

do
{
	d:
    printf("\n\t\t\tcontact no: ");
    scanf("%s",p.contact_no);
    if(strlen(p.contact_no)>10||strlen(p.contact_no)!=10)
	{
		printf("\n\t sorry :( invalid. contact no. must contain 10 numbers. enter again :)");
		goto d;
	}
	else
	{
		for (b=0;b<strlen(p.contact_no);b++)
		{
			if (!isalpha(p.contact_no[b]))
			{
				valid=1;
			}
			else
			{
				valid=0;
				break;
			}
		}
		if(!valid)
		{
			printf("\n\t\t contact no. contain invalid character :(  enter again :)");
			goto d;
		}
	}
}while(!valid);

do
{
    printf("\n\t\t\temail: ");
    scanf("%s",p.email);
    if (strlen(p.email)>30||strlen(p.email)<8)
    {
       printf("\n\t invalid :( \t the max range for email is 30 and min range is 8 :)");	
	}
}while(strlen(p.email)>30||strlen(p.email)<8);

    e:
    printf("\n\t\t\tproblem: ");
    scanf("%s",p.problem);
    p.problem[0]=toupper(p.problem[0]);
    if(strlen(p.problem)>15||strlen(p.problem)<3)
	{
		printf("\n\t invalid :( \t the max range for first name is 15 and min range is 3 :)");
		goto e;
	}
	else
	{
		for (b=0;b<strlen(p.problem);b++)
		{
			if (isalpha(p.problem[b]))
			{
				valid=1;
			}
			else
			{
				valid=0;
				break;
			}
		}
		if(!valid)
		{
			printf("\n\t\t problem contain invalid character :(  enter again :)");
			goto e;
		}
	}

	f:
    printf("\n\t\t\tprescribed doctor:");
    scanf("%s",p.doctor);
    p.doctor[0]=toupper(p.doctor[0]);
    if(strlen(p.doctor)>30||strlen(p.doctor)<3)
	{
		printf("\n\t invalid :( \t the max range for first name is 30 and min range is 3 :)");
		goto f;
	}
	else
	{
		for (b=0;b<strlen(p.doctor);b++)
		{
			if (isalpha(p.doctor[b]))
			{
				valid=1;
			}
			else
			{
				valid=0;
				break;
			}
		}
		if(!valid)
		{
			printf("\n\t\t doctor name contain invalid character :(  enter again :)");
			goto f;
		}
	}
    
    fprintf(ek," %s %s %c %i %s %s %s %s %s\n", p.first_name, p.last_name, p.gender, p.age, p.address, p.contact_no, p.email, p.problem, p.doctor);
    printf("\n\n\t\t\t.... information record successful ...");
    fclose(ek);
    sd:
    getch();
    printf("\n\n\t\t\tdo you want to add more[y/n]?? ");
    scanf(" %c",&ans);
    if (toupper(ans)=='y')
	{
    	add_rec();
	}
    else if(toupper(ans)=='n')
	{
		printf("\n\t\t thank you :) :)");
    	getch();
    	mainmenu();
	}
    else
    {
        printf("\n\t\tinvalid input\n");
        goto sd;
    }
}

void func_list()
{
	int row;
	system("cls");
	title();
	file *ek;
	ek=fopen("record2.dat","r");
	printf("\n\n\t\t\t!!!!!!!!!!!!!! list patients record !!!!!!!!!!!!!\n");
	gotoxy(1,15);
		printf("full name");
		gotoxy(20,15);
		printf("gender");
		gotoxy(32,15);
		printf("age");
		gotoxy(37,15);
		printf("address");
		gotoxy(49,15);
		printf("contact no.");
		gotoxy(64,15);
		printf("email");
		gotoxy(88,15);
		printf("problem");
		gotoxy(98,15);
		printf("prescribed doctor\n");
		printf("=================================================================================================================");
		row=17;
		while(fscanf(ek,"%s %s %c %i %s %s %s %s %s\n", p.first_name, p.last_name, 
					&p.gender, &p.age, p.address, p.contact_no, p.email, p.problem, p.doctor)!=eof)
		{
			gotoxy(1,row);
			printf("%s %s",p.first_name, p.last_name);
			gotoxy(20,row);
			printf("%c",p.gender);
			gotoxy(32,row);
			printf("%i",p.age);
			gotoxy(37,row);
			printf("%s",p.address);
			gotoxy(49,row);
			printf("%s",p.contact_no);
			gotoxy(64,row);
			printf("%s",p.email);
			gotoxy(88,row);
			printf("%s",p.problem);
			gotoxy(98,row);
			printf("%s",p.doctor);
			row++;
		}
		fclose(ek);
		getch();
		mainmenu();
}
void search_rec(void)
{
	char name[20];
	system("cls");
	title();
	file *ek;
	ek=fopen("record2.dat","r");
	printf("\n\n\t\t\t!!!!!!!!!!!!!! search patients record !!!!!!!!!!!!!\n");
	gotoxy(12,8);
	printf("\n enter patient name to be viewed:");
	scanf("%s",name);
	fflush(stdin);
	name[0]=toupper(name[0]);
	while(fscanf(ek,"%s %s %c %i %s %s %s %s %s\n", p.first_name, p.last_name, &p.gender, &p.age, p.address, p.contact_no, p.email, p.problem, p.doctor)!=eof)
	{
		if(strcmp(p.first_name,name)==0)
		{
			gotoxy(1,15);
			printf("full name");
			gotoxy(25,15);
			printf("gender");
			gotoxy(32,15);
			printf("age");
			gotoxy(37,15);
			printf("address");
			gotoxy(52,15);
			printf("contact no.");
			gotoxy(64,15);
			printf("email");
			gotoxy(80,15);
			printf("problem");
			gotoxy(95,15);
			printf("prescribed doctor\n");
			printf("=================================================================================================================");
			gotoxy(1,18);
			printf("%s %s",p.first_name, p.last_name);
			gotoxy(25,18);
			printf("%c",p.gender);
			gotoxy(32,18);
			printf("%i",p.age);
			gotoxy(37,18);
			printf("%s",p.address);
			gotoxy(52,18);
			printf("%s",p.contact_no);
			gotoxy(64,18);
			printf("%s",p.email);
			gotoxy(80,18);
			printf("%s",p.problem);
			gotoxy(95,18);
			printf("%s",p.doctor);
			printf("\n");
			break;
		}
	   }
	   if(strcmp(p.first_name,name)!=0)
	   {
		gotoxy(5,10);
		printf("record not found!");
		getch();
	   }
	fclose(ek);
	l:
	getch();
	printf("\n\n\t\t\tdo you want to view more[y/n]??");
    scanf("%c",&ans);
    if (toupper(ans)=='y')
    {
        search_rec();
    }
	else if(toupper(ans)=='n')
	{
		printf("\n\t\t thank you :) :)");
    	getch();
		mainmenu();
    }
	else
    {
    	printf("\n\tinvalid input.\n");
    	goto l;
    }
}

void edit_rec(void)
{
	file *ek, *ft;
  int i,b, valid=0;
  char ch;
  char name[20];

  system("cls");
  	title();
 		ft=fopen("temp2.dat","w+");
	   ek=fopen("record2.dat","r");
	   if(ek==null)
	   {
		printf("\n\t can not open file!! ");
		getch();
		mainmenu();
	   }
       	printf("\n\n\t\t\t!!!!!!!!!!!!!! edit patients record !!!!!!!!!!!!!\n");
	   	gotoxy(12,13);
	   	printf("enter the first name of the patient : ");
	   	scanf(" %s",name);
	   	fflush(stdin);
	   	name[0]=toupper(name[0]);
		gotoxy(12,15);
		
		if(ft==null)
		{
			printf("\n can not open file");
			getch();
			mainmenu();
		}
		while(fscanf(ek,"%s %s %c %i %s %s %s %s %s\n", p.first_name, p.last_name, &p.gender, &p.age, p.address, p.contact_no, p.email, p.problem, p.doctor)!=eof)
		{
			if(strcmp(p.first_name, name)==0)
			{
				valid=1;
				gotoxy(25,17);
				printf("* existing record *");
				gotoxy(10,19);
				printf("%s \t%s \t%c \t%i \t%s \t%s \t%s \t%s \t%s\n",p.first_name,p.last_name,p.gender, p.age,p.address,p.contact_no,p.email,p.problem,p.doctor);
				gotoxy(12,22);	
				printf("enter new first name: ");
				scanf("%s",p.first_name);    
				gotoxy(12,24);
				printf("enter last name: ");
				scanf("%s",p.last_name);
				gotoxy(12,26);
				printf("enter gender: ");
				scanf(" %c",&p.gender);
				p.gender=toupper(p.gender);
				gotoxy(12,28);
				printf("enter age: ");
				scanf(" %i",&p.age);
				gotoxy(12,30);
				printf("enter address: ");
				scanf("%s",p.address);
				p.address[0]=toupper(p.address[0]);
				gotoxy(12,32);
				printf("enter contact no: ");
				scanf("%s",p.contact_no);
				gotoxy(12,34);
				printf("enter new email: ");
				scanf("%s",p.email);
			    gotoxy(12,36);
				printf("enter problem: ");
				scanf("%s",p.problem);
				p.problem[0]=toupper(p.problem[0]);
			    gotoxy(12,38);
				printf("enter doctor: ");
			    scanf("%s",p.doctor);
			    p.doctor[0]=toupper(p.doctor[0]);
			    printf("\npress u charecter for the updating operation : ");
				ch=getche();
				if(ch=='u' || ch=='u')
				{
				fprintf(ft,"%s %s %c %i %s %s %s %s %s\n",p.first_name,p.last_name,p.gender, p.age,p.address,p.contact_no,p.email,p.problem,p.doctor);
				printf("\n\n\t\t\tpatient record updated successfully...");
				}					
			}
			else
			{
			fprintf(ft,"%s %s %c %i %s %s %s %s %s\n",p.first_name,p.last_name,p.gender, p.age,p.address,p.contact_no,p.email,p.problem,p.doctor);	
			}
		 }
		 if(!valid) printf("\n\t\tno record found...");
	   fclose(ft);
	   fclose(ek);
	   remove("record2.dat");
   	   rename("temp2.dat","record2.dat");
		getch();
		mainmenu();		
}
void dlt_rec()
{
	char name[20];
	int found=0;
	system("cls");
	title();
	file *ek, *ft;
	ft=fopen("temp_file2.dat","w+");
	ek=fopen("record2.dat","r");
	printf("\n\n\t\t\t!!!!!!!!!!!!!! delete patients record !!!!!!!!!!!!!\n");
	gotoxy(12,8);
	printf("\n enter patient name to delete: ");
	fflush(stdin);
	gets(name);
	name[0]=toupper(name[0]);
	
	while (fscanf(ek,"%s %s %c %i %s %s %s %s %s", p.first_name, p.last_name, &p.gender,
			 &p.age, p.address, p.contact_no, p.email, p.problem, p.doctor)!=eof)
	{
		if (strcmp(p.first_name,name)!=0)
		fprintf(ft,"%s %s %c %i %s %s %s %s %s\n", p.first_name, p.last_name, p.gender, p.age, p.address, p.contact_no, p.email, p.problem, p.doctor);
		else 
		{
			printf("%s %s %c %i %s %s %s %s %s\n", p.first_name, p.last_name, p.gender, p.age, p.address, p.contact_no, p.email, p.problem, p.doctor);
			found=1;
		}
	}
	if(found==0)
	{
		printf("\n\n\t\t\t record not found....");
		getch();
		mainmenu();
	}
	else
	{
		fclose(ek);
		fclose(ft);
		remove("record2.dat");
		rename("temp_file2.dat","record2.dat");
		printf("\n\n\t\t\t record deleted successfully :) ");
		getch();
		mainmenu();
	}
}
