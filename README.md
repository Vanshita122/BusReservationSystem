# BusReservationSystem

Basically four features are available in this project, but you can write your own code to add more features, and make this project even better. Here, I am going to briefly describe the features:

1.Install Bus Information:
This feature allows you to install a typical bus information before it can be reserved by the passengers or shown in buses available. It includes the bus no., driver’s name, arrival time, departure time and destination (from and to) of the bus.

2.Reservation:
This feature is very simple; it includes the bus no., seat number and the passenger’s name. The seat number of the particular bus is reserved under the passenger’s name.

3.Show Reservation Information:
With this feature, you can show all the information regarding the buses and their respective seats. It contains all the information stored by the previous two function of this project. It also enlists the no. of empty seats in a bus along with the seat number registered to a particular passenger.

4.Buses Available:
This feature simply shows the buses available for reservation, and the information regarding the bus no. stored under the first feature. In bus reservation system project, file has not been used to store the data of bus information. So, upon every run of the program, previously stored data regarding the aforementioned features are lost.

You are encouraged to incorporate file handling in this project to store all the bus details, and make the project more effective and complete overall. This is a very simple project,published here just to show the implementation processes and techniques of class and object of the C++ language and some concept of oops.

Coding part:

   #include<iostream>

   #include<conio.h>

   #include<stdio.h>

   #include<fstream>

   #include<windows.h>

   using namespace std;

   class bus{

	private:

		string b_no,b_name,d_name;

		int b_seats;

	public:

	   void menu();
	
	   void new_bus();

	   void view_bus

	   void single_view_bus();

	   void all_view_bus();

	   void update_bus();

	   void del_bus();
 
	   void route_bus();

	   void details_bus();

	   void booking();

	   void renew();

	   void search_booking();

	   void update_record();

	   void del_record();

	   void show();

};

    void bus::menu(){

    	system("cls");

		int choice;

    	p:
		cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";

		cout<<"\n\n  ****MAIN MENU****";

		cout<<"\n\n 1.ADD BUS RECORD";

		cout<<"\n 2.VIEW BUSES DETAIL";

		cout<<"\n 3.UPDATE BUS DETAIL";

		cout<<"\n 4.DELETE BUS DETAIL";

		cout<<"\n 5.ROUTS OF BUSES";

		cout<<"\n 6.SEAT DETAIL";

		cout<<"\n 7.BOOKING RECORD";

		cout<<"\n 8.SEATS RENEW";

		cout<<"\n 9.SEARCH BOOKING RECORD";

		cout<<"\n 10.UPDATE BOOKING RECORD";

		cout<<"\n 11.DELETE BOOKING RECORD";

		cout<<"\n 12.SHOW ALL BOOKING RECORD";

		cout<<"\n 13.EXIT";

		cout<<"\n\n ENTER YOUR CHOICE: ";

		cin>>choice;

		switch(choice){

			case 1:

			    new_bus();

				break;

			case 2:

				view_bus();

				break;

			case 3:

				update_bus();

				break;

			case 4:

				del_bus();

				break;

			case 5:

				route_bus();

				break;

		    case 6:

		    	details_bus();

				break;

			case 7:

				booking();

				break;

			case 8:

				renew();

				break;

			case 9:

				search_booking();

				break;

			case 10:

				update_record();

				break;

			case 11:

				del_record();

				break;

			case 12:

				show();

				break;

			case 13:

				exit(0);

			default:

			   cout<<"\n\n Invalid Choice.... Please Try again.....";
				
		}

		getch();

		goto p;
	
	}

	void bus::new_bus(){

		p:

		system("cls");

		fstream file;

		int found=0;

		string t_no,tb_name,td_name;

		int t_seats;

		cout<<"\n\t\t____________BUS MANAGMENT SYSTEM____________";

		cout<<"\n\n Bus No: ";

		cin>>b_no;

		cout<<"\n\n Bus Name: ";

		cin>>b_name;

		cout<<"\n\n Total seats: ";

		cin>>b_seats;

		cout<<"\n\n Driver Name: ";

		cin>>d_name;

		file.open("bus.txt",ios::in);

		if(!file){

			file.open("bus.txt",ios::app|ios::out);

			file<<b_no<<" "<<b_name<<" "<<b_seats<<" "<<d_name<<"\n";

			file.close();

		}

		else{

		file>>t_no>>tb_name>>t_seats>>td_name;

		while(!file.eof()){

			if(b_no== t_no){

				found++;

			}
			file>>t_no>>tb_name>>t_seats>>td_name;

		}

		file.close();

		if(found==0){

			file.open("bus.txt",ios::app|ios::out);

			file<<b_no<<" "<<b_name<<" "<<b_seats<<" "<<d_name<<"\n";

			file.close();
		}
		else{
			cout<<"\n\n Duplicate record found...";
			getch();
			goto p;
		}	
		}
		cout<<"\n\n Inserted new bus data successfully.....";
	}
	void bus::view_bus(){
		system("cls");
		p:
		int choice;
		cout<<"\n\t\t___________BUS MANAGMENT SYSTEM___________";
		cout<<"\n\n 1.Single Bus View";
		cout<<"\n 2.All Buses View";
		cout<<"\n 3.Go Back";
		cout<<"\n\n Enter Your Choice: ";
		cin>>choice;
		switch(choice){
			case 1:
				single_view_bus();
				break;
			case 2:
				all_view_bus();
				break;
			case 3:
				menu();
			default:
				cout<<"\n\n Invalid Choice.....Please Try Again.....";
		}
		getch();
		goto p;
	}
	void bus::single_view_bus(){
	   system("cls");
	   string t_no;
	   fstream file;
	   int found=0;
	   cout<<"\n\n\t___________BUS MANAGMENT SYSTEM____________";
	   file.open("bus.txt",ios::in);
	   if(!file){
	   	  cout<<"\n\n File Openning Error....";
	   }
	   else{
	   	cout<<"\n\n Bus no: ";
	    cin>>t_no;
	    file>>b_no>>b_name>>b_seats>>d_name;
	    while(!file.eof()){
	    	if(t_no==b_no){
	    		system("cls");
	    		cout<<"\n\n\t___________BUS MANAGMENT SYSTEM____________";
	    		cout<<"\n\n BUS NO.\tBUS NAME\tNO. OF SEATS\tDRIVER NAME";
	    		cout<<"\n "<<b_no<<"\t\t"<<b_name<<"\t\t"<<b_seats<<"\t\t"<<d_name;
	    		found++;
			}
			file>>b_no>>b_name>>b_seats>>d_name; 
		}
		file.close();
		if(found==0){
			cout<<"\n\n Invalid Bus No......"; 
		}
	   }
	   	
	}
	void bus::all_view_bus(){
		system("cls");
	   string t_no;
	   fstream file;
	   cout<<"\n\n\t___________BUS MANAGMENT SYSTEM____________";
	   file.open("bus.txt",ios::in);
	   if(!file){
	   	  cout<<"\n\n File Openning Error....";
	   }
	   else{
	   	cout<<"\n\n BUS NO.\tBUS NAME\tNO. OF SEATS\tDRIVER NAME";
	    file>>b_no>>b_name>>b_seats>>d_name;
	    while(!file.eof()){
	        cout<<"\n "<<b_no<<"\t\t"<<b_name<<"\t\t"<<b_seats<<"\t\t"<<d_name;
		   file>>b_no>>b_name>>b_seats>>d_name; 
	    }
		file.close();
	   }
	}
	void bus::update_bus(){
		system("cls");
		fstream file,file1;
		string t_no,t_name,td_name,no;
		int t_seats,found=0;
		cout<<"\n\t\t___________BUS MANAGMENT SYSTEM___________";
		file.open("bus.txt",ios::in);
		if(!file){
		  cout<<"\n\n File Opening Error....";	
		}
		else{
			cout<<"\n\n Bus No.: ";
			cin>>t_no;
			file1.open("bus1.txt",ios::app|ios::out);
			file>>b_no>>b_name>>b_seats>>d_name;
			while(!file.eof()){
				if(t_no==b_no){
				    cout<<"\n\n New Bus No.: ";
					cin>>no;
					cout<<"\n\n Bus Name: ";
					cin>>t_name;
					cout<<"\n\n Total seats: ";
					cin>>t_seats;
					cout<<"\n\n Driver Name: ";
					cin>>td_name;
					file1<<no<<" "<<t_name<<" "<<t_seats<<" "<<td_name<<"\n";
					cout<<"\n\n\t\t\tUpdate Bus Record Successfully....";
					found++; 	
				}
				else{
					file1<<b_no<<" "<<b_name<<" "<<b_seats<<" "<<d_name<<"\n";
				}
			   file>>b_no>>b_name>>b_seats>>d_name;	
			}
			file.close();
			file1.close();
		}
		remove("bus.txt");
		rename("bus1.txt","bus.txt");
		if(found==0){
			cout<<"\n\n Bus No. is Invalid.....";
		}
	}
	void bus::del_bus(){
		system("cls");
		fstream file,file1;
		string t_no;
		int found=0;
		cout<<"\n\t\t___________BUS MANAGMENT SYSTEM___________";
		file.open("bus.txt",ios::in);
		if(!file){
		  cout<<"\n\n File Opening Error....";	
		}
		else{
			cout<<"\n\n Bus No.: ";
			cin>>t_no;
			file1.open("bus1.txt",ios::app|ios::out);
			file>>b_no>>b_name>>b_seats>>d_name;
			while(!file.eof()){
				if(t_no==b_no){
				    cout<<"\n\n\t\t\tDelete Bus Record Successfully....";
					found++; 	
				}
				else{
					file1<<b_no<<" "<<b_name<<" "<<b_seats<<" "<<d_name<<"\n";
				}
			   file>>b_no>>b_name>>b_seats>>d_name;	
			}
			file.close();
			file1.close();
		}
		remove("bus.txt");
		rename("bus1.txt","bus.txt");
		if(found==0){
			cout<<"\n\n Bus No. is Invalid.....";
		}
	}
	void bus::route_bus(){
		p:
		system("cls");
		int choice;
		cout<<"\n\t\t___________BUS MANAGMENT SYSTEM___________";
		cout<<"\n\n 1.1st ROUT DETAILS";
		cout<<"\n\n 2.2nd ROUT DETAILS";
		cout<<"\n\n 3.3rd ROUT DETAILS";
		cout<<"\n\n 4.4th ROUT DETAILS";
		cout<<"\n\n 5.5th ROUT DETAILS";
		cout<<"\n\n Enter Your Choice: ";
		cin>>choice;
		switch(choice){
			case 1:
				system("cls");
				cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";
				cout<<"\n   From Sialkot to Lahore";
				cout<<"\n9:00 am ............ 11:00 am";
				cout<<"\n   From Lahore to Faisalabad";
				cout<<"\n12:00 pm ............ 2:30 pm";
				cout<<"\n   From Sahiwaal to Bhawalpur ";
				cout<<"\n4:00 am ............. 9:00 am";
				cout<<"\n    From Lahore to Multan";
				cout<<"\n7:00 am .............. 2:00 pm";
				cout<<"\n    From Islamabad to Murree";
				cout<<"\n10:00 am ................. 11:30 am";
				cout<<"\n     From Daska to Lahore";
				cout<<"\n8:30 am ...............10:00 am";
				break;
			case 2:
				system("cls");
				cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";
				cout<<"\n    From Sialkot to Gujranwala";
				cout<<"\n9:00 am ............... 10:00 am";
				cout<<"\n    From Lahore to Kamoki";
				cout<<"\n12:00 pm ................ 1:00 pm";
				cout<<"\n    From Islambad to Rawalpindi";
				cout<<"\n10:00 pm ................... 11:00 pm";
				break;
			case 3:
				system("cls");
				cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";
				cout<<"\n     From Kamoki to Wazirabad ";
				cout<<"\n8:30 am ................ 9:30 am";
				cout<<"\n     From Lahore to Gujranwala";
				cout<<"\n1:00 pm ................. 2:30 pm";
				cout<<"\n     From Muree to New Muree";
				cout<<"\n4:00 pm .................. 4:30 pm";
				cout<<"\n     From Naran to Nathiya Gali";
				cout<<"\n7:00 am .................. 12:00 pm";
				cout<<"\n     From Sialkot to Jehlum ";
				cout<<"\n8:00 am ......................10:00 am"; 
				break;
			case 4:
				system("cls");
				cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";
				cout<<"\n     From Rawalpindi to Attock";
				cout<<"\n1:00 pm ................. 10:00 pm";
				cout<<"\n     From Sialkot to Lahore";
				cout<<"\n8:00 pm ................. 10:00 pm";
				cout<<"\n     From Lahore to Faisalabad";
				cout<<"\n11:00 am ................. 1:30 pm";
				cout<<"\n     From Sialkot to Islamabad";
				cout<<"\n5:00 pm .................. 10:00 pm";
				cout<<"\n     From Lahore to Multan";
				cout<<"\n6:00 pm ................... 11:00 pm";
				cout<<"\n     From Multan to Gujranwala";
				cout<<"\n7:30 am .................... 5:00 pm";
				break;
			case 5:
				system("cls");
				cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";
				cout<<"\n     From Multan to Lahore";
				cout<<"\n8:00 pm .................... 12:00 pm";
				cout<<"\n     From Daska to Faisalabad";
				cout<<"\n11:00 pm ................. 3:30 pm";
				cout<<"\n     From Sialkot to Islamabad";
				cout<<"\n3:00 am .................. 10:00 pm";
				cout<<"\n     From Sialkot to Quetta";
				cout<<"\n7:30 am .................. 5:00 pm";
				break;
			default:
				cout<<"\n\n Invalid Choice.....Please Try Again.....";	
		}
		getch();
		goto p;
		
	}
	void bus::details_bus(){
		system("cls");
		fstream file,file1;
	    string t_no,sb_no,s_no;
	    int count=0,found=0;
		cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";
		file.open("bus.txt",ios::in);
		file1.open("seat.txt",ios::in);
		if(!file || !file1){
			cout<<"\n\n File Opening Error.....";
		}	
		else{
			cout<<"\n\n Bus No. : ";
			cin>>t_no;
			file1>>sb_no>>s_no;
			while(!file1.eof()){
				if(b_no==s_no){
					count++;
				}
				file1>>sb_no>>s_no;
			}
			file1.close();
			file>>b_no>>b_name>>b_seats>>d_name;
			while(!file.eof()){
				if(t_no==b_no){
					system("cls");
					cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";
					cout<<"\n\n Total No. of seats: "<<b_seats;
					cout<<"\n\n Reserved No. of Seats: "<<count;
					cout<<"\n\n Empty No. of Seats: "<<b_seats-count;
					found++;
				}
				file>>b_no>>b_name>>b_seats>>d_name;
			}
			file.close();
			if(found==0){
				cout<<"\n\n Bus No. is Invalid.........Please Enter valid bus";
			}
		}
	}
	void bus::booking(){
		p:
		system("cls");
		fstream file;
		string t_no,sb_no,cus_name,phone,from,to;
		int s_no,found=0,seats,count=0,s_s_no,ss_no[50],i=0,s_amt,r_amt,total_amt=0;
		char x;
		cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";
		file.open("bus.txt",ios::in);
		if(!file){
			cout<<"\n\n File Opening Error...";
		}			
		else{
			cout<<"\n\n Bus No. : ";
			cin>>t_no;
			file.close();
			file.open("seat.txt",ios::in);
			if(file){
			    file>>sb_no>>s_s_no;	
			    while(!file.eof()){
			    	if(t_no==sb_no)
			    	     count++;
			        file>>sb_no>>s_s_no;
				}
				file.close();
			}
			file.open("bus.txt",ios::in);
			file>>b_no>>b_name>>b_seats>>d_name;
			while(!file.eof()){
				if(t_no==b_no){
					seats=b_seats;
					found++;
				}
				file>>b_no>>b_name>>b_seats>>d_name;		 
			}
			file.close();
			if(seats-count==0){
				cout<<"\n\n All seats are Already Reserved";
			}
			else if(found==1){
				do{
					h:
					cout<<"\n\n Seat No. : ";
					cin>>s_no;
					if(s_no>seats){
						cout<<"\n\n Seat no. is Invalid ....Please Try Again";
						goto h;
					}
					file.open("seat.txt",ios::in);
					if(!file){
						file.open("seat.txt",ios::app|ios::out);
						file<<t_no<<" "<<s_no<<"\n";
						file.close();
					}
					else{
					   file>>sb_no>>s_s_no;
						while(!file.eof()){
							if(t_no==sb_no && s_no==s_s_no){
								cout<<"\n\n Seat is Already Reserved ...Please Try Again...";
								file.close();
								goto h;
							}
							file>>sb_no>>s_s_no;
						}
						file.close();
						file.open("seat.txt",ios::app|ios::out);
						file<<t_no<<" "<<s_no<<"\n";
						file.close();
					}
					ss_no[i]=s_no; 
					i++;
					cout<<"\n\n Booking another Seat (Y,N) : ";
					cin>>x;
				}while(x=='Y' || x=='y');
				system("cls");
				cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";
			    cout<<"\n\n Customer Name : ";
			    cin>>cus_name;
			    cout<<"\n\n Phone No. : ";
			    cin>>phone;
			    cout<<"\n\n From : ";
			    cin>>from;
			    cout<<"\n\n To : ";
			    cin>>to;
			    cout<<"\n\n Single Seat Amount : ";
			    cin>>s_amt; 
			    total_amt=s_amt*i;
			    cout<<"\n\n Total Amount to Pay : "<<total_amt;
			    cout<<"\n\n Receive amount : ";
			    cin>>r_amt;
			    file.open("customer.txt",ios::app|ios::in);
			    file<<cus_name<<" "<<t_no<<" "<<phone<<" "<<i<<" "<<total_amt<<"\n";
			    file.close();
			    system("cls");
			    cout<<"\n\t\t____________BUS MANAGMENT SYSTEM_____________";
			    cout<<"\n\n\t\t*********************************************";
			    cout<<"\n\n\t\t_____________Booking Information_____________";
			    cout<<"\n\n\t\t*********************************************";
			    cout<<"\n\n\t\tName :            "<<cus_name;
			    cout<<"\n\t\tFrom :              "<<from;
			    cout<<"\n\t\tTo :                "<<to;
			    cout<<"\n\t\tTotal Seats :       "<<i;
			    cout<<"\n\t\tReserved Seats :    ";
			    for(int a=0;a<i;a++){
			    	if(a!=0)
			    	  cout<<",";
			    	  cout<<ss_no[a];
				}
				cout<<"\n\t\tSingle Seat Amount:    "<<s_amt;
				cout<<"\n\t\tTotal Amount :         "<<total_amt;
				cout<<"\n\t\tReceive Amount :       "<<r_amt;
				cout<<"\n\t\tReturn Amount :        "<<r_amt-total_amt; 
				cout<<"\n\n\t\t*********************************************";
			    cout<<"\n\n\t\tThank you so much for Booking";
				cout<<"\n\n\t\t*********************************************";
			    
			}
			else{
				cout<<"\n\n Bus No. is Invalid...Please Try Again....";
				getch();
				goto p;
			}
		}
	}
	void bus::renew(){
		system("cls");
		fstream file;
		char x;
		cout<<"\n\t\t______________BUS MANAGMENT SYSTEM___________________";
		file.open("seat.txt",ios::in);
		if(!file){
			cout<<"\n\n File Opening Error.........";
		}
		else{
			cout<<"\n\n Do You Want Renew All Seats (Y,N) : ";
			cin>>x;
			if(x=='Y'|| x=='y'){
				remove("seat.txt");
				cout<<"\n\n\t\t\t All Seats Are Empty........";
			}
			else{
				cout<<"\n\n\t Thank You All Seats Reservation Saved......";
			}
		}
	}
	void bus::search_booking(){
		system("cls");
		fstream file;
		int t_seats,t_amo,found=0;
		string name,no,phone,t_name;
		cout<<"\n\t\t_____________BUS MANAGMENT SYSTEM____________";
		file.open("customer.txt",ios::in);
		if(!file){
			cout<<"\n\n File Opening Error........";
		}
		else{
			cout<<"\n\n Customer Name : ";
			cin>>t_name;
			file>>name>>no>>phone>>t_seats>>t_amo;
			while(!file.eof()){
				if(t_name==name){
					if(found==0){
						system("cls");
				        cout<<"\n\t\t_____________BUS MANAGMENT SYSTEM____________";
					}
					cout<<"\n\n\n Customer Name : "<<name;
					cout<<"\n\n Bus No. : "<<no;
					cout<<"\n\n Phone No. : "<<phone;
					cout<<"\n\n Reserved Seats : "<<t_seats;
					cout<<"\n\n Total Amount : "<<t_amo;
					cout<<"\n\n================================";
					found++;
				}
				file>>name>>no>>phone>>t_seats>>t_amo;
			}
			file.close();
			if(found==0){
				cout<<"\n\n Customer Name is Invalid......";
			}
		}
	}
	void bus::update_record(){
		system("cls");
		fstream file,file1;
		int t_seats,t_amo,found=0,del_seats,i=0;
		string name,no,phone,t_phone,del_no;
		cout<<"\n\t\t______________BUS MANAGMENT SYSTEM____________";
		file.open("customer.txt",ios::in);
		if(!file){
			cout<<"\n\n File Opening Error..........";
		}
		else{
			cout<<"\n\n Phone No. : ";
			cin>>t_phone;
			file>>name>>no>>phone>>t_seats>>t_amo;
			while(!file.eof()){
				if(t_phone==phone){
				    file.close();
				    file.open("customer.txt",ios::in);
				    file1.open("customer1.txt",ios::app|ios::out);
				    file>>name>>no>>phone>>t_seats>>t_amo;
				    while(!file.eof()){
				    	if(t_phone==phone){
				    		del_no=no;
				    		del_seats=t_seats;
						}
				    	if(t_phone!=phone){
				    		file1<<name<<" "<<no<<" "<<phone<<" "<<t_seats<<" "<<t_amo<<"\n";
						}
				    	file>>name>>no>>phone>>t_seats>>t_amo;
					}
					file.close();
					file1.close();
					remove("customer.txt");
					rename("customer1.txt","customer.txt"); 
					file.open("seat.txt",ios::in);
					file1.open("seat1.txt",ios::app|ios::out);
					file>>no>>t_seats;
					while(!file.eof()){
						if(!(del_no==no && i<del_seats)){
							file1<<no<<" "<<t_seats<<"\n";
						}
						file>>no>>t_seats;
					}
					file.close();
					file1.close();
					remove("seat.txt");
					rename("seat1.txt","seat.txt");
					booking();
					found++;
					goto h;	
				}
				file>>name>>no>>phone>>t_seats>>t_amo;
			}
			file.close();
			h:
			if(found==0){
				cout<<"\n\n Phone no. is Invalid......";
			}
		}
	}
	void bus::del_record(){
		system("cls");
		fstream file,file1;
		int t_seats,t_amo,found=0,del_seats,i=0;
		string name,no,phone,t_phone,del_no;
		cout<<"\n\t\t______________BUS MANAGMENT SYSTEM____________";
		file.open("customer.txt",ios::in);
		if(!file){
			cout<<"\n\n File Opening Error..........";
		}
		else{
			cout<<"\n\n Phone No. : ";
			cin>>t_phone;
			file>>name>>no>>phone>>t_seats>>t_amo;
			while(!file.eof()){
				if(t_phone==phone){
				    file.close();
				    file.open("customer.txt",ios::in);
				    file1.open("customer1.txt",ios::app|ios::out);
				    file>>name>>no>>phone>>t_seats>>t_amo;
				    while(!file.eof()){
				    	if(t_phone==phone){
				    		del_no=no;
				    		del_seats=t_seats;
						}
				    	if(t_phone!=phone){
				    		file1<<name<<" "<<no<<" "<<phone<<" "<<t_seats<<" "<<t_amo<<"\n";
						}
				    	file>>name>>no>>phone>>t_seats>>t_amo;
					}
					file.close();
					file1.close();
					remove("customer.txt");
					rename("customer1.txt","customer.txt"); 
					file.open("seat.txt",ios::in);
					file1.open("seat1.txt",ios::app|ios::out);
					file>>no>>t_seats;
					while(!file.eof()){
						if(!(del_no==no && i<del_seats)){
							file1<<no<<" "<<t_seats<<"\n";
						}
						file>>no>>t_seats;
					}
					file.close();
					file1.close();
					remove("seat.txt");
					rename("seat1.txt","seat.txt");
					
					found++;
					goto h;	
				}
				file>>name>>no>>phone>>t_seats>>t_amo;
			}
			file.close();
			h:
			if(found==0){
				cout<<"\n\n Phone no. is Invalid......";
			}
		}
	}
	void bus::show(){
		 system("cls");
		fstream file;
		int t_seats,t_amo,found=0;
		string name,no,phone;
		cout<<"\n\t\t_____________BUS MANAGMENT SYSTEM____________";
		file.open("customer.txt",ios::in);
		if(!file){
			cout<<"\n\n File Opening Error........";
	}
			file>>name>>no>>phone>>t_seats>>t_amo;
			while(!file.eof()){
				
					cout<<"\n\n\n Customer Name : "<<name;
					cout<<"\n\n Bus No. : "<<no;
					cout<<"\n\n Phone No. : "<<phone;
					cout<<"\n\n Reserved Seats : "<<t_seats;
					cout<<"\n\n Total Amount : "<<t_amo;
					cout<<"\n\n================================";
					found++;
					file>>name>>no>>phone>>t_seats>>t_amo;
				}
			file.close();
			if(found==0){
				cout<<"\n\n No Any Booking Record Found......";
			}
		}
			
main(){

	bus b;

	char ch;

	p:

	system("cls");

	string email,pass;

	cout<<"\n\n\t\t\t****Security are Required****";

	cout<<"\n\n Email: ";

	cin>>email;

	cout<<"\n\n Password: ";

	for(int i=1;i<=6;i++){

	   ch=getch();

	   pass+=ch;

	   cout<<"*";
	
	}

	if(email=="vanshitaagarwal2401@gmail.com" && pass=="vanshi"){

		cout<<"\n\n\n\t\t\tLoading";

		for(int i=1;i<=5;i++){

			Sleep(500);

			cout<<".";

			b.menu();

		}
	
	}

	else{

		cout<<"\n\n\t\tYour Email & password is wrong...";

		getch();

		goto p;

	


}


