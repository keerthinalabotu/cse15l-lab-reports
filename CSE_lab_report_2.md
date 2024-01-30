## CSE 15L Lab 2
# Part 1

**Creating ChatServer**

Code of Chat Server:

<img width="603" alt="ChatServer" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/1b5aa0d0-bae7-475b-aa33-4fa81c92e6fd">

Which methods are called in this code?

The code has two classes, one being the actual class ChatServer, and the other being the Class Handler (containing that /add-message). The methods
called within the ChatServer class include the `parseInt` method and the `.start` method. The Handler class has several
methods called including the `.getpath()` method as well as `.size()` and `.get()` from the ArrayList class. We also used
the `.getQuery()` and `.split()` in order to process the input url and split it based on the input characters. Lastly, we
also used the `.add()` method and `.contains()` methods.

What are the relevant arguments to those methods, and the values of any relevant fields of the class?

The methods that are used are `parseInt()` as well as `.start()`. The relevant arguments for `.parseInt()` is the 
integer that we want to convert into a string. In this case the argument passed in is args[0]. 

The other method, the `.start()` takes in two arguments, one being the Handler and the other being the port in which 
we are running the server. It looks like `.start(port, new Handler())`.

How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

When `.parseInt()` is carried out, the field passed in which is `args[0]` is changed to a string format. In addition, the 
`.start()` method creates a `new Handler()` but doesn't change any existing fields of the class. 


**Screenshots of how the `/add-message` works:**

<img width="554" alt="FirstPartOfChatServer" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/cf3b36d7-8e7f-48da-8df5-8d54133b8efa">

**this is the part specifically for `/add-message`:**
<img width="597" alt="SecondPartofChatServer" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/06a85086-7dbf-4a34-9330-4305229d701e">

<img width="607" alt="ThridPartOfChatServer" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/f8d65f80-c43b-4ad8-bdb1-2079f491e08d">

<img width="481" alt="1line" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/fcf69211-3935-42c3-a690-57fa2d021763">

<img width="487" alt="2line" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/d31389c7-f5de-4e6f-b069-4fecb98207e7">

<img width="401" alt="3line" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/14bf4240-1f22-4656-8e8a-29c74105b2c8">

<img width="490" alt="4line" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/16d68cdb-f645-4def-b909-55c3ad16bae7">

Which methods are called in this code?

The methods called within the part using /add-message include `.getQuery()`, `.split()`, `.add()`, `.get()`, and `.size()`. 
Most of these methods are called on the ArrayList that was declared previously called tracking.

What are the relevant arguments to those methods, and the values of any relevant fields of the class?

The fields in the Handler class that I created was the ArrayList tracking in order to keep track of all the user input
and eventually return the formatted version of it. 
The methods called/relevant arguments include:
`.getpath()` -- there was no argument within this, rather the output we get from that was used to call the `.equals()` method
on the argument "/" which is the defualt where the user doesn't put anything else into the url.
In `/add-message` section:`.size()` -- there is no argument for this method of the ArrayList class, rather it is called upon the list itself. 
In `/add-message` section:`.get()` -- the argument for this passed into the method was the index of the location that we wanted.
`.contains()` -- this method was used after the `.getpath()` method in order to see if the user input contained the 
desired string. the argument passed in was the desired string
In `/add-message` section:`.add()` -- this method was used to add onto tracking, the input argument is the element that we want to add.
In `/add-message` section: `.getQuery()` -- this had no arguments passed in but the output from this method being called was a string that was 
later split using the `.split()` method which takes in an argument that represents the location of being split.

How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.

`.getpath()` -- No values get changed because of this request since the only 
on the argument "/" which is the defualt where the user doesn't put anything else into the url. Eventually
the existing tracking field is returned with no changes made.
In `/add-message` section: `.size()` -- there is no change because of this, the size of the existing ArryaList is returned.
In `/add-message` section: `.get()` -- the is no change for this either, it's just getting what is already existing in the ArrayList.
`.contains()` -- there is no change becuase of this method either since it is merely checking if the input contains
certain characters
In `/add-message` section: `.add()` -- this does change the existing tracking field since we're adding onto it.
In `/add-message` section: `.getQuery()` -- this doesn't change any fields since it's just retrieving the user input. 
In `/add-message` section: `.split()` -- this doens't change the field tracking list but, it does change the user input by spliting at
certain characters which is then stored in the `String [] parameters`.

# Part 2




# Part 3

In a couple of sentences, describe something you learned from lab in week 2 or 3 that you didn't know before.

I learned a lot this week in terms of understanding what it meant to run a server and creating your own ssh keys. 
I also thought it was cool how I could create the local host and view the output of my code in a completely new browser. 
This was cool since I've never had the experience of creating the new browser and being able to see the affect of
my code on a different platform other than the terminal and output on vscode or edstem.