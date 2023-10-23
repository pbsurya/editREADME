HOTEL MANAGEMENT


#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_ROOMS 50

struct Reservation 
{
    char guestName[50];
    int roomNumber;
    int duration;
};

struct Hotel 
{
    struct Reservation reservations[MAX_ROOMS];
    int numReservations;
};

void makeReservation(struct Hotel *hotel, 
const char *guestName, 
int roomNumber, 
int duration) 
{
    if (hotel->numReservations < MAX_ROOMS) 
    {
        struct Reservation newReservation;
        strncpy(newReservation.guestName, guestName, 
        sizeof(newReservation.guestName) - 1);
        
        newReservation.roomNumber = roomNumber;
        
        newReservation.duration = duration;

        hotel->reservations[hotel->numReservations++] = newReservation;

        printf("Reservation made successfully.\n");
    } else
    {
        printf("Hotel is fully booked. Cannot make more reservations.\n");
    }
}

void displayReservations(struct Hotel hotel) 
{
    printf("Reservation Records:\n");

    for (int i = 0; i < hotel.numReservations; ++i) 
    {
        printf("Guest: %s\nRoom: %d\nDuration: %d days\n\n",
        hotel.reservations[i].guestName, hotel.reservations[i].roomNumber, hotel.reservations[i].duration);
    }
}

int main() 
{
   struct Hotel myHotel = {{}, 0};

    makeReservation(&myHotel, "surya", 101, 3);
    
    makeReservation(&myHotel, "divya", 202, 5);

    displayReservations(myHotel);
return 0;
}
