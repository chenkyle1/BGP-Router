# CS3700 Project 3: BGP Router

Steven Ngo and Kyle Chen

## High Level Approach

As we were given both starter code and the different test cases, we began
by reviewing both to gain a basic understand of the structure of the router and the different types and format
of messages that were being sent. We then followed along with the suggested implementation approach by designing
support for "update" and "data" messages. Our update method would add a new router in our forwarding table and send
an announcement to its neighboring routers. Our data method forwarded the message to its neighbors by looking up
the routes on the forwarding table and the dump function which forwarded the table to the requesting source. For the
five rules of selecting a path, we implemented each of the rules as an independent function, where the list of 
possible routes would go each of the rules until there was one left. When implementing withdraw functionality, we 
split it into three steps where the message is appended to a list of withdraw messages, the forwarding table
is filtered and the message is forwarded to each neighbor. We modified our send message to neighbor function to 
include cases for peers and customers, which enabled us to pass the level 4 tests. For longest prefix matching we
converted the addresses to binary, compared them using bitwise operators and determined the length of the match in
bits.

## Challenges

One challenge we face was understanding the format of the messages and how to extract specific data
from them, as well as how to represent them in the forwarding table. Another minor challenge was debugging, as 
it felt like there was a lot of data in the test cases, which we had to examine to determine the source of the 
bug. However, this was easily resolved through closer evaluation of the given address in the error message
and print statements throughout the program. As we progressed past milestone 1 to the final program, the biggest
challenge we faced was how to implement the longest prefix matching because it required us to think about
our logic. We had to think of many ideas as to how to iterate through the list of routes and extract the address
then compare each of them after being converted to binary. It was the process of then keeping track of the 
address which the longest prefix that challenged us since it was in binary during the comparison, which we resolved
using bitwise logic and for loops and if statements

## Features

Some design methods we utilized in our program was the delegation of certain tasks into helper functions which 
made our program easier to understand. We also added many comments throughout the code, which assisted each other
when we worked independently and had to combine. We also used specific data structures of arrays and dictionaries
for various types of data such as the forwarding table and relationships. For each of the five rules, we tried to
make it as efficient as possible by not iterating through the routes to find the highest localpref, for example

## Testing

We tested our implementation by printing out all the messages sent and received from the router, which we
were able to use during the tests to debug and ensure that our program ran as expected. The logging library was
essential to debugging our program, as it enabled us to determine where a specific debugging message was being
sent in the list of messages being printed