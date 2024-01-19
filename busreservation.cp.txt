#include <stdio.h>
#include <stdbool.h>
#include <string.h>
#include<ctype.h>
#define MAX_BUSES 5
#define MAX_SEATS 30
char cityleaving[50],citygoingto[50];
int dd,mm,yyyy,numSeats;
struct User user;
int  age,phonenumber,i,aadharnumber;
 bool valid = 0;
 char Sleeper[10],Standard[10],Deluxe[10];

int choice, seatNumber, size=0;
char buses[10];
char selectedBusType[100];
void initializeBus(bool seats[]);
void displaySeats(bool seats[]);
int reserveSeat(bool seats[], int seatNumber);


void displayBusFacilities(char facilities[][100],  char amenities[][100], int numBuses, char busType[]) {
    int i;
    int found = 0;

printf("Bus Facilities:\n");
    printf("-------------------------------------------------------\n");
    printf("Facilities\t\t\tAmenities\n");
    printf("-------------------------------------------------------\n");

    for (i = 0; i<numBuses; i++) {
        if (strstr(facilities[i], busType) != NULL) {
printf("%s\t\t\t%s\n",  facilities[i],  amenities[i]);
            found = 1;
        }
    }

    if (!found) {
printf("No facilities available for the selected bus type.\n");
    }

    printf("-------------------------------------------------------\n");
}

int reserveSeat(bool seats[], int seatNumber) {
    if (seatNumber< 1 || seatNumber> MAX_SEATS) {
printf("Invalid seat number.\n");

    }

    if (seats[seatNumber - 1]) {
printf("Seat %d is already reserved.\n", seatNumber);
    } else {
seats[seatNumber - 1] = true;
printf("Seat %d reserved successfully.\n", seatNumber);
    }
}
void cancelReservation(bool seats[], int seatNumber);

void initializeBus(bool seats[]) {
    for (int i = 0; i< MAX_SEATS; i++) {
        seats[i] = false;
    }
}


void displaySeats(bool seats[]) {
printf("Available seats: ");
    for (int i = 0; i< MAX_SEATS; i++) {
        if (!seats[i]) {
printf("%d ", i + 1);
        }
    }
    printf("\n");
}



void bookSeats(bool seats[], int numSeats) {
    int numTickets;
printf("Enter the number of tickets to book: ");
scanf("%d", &numTickets);
    for (int i = 0; i<numTickets; i++) {
printf("Enter the seat number for ticket %d: ", i + 1);
scanf("%d", &seatNumber);

reserveSeat(seats,seatNumber);
    }
}
void displayTicketPrices() {
printf("Ticket Prices:\n");
printf("1. sleeper: RS750.00\n");
printf("2. standard: RS650.00\n");
printf("3. deluxe: RS900.00\n");
}
void cancelReservation(bool seats[], int seatNumber) {
    if (seatNumber< 1 || seatNumber> MAX_SEATS) {
printf("Invalid seat number.\n");
        return;
    }
    if (seats[seatNumber - 1]) {
seats[seatNumber - 1] = false;
printf("Reservation for seat %d canceled.\n", seatNumber);
    } else {
printf("Seat %d is not reserved.\n", seatNumber);
    }
}
struct User {
    char name[50];
    char email[50];
    char gender[10];
 };
int isEmailValid( const  char *email) {
    if (strchr(email, '@') == NULL) {
        return false;
    }
    char *dot = strrchr(email, '.');
    if (dot == NULL || dot <strchr(email, '@')) {
        return false;
    }
    return true;
}
int main() {
    bool seats[MAX_SEATS];
initializeBus(seats); // Initialize the bus seats
     char facilities[MAX_BUSES][100] = {
        "Air Conditioning(Sleeper)",
        "TV Screens(Standard)",
        "Wi-Fi (Deluxe)",
        "Power Outlets (Deluxe)",
            };

    char amenities[MAX_BUSES][100] = {
        "Drinking Water(Sleeper)",
        "Snacks(Standard)",
        "Blankets (Deluxe)",
        "Reading Lights (Deluxe)",
        "Luggage Storage(Deluxe)"
    };
    do {
printf("\nBus Reservation System\n");

printf("1. Enter 1 to know  Facilities and Amenities available on bus\n");
printf("2. Enter 2 to begin the process\n");
printf("3. Enter 9 to book multiple tickets\n");
printf("4. Enter 10 to Cancel Reservation\n");
printf("5. enter 11 to Exit\n");
printf("Enter your choice: ");
scanf("%d", &choice);
        switch (choice) {
        case 1:
     int numBuses = sizeof(facilities) / sizeof(facilities[0]);
printf("Enter the type of bus ( Deluxe,Sleeper,Standard): ");
scanf("%s", selectedBusType);
displayBusFacilities(facilities,  amenities, numBuses, selectedBusType);
          break;  
        case 2:
printf("Enter the city leaving from\n");
            scanf("%s",cityleaving);
printf("Enter the city going to\n");
            scanf("%s",citygoingto);
            case 3:
printf("Enter the date of departure in the format dd/mm/yy\n");
scanf("%d/%d/%d", &dd, &mm, &yyyy);
          case 4:
displayTicketPrices();
printf("Enter the type of bus ( Deluxe,Sleeper,Standard): ");
scanf("%s", selectedBusType);
                 case 5:
displaySeats(seats);
            case 6:
printf("Enter the seat number to reserve: ");
scanf("%d", &seatNumber);
reserveSeat(seats, seatNumber);
            case 8:
printf("Enter your name: ");
scanf("%s", user.name);
     while (!valid) {
printf("Enter your email address: ");
scanf("%99s", user.email);
     if (isEmailValid(user.email)) {
            valid = true;
        } else {
printf("Invalid email address!\n");
        }
    }


printf("Enter your gender: ");
scanf("%s", user.gender);

printf("Enter your age: ");
scanf("%d", &age);
printf("_________________________________________________________");

        printf("\n");                                                                
printf("Ticket Details:\n");                                                      
printf("Name: %s\n", user.name);                    
printf("Email: %s\n", user.email);                    
printf("Gender: %s\n", user.gender);                
printf("Age: %d\n", age);                            
printf("Seat Number:%d\n", seatNumber); 
             if(selectedBusType==Sleeper)
             {
printf("Type of Bus:Sleeper\n");
             printf("Price:RS750.00\n");
             }
             else if(selectedBusType==Standard){
printf("Type of Bus:Standard\n");
             printf("Price:RS650.00\n");
             }
else{
printf("Type of Bus:Deluxe\n");
             printf("Price:RS900.00\n");
             }            
printf("Date of travelling:%d/%d/%d\n", dd, mm, yyyy);
printf("_________________________________________________________");
    break;
            case 9:
                      int numTickets;
printf("Enter the number of tickets to book: ");
scanf("%d", &numTickets);
printf("Enter the city leaving from\n");
            scanf("%s",cityleaving);
printf("Enter the city going to\n");
            scanf("%s",citygoingto);
printf("Enter the date of departure in the format dd/mm/yy\n");
scanf("%d/%d/%d", &dd, &mm, &yyyy);

displaySeats(seats);
                  for ( i = 0; i<numTickets; i++) {

printf("Enter the seat number for ticket %d: ", i + 1);
scanf("%d", &seatNumber);

reserveSeat(seats,seatNumber);

printf("Enter Passenger%d details: \n",i+1);
printf("Enter name: ");
scanf("%s", user.name);
     while (!valid) {
printf("Enter email: ");
scanf("%s", user.email);
    if (isEmailValid(user.email)) {
            valid = true;
        } else {
printf("Invalid email address!\n");
        }
        }
printf("Enter gender: ");
scanf("%s", user.gender);

printf("Enter age: ");
scanf("%d", &age);
    }

     for ( i = 0; i<numTickets; i++) {
printf("_____________________________________________________\n");
printf("Ticket Details of passenger %d:\n",i+1);

printf("Name: %s\n", user.name);
printf("Email: %s\n", user.email);
printf("Gender: %s\n", user.gender);
printf("Age: %d\n", age);
printf("Seat Number:%d\n", seatNumber);
            if(selectedBusType==Sleeper)
             {
printf("Type of Bus:Sleeper\n");
             printf("Price:RS750.00\n");
             }
             else if(selectedBusType==Standard){
printf("Type of Bus:Standard\n");
             printf("Price:RS650.00\n");
             }
else{
printf("Type of Bus:Deluxe\n");
             printf("Price:RS900.00\n");
             }
printf("Date of travelling:%d/%d/%d\n", dd, mm, yyyy);
printf("_________________________________________________");
       }

      break;
            case 10:
printf("Enter the seat number to cancel reservation: ");
scanf("%d", &seatNumber);
cancelReservation(seats, seatNumber);
                break;
            case 11:
printf("Exiting the program.\n");
                break;
            default:
printf("Invalid choice. Please try again.\n");    
        break;
    }} while (choice != 11);
    }


