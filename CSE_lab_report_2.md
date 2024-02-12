## CSE 15L Lab 2
# Part 1

**Creating ChatServer**

Code of Chat Server:

<img width="603" alt="ChatServer" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/1b5aa0d0-bae7-475b-aa33-4fa81c92e6fd">

**Which methods are called in this code?**

The code has two classes, one being the actual class `ChatServer`, and the other being the Class `Handler` (containing that /add-message). The methods
called within the `ChatServer` class include the `parseInt` method and the `.start` method. The `Handler` class has several
methods called including the `.getpath()` method as well as `.size()` and `.get()` from the `ArrayList` class. We also used
the `.getQuery()` and `.split()` in order to process the input url and split it based on the input characters. Lastly, we
also used the `.add()` method and `.contains()` methods.

**What are the relevant arguments to those methods, and the values of any relevant fields of the class?**

The methods that are used are `parseInt()` as well as `.start()`. The relevant arguments for `.parseInt()` is the 
integer that we want to convert into a string. In this case the argument passed in is `args[0]`. 

The other method, the `.start()` takes in two arguments, one being the `Handler` and the other being the port in which 
we are running the server. It looks like `.start(port, new Handler())`.

The relevant fields of the class is mainly just the `ArrayList` called `tracking` for the Handler class and there are no arguments passed into the `ChatServer` class.

**How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.**

There no actual fields for the ChatServer class, however there are fields for the Handler class in which the `ArrayList` called `tracking`  does not change either with any of the methods. This is because we return a `String` created within the `Handler` class. 

In addition, the 
`.start()` method creates a `new Handler()` but doesn't change any existing fields of the class. 


**Screenshots of how the `/add-message` works:**

```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.

    //created ArrayList to keep track of the strings passed in
    ArrayList<String> tracking = new ArrayList<>();

    public String handleRequest(URI url) {
        //default: if nothing is passed into the url
        if (url.getPath().equals("/")) {
            
            String formatted = "";

            for (int i =0; i<tracking.size(); i++){
                formatted=tracking.get(i)+"\n";
            }
            return formatted;

        //if messages are added, this will run
        } else {
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                String[] fullySplit =parameters[1].split("&");
                String add = parameters[2]+ ": "+ fullySplit[0];
                tracking.add(add);

                String formatted = "";

                for (int i =0; i<tracking.size(); i++){
                    formatted+=tracking.get(i)+"\n";
                }

                return formatted;
                
            }
            return "404 Not Found!";
        }
    }
}

class ChatServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```


<img width="481" alt="1line" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/fcf69211-3935-42c3-a690-57fa2d021763">

<img width="487" alt="2line" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/d31389c7-f5de-4e6f-b069-4fecb98207e7">

<img width="401" alt="3line" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/14bf4240-1f22-4656-8e8a-29c74105b2c8">

<img width="490" alt="4line" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/16d68cdb-f645-4def-b909-55c3ad16bae7">

**Which methods are called in this code?**

The methods called within the part using `/add-message` include `handleRequest()`, `.getQuery()`, `.split()`, `.add()`, `.get()`, and `.size()`. 
Most of these methods are called on the `ArrayList` that was declared previously called tracking.

**What are the relevant arguments to those methods, and the values of any relevant fields of the class?**

The fields in the `Handler` class that I created was the `ArrayList` tracking in order to keep track of all the user input
and eventually return the formatted version of it. 

The methods called/relevant arguments include:

`handleRequest()` -- the argument for this is the URL    
`.getpath()` -- there was no argument within this, rather the output we get from that was used to call the `.equals()` method
on the argument "/" which is the defualt where the user doesn't put anything else into the url.

In `/add-message` section:`.size()` -- there is no argument for this method of the `ArrayList` class, rather it is called upon the list itself. 

In `/add-message` section:`.get()` -- the argument for this passed into the method was the index of the location that we wanted.

`.contains()` -- this method was used after the `.getpath()` method in order to see if the user input contained the 
desired string. The argument passed in was the desired string.

In `/add-message` section:`.add()` -- this method was used to add onto tracking, the input argument is the element that we want to add.

In `/add-message` section: `.getQuery()` -- this had no arguments passed in but the output from this method being called was a string that was 
later split using the `.split()` method which takes in an argument that represents the location of being split.

**How do the values of any relevant fields of the class change from this specific request? If no values got changed, explain why.**

`.getpath()` -- No values get changed because of this request since the only 
on the argument "/" which is the defualt where the user doesn't put anything else into the url. Eventually
the existing tracking field is returned with no changes made.

In `/add-message` section: `.size()` -- there is no change because of this, the size of the existing `ArryaList` is returned.

In `/add-message` section: `.get()` -- the is no change for this either, it's just getting what is already existing in the `ArrayList`.

`.contains()` -- there is no change because of this method either since it is merely checking if the input contains
certain characters.

In `/add-message` section: `.add()` -- this does change the existing tracking field since we're adding onto it.

In `/add-message` section: `.getQuery()` -- this doesn't change any fields since it's just retrieving the user input. 

In `/add-message` section: `.split()` -- this doesn't change the field tracking list but, it does change the user input by spliting at
certain characters which is then stored in the `String [] parameters`.


# Part 2

The screenshot below is for finding the absolute path to the private key within my local machine. The absolute path I used was `C:\Users\keert\.ssh`. I then used `ls` to get the contents of the directory where the private key `id_rsa` was located.

<img width="372" alt="pwd" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/a95184a7-1e00-49f7-a39b-7e02b02715a7">

The screenshot below is for finding the absolute path to the public key within my ieng6 machine. The absolute path used was 
`/home/linux/ieng6/oce/38/knalabotu/.ssh` shown by the `pwd` and soon after when I used `ls` I got the contents of the directory including the public key which is `id_rsa.pub`.

<img width="514" alt="pwd1" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/8426b280-6028-4936-9c85-260c4f148714">


The screenshots above show how I used `ls` to get into the directory that contained the private and public keys shown by `id_rsa.` for the private key and `id_rsa.pub.` for the public key. The two screenshots show how I used `cd` to get into 
the directories in which they were stored. Then I used `pwd` to get the absolute path and lastly `ls` to see the
contents of the absolute path.

To eventually get to a place where you don't have to sign into your ieng6 account, we have to use `scp <path to your public SSH key> user@ieng6.ucsd.edu:~/.ssh/authorized_keys` which I used. The following screenshot shows the process of being able to login without having to use my password again.

<img width="502" alt="logging_in" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/d102658c-8165-4f6b-a024-fa52fb9c671a">

# Part 3

**In a couple of sentences, describe something you learned from lab in week 2 or 3 that you didn't know before.**

I learned a lot this week in terms of understanding what it meant to run a server and creating your own ssh keys. 
I also thought it was cool how I could create the local host and view the output of my code in a completely new browser. 
This was cool since I've never had the experience of creating the new browser and being able to see the affect of
my code on a different platform other than the terminal and output on vscode or edstem.
