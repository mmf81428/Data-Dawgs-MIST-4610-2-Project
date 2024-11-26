# Data-Dawgs-MIST-4610-Project-2

# Team Name
15058 Data Dawgs

# Team Members:
1. Anabelle Dolhun - [@Anabelledolhun](https://www.github.com/Anabelledolhun)
2. Hailey Franz - [@Haileyfranz](https://www.github.com/Haileyfranz)
3. Madeleine Fordham - [@mmf81428](https://www.github.com/mmf81428)
4. Alex Craig - [@ACC69908](https://www.github.com/ACC69908)
5. Dakota Corry - [@dakotamarie](https://www.github.com/dakotamarie)

# Scenario Description
The goal of this project is to model and implement a relational database system to help manage essential operational data for Delta airlines. The system mostly branches off from the main entity, trip, that connects information about airports, flights, tickets, baggage, passengers, and more through their relationships. This model is used to help centralize and organize key operational data improving efficiency in areas such as flight management, customer service, baggage handling, and employee assignments. The project includes queries to help produce and analyze data that can be used to enhance the overall experience for both the staff and passengers at Delta Airlines.

# Data Model
Our model works to connect entities within Delta in order to allow managers to filter information regarding customers, employees, flights, specific trips, airports, baggage, Delta accounts, and much more. 

The main center of the data model is the trip entity. The model has the following relationships: 

 The trip entity has a one-to-many identifying relationship with the ticket entity. A ticket can consist of many trips while a specific trip belongs to one specific ticket. This relationship allows managers to filter the tickets that are being bought most or least often. The relationship is identifying because a trip requires the ticket number to be uniquely defined.
 
The trip entity also has a one-to-many non-identifying relationship to the baggage entity. A specific trip can be associated with multiple bags while a specific bag can only be associated with one specific trip. This allows managers to filter data regarding baggage weight, type, etc for each individual trip. The relationship is non-identifying because baggage and trip can exist independently.

The trip entity also has two one-to-many relationships with the airport entity. One for departing airports, and one for arriving airports. An arriving airport can have many different trips, but a trip can only have one arriving airport. The same is true for a departing airport. These relationships help analyze popular flight routes without needing the airport keys for trip identification.

The trip entity has a one-to-many relationship with the passenger entity. A passenger can book multiple trips, but one specific trip is associated with one specific passenger. This relationship is non-identifying because a trip doesn’t need the passenger’s key for identification.

The passenger entity has a one-to-one relationship with the Delta Account entity. A passenger only has one Delta Account and a specific Delta Account can only be related to one customer. This is non-identifying because some customers may not have a Delta Account and it is therefore not necessary to define a specific passenger. 
The ticket entity has a one-to-many relationship with the flight entity. A flight can have many tickets associated with it, however, a specific ticket only links to a specific flight. This relationship is non-identifying because a flight is not necessary to define a ticket. 

The flight entity has a one-to-many relationship to the airplane entity. An airplane can have many different flights that it is used for, while a flight only uses one specific airplane. This relationship is non-identifying, because an airplane is not identified by its flight. 

The flight entity also has a one-to-many relationship with the flight crew entity. A flight crew can go on multiple flights but a flight only has one specific flight crew. This relationship is non-identifying because a flight is not identified by the flight crew that is on it. 

The flight crew entity has a many-to-many relationship with the employee entity. A flight crew can have multiple employees and an employee can work on many different flight crews. This relationship is identifying because you need to know both the employee and the flight crew they were working on to identify an employee on a flight crew. The weak entity of this many-to-many relationship, flight_crew_employee, is used to help connect the relationships. This entity helps identify the flight crew for a specific flight and what each of the employee’s specific roles were.

Finally, one of our improvements was to add a mantinenance entity. An airplane can have many mainenance visits, but one specific mainenance visit belongs to a specific airplane. The addition of this entity is useful because it can be used to track the maintenance dates, types, and statuses of each of the aircraft.

# Improvements

One of the first improvements of the model was the addition of the maintenance entity for a more thorough and complex model. Please see the description above for further information about this entity (last paragraph of the Data Model explanation).

The next improvement was adding the cardinalities to the model. This allows the optionality of each relationship to be documented. For example, the new model demonstrates that relationships like the one between employee and flight_crew_employee have a one to zero or many relationship. This is because an employee does not have to ever be on a flight crew, but an employee can still be on many instances of different flight crews.

The group then made adjustments to correct the non-identifying and identifying relationships on the data model. For example, there were more identifying relationships than necessary on the previous model because some of the relationships already had unique ids that did not require the identifying relationship between entities. For instance, the previous model included an identifying relationship between ticket and trip which is unnecessary because ticket and trip entities each have their own unique identifying primary keys. The new data model reflects the changes in altering this relationship to non-identifying.

Finally, the last modification made was that the total miles attribute was removed from the DeltaAccount entity. This attribute was removed because the total miles earned from a Delta account can already be determined using a query that joins DeltaAccount, passenger, and trip with the miles_earned attribute. 
