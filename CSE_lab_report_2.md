## CSE 15L Lab 2
# Part 1

**Creating ChatServer**

Code of Chat Server:

<img width="554" alt="FirstPartOfChatServer" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/46954ce5-1300-454f-874a-4480ee3ef546">


<img width="597" alt="SecondPartofChatServer" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/06a85086-7dbf-4a34-9330-4305229d701e">


<img width="607" alt="ThridPartOfChatServer" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/f8d65f80-c43b-4ad8-bdb1-2079f491e08d">

Which methods are called in this code?

The code has two classes, one being the actual class ChatServer, and the other being the Class Handler. The methods
called within the ChatServer class include the parseInt method and the .start method. The Handler class has several
methods called including the `.getpath()` method as well as `.size()` and `.get()` from the ArrayList class. We also used
the `.getQuery()` and `.split()` in order to process the input url and split it based on the input characters. Lastly, we
also used the `.add()` method and `.contains()` methods.

What are the relevant arguments to those methods, and the values of any relevant fields of the class?

The fields in the Handler class that I created was the ArrayList tracking in order to keep track od all the user input
and eventually return the formatted version of it. 
The methods called/relevant arguments include:
`.getpath()` -- there was no argument within this, rather the output we get from that was used to call the `.equals()` method
on the argument "/" which is the defualt where the user doesn't put anything else into the url.
`.size()` -- there is no argument for this method of the ArrayList class, rather it is called upon the list itself. 
`.get()` -- the argument for this passed into the method was the index of the location that we wanted.
`.contains()` -- this method was used after the `.getpath()` method in order to see if the user input contained the 
desired string. the argument passed in was the desired string
`.getQuery()` -- this had no arguments passed in but the output from this method being called was a string that was 
later split using the `.split()` method which takes in an argument that represents the location of being split.

How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.
`.getpath()` -- No values get changed because of this request since the only 
on the argument "/" which is the defualt where the user doesn't put anything else into the url. Eventually
the existing tracking field is returned with no changes made.
`.size()` -- there is no change because of this, the size of the existing ArryaList is returned.
`.get()` -- the is no change for this either, it's just getting what is already existing in the ArrayList.
`.contains()` -- there is no change becuase of this method either since it is merely checking if the input contains
certain characters
`.add()` -- this does change the existing tracking field since we're adding onto it.
`.getQuery()` -- this had no arguments passed in but the output from this method being called was a string that was 
later split using the `.split()` method which takes in an argument that represents the location of being split.
