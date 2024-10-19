Vehicle Rental Management System Project Report
Overview
This Python code implements a simple vehicle rental management system. It allows customers to rent, return, book, and search for vehicles. The system also handles customer registration, booking requests, and reminder functionality for vehicle rentals. Additionally, the system manages different types of vehicles, including luxury and regular vehicles, and supports both regular and premium customers.

Classes and Functions
Vehicle Class
The Vehicle class represents a vehicle that can be rented by customers. Each vehicle has the following attributes:

vehicle_id: A unique identifier for the vehicle.
make: The manufacturer of the vehicle (e.g., Toyota).
model: The specific model of the vehicle (e.g., Camry).
year: The year of manufacturing.
rental_rate: The daily rental rate for the vehicle.
availability: Boolean value indicating whether the vehicle is available for rent.
The class also includes a method print_details() to print the details of the vehicle.

Luxury Vehicle Class
The LuxuryVehicle class inherits from the Vehicle class and includes additional luxury features such as leather seats, GPS, automatic gear, and seat warmers. It modifies the rental rate by increasing it by 20% for luxury vehicles.

Customer Class
The Customer class represents a customer of the rental service. Each customer has the following attributes:

customer_id: A unique identifier for the customer.
name: The customer's name.
contact_info: Contact information of the customer.
rental_history: A list of the customer's past vehicle rentals.
The class includes methods print_details() to display customer information and view_history() to display the customer's rental history.

Booking Class
The Booking class represents a booking made by a customer. It stores information about the customer, the booked vehicle, the requested start time, the duration of the booking, and whether the booking has been completed.

Rental Manager Class
The RentalManager class manages a list of available vehicles. It includes methods for adding vehicles and generating reports about vehicle rentals and their users.

Functions
rent_vehicle Function
The rent_vehicle() function allows a customer to rent a vehicle for a specified duration. It checks the availability of the vehicle and applies a discount for premium customers. It also updates the customer's rental history and marks the vehicle as unavailable.

return_vehicle Function
The return_vehicle() function allows a customer to return a rented vehicle. It marks the vehicle as available again and removes the customer from the vehicle's user.

book Function
The book() function allows customers to book a vehicle in advance for a specified time and duration. It checks if the vehicle is available during the requested period and adds the booking to the system.

givebooking Function
The givebooking() function assigns the booked vehicle to the customer once the booking period starts. It checks if the current time matches the booking time and rents the vehicle if available.

search Function
The search() function allows users to search for vehicles based on multiple criteria, such as vehicle type, make, model, year, rental rate, or availability. The results can be sorted by various fields such as rental rate or year of manufacturing.

remind Function
The remind() function sends reminders to customers one day before their rental is due, reminding them to return the vehicle. It adjusts the message for premium customers by applying the discount to the rental rate.

Problems Faced
While working on the booking function, it was necessary to track time so that the user would get notified that it is time to receive their vehicle. Time tracking would also need to be used to check if two bookings of the same vehicle are clashing or to make sure another user does not rent a car that is booked later during this rent time. To add this functionality, I used the datetime module, first converting the time span of a day in reality to a minute in the program—for quicker testing.

The givebooking() and remind() functions are continuously called in the main loop, but I ran into one major problem with this approach. I planned to run a while loop that continually takes user input for renting, booking, returning, and searching vehicles. This was to take care of the case where the user might want to rent multiple vehicles at a time. But if the CLI is asking for some input and the user delays in giving input, the remind function will not be called until the user provides the input, thus delaying the reminder function. To solve this, one option is to implement threading and Queues, which will allow the time-related functions to run in parallel with the main program without interfering with the inputs.

Outputs

