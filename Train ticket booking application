//paxName->passenger name
//paxAge->passenger age
//PNR->unique Ticket number
//pref->passenger prefered berth
//paxCount->passenger Count
//bno->Berth number
//mmopt->main menu option(the customer selection)

#include <stdio.h>
#include <string.h>

struct Berth {
    int status; /* 0=empty 1=booked */
    int berthNumber; /* 1 to 16 */
    char paxName[50];
    int paxAge;
    int PNR;
};

struct bookingForm {
    char paxName [ 50];
    int paxAge;
    int pref; /* 0 = LB; 1=MB; 2=UB; 3=NoChoice */
    int bno;
    int PNR;
    int paxCount;
    int Children;
};


  int vaCount=14;
  int raCount=4;
  int wlCount=2;
  int mmOpt;
  struct Berth berths[18];
  struct bookingForm bf[5];
  int numBookedPax=0;
  int SPNR=1001,SBNO=1;
  void dispMainMenu() {
    printf("Indian Railways Ticket Reservation System\n");
    printf("Main Menu\n \
                1. Book Ticket\n\
                2. Cancel Ticket\n\
                3. Print All\n\
                4. Print Availability\n\
                5. Exit Program\n");
    printf("Enter your Option:");
}

int getMainMenuInput() {
    int mmOption;
    scanf("%d", &mmOption);
    return(mmOption);
}

void bookTicket() {
    int numCurPax;char name[50];int age; int pref;
    
    printf("Book Ticket\n"); 
    printf("Enter no of pax:");
    scanf("%d", &numCurPax);
    if(numCurPax > (vaCount+raCount+wlCount)){
        printf("Tickets not available\n\
        Press any key to return to main menu");
        getchar();
        return;
    } else if (numCurPax >= (vaCount+raCount)) {
        printf("Tickets are in waiting list: Press Y to proceed, N to return to main menu:");
        if(getchar() == 'N') return;
    } else if (numCurPax >= (vaCount)){
        printf("Tickets are in RAC: Press Y to proceed, N to return to main menu:");
        if(getchar() == 'N') return;
    }
    for (int i=1; i<=numCurPax; i++) {
        printf("Enter your details\n\
            Name:");
        
        scanf("%s", bf[i].paxName);
        printf("Age:");
        scanf("%d", &age); bf[i].paxAge = age;
        printf("Preference: (0 = LB; 1=MB; 2=UB; 3=NoChoice}:");
        scanf("%d", &pref); bf[i].pref = pref;
        berths[numBookedPax].status=1;
        bf[i].PNR = SPNR;
        bf[i].bno = SBNO;
        SBNO+=1;
        SPNR+=1;
        berths[numBookedPax].berthNumber=bf[i].bno;
        
        //berths[numBookedPax].paxName = bf[i].paxName;
        strcpy(berths[numBookedPax].paxName,bf[i].paxName );
        berths[numBookedPax].paxAge = bf[i].paxAge;
        berths[numBookedPax].PNR=bf[i].PNR;
        numBookedPax++;
        
    }
    printf("Tickets Booked\n");
    printf("Name        Age     berthno     PNR\n");
    printf("======================================\n");
    for (int i=1; i<=numCurPax; i++) {
        printf("%s        %d     %d     %d\n", bf[i].paxName, bf[i].paxAge, bf[i].bno, bf[i].PNR );
    }
    numCurPax++;
    printf("======================================\n");
    
}
void canTicket() {
    
    int i,pnr;
    printf("enter the PNR no in your ticket:");
    scanf("%d",&pnr);
    for(i=0;i<=pnr;i++)
    {
        if(berths[i].PNR==pnr)
        {
            berths[i].status=0;
            berths[i].PNR=0;
          
            berths[i].berthNumber=0;
        }
    }printf("the ticket has been cancelled succussfully\n\n");
    
}
void printAll() {
    printf("Name     Age     BNO     PNR\n");
    printf("============================\n");
    for(int i=0;i<=18;i++){
        if(berths[i].status==1){
        printf("%s      %d       %d       %d\n",berths[i].paxName,berths[i].paxAge,berths[i].berthNumber,berths[i].PNR);}
        
    }
}
void printAvail() {
    int avail=0;
    printf("no of available seats:");
    for(int i=1;i<=18;i++){
        if(berths[i].status==0){
            avail++;
        }
    }printf("%d\n",avail);
}



  int main() {
      numBookedPax=0;
  do {
      dispMainMenu();
      mmOpt = getMainMenuInput();
      switch (mmOpt) {
          case 1: bookTicket();break;
          case 2: canTicket();break;
          case 3: printAll();break;
          case 4: printAvail();break;
          case 5: break;
      }
      
  } while (1);
  

    return 0;
}
