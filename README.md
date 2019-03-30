# Complete-Sleeping-Barber-Solution

I implemeted my own Semaphores you can see the code files in semaphore library file uploaded in this github  
for Expalnation for those implemtation please see readme files of github files 
https://github.com/lokeshreddy1999/producer_consumer_solution

Now I am  going to explain solution of  Complete(deadlock free starvation)-Sleeping-Barber-Solution  

Problem statement:The barber shop has one barber, one barber chair, and n chairs for waiting customers, if any, to sit on. If there are
no customers present, the barber sits down in the barber chair and falls asleep.
When a customer arrives, he has to wake up the sleeping barber. If additional customers arrive while the barber is cutting a customer's hair, they
either sit down (if there are empty chairs) or leave the shop (if all chairs are full). The problem is to program the barber and the customers without getting into race conditions

Solution:Our solution uses three semaphores, customers, which counts waiting customers (excluding the customer in the barber chair, who is not waiting), barbers, the number of
barbers (0 or 1) who are idle, waiting for customers, and mutex, which is used for mutual exclusion. We also need a variable, nof of free seats
to know no of waiting customers.This solution, a customer entering the shop has to count the number of waiting customers. If it is less than the number of chairs, he stays; otherwise, he leaves


When the barber shows up for work in the morning,he executes the procedure barber, causing him to block on the semaphore customers
because it is initially 0. The barber then goes to sleep.He stays asleep until the first customer shows up. 

When a customer arrives, he executes customer, starting by acquiring mutex to enter a critical region. If another customer enters shortly thereafter, the second one will no be able to do anything until the first one has released mutex. The customer then checks to
see if the number of waiting customers is less than the number of chairs. If not, he releases mutex and leaves without a haircut
If there is an available chair, the customer decrements the integer variable, free_seats. Then he does an Up on the semaphore customers, thus waking up the barber. At this
point, the customer and the barber are both awake. When the customer releases mutex, the barber grabs it, does some housekeeping, and begins the haircut.

When the haircut is over, the customer exits the procedure and leaves the shop. Unlike our earlier examples, there is no loop for the customer because each one gets only
one haircut. The barber loops, however, to try to get the next customer. If one is present,a haircut is given. If not, the barber goes to sleep



for complete code please see in the .c 
