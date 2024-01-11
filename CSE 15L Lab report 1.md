## CSE 15L Lab 1
# Using no arguments
The comman `cd` lets us establish which directory we want to go to

`[user@sahara ~] $ cd` returns nothing 
`[user@sahara ~] $ ls` returns `lecture1` since that is the current list of what we have under the directory
`[user@sahara ~] $ cat` returns nothing as well since you're not concactenating anything at the moment

The image below shows all three results:

<img width="219" alt="screen3" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/5508e894-09f8-4288-aafd-f29e2f37c107">


# example of using the command with a path to a directory as an argument

`[user@sahara ~] $ cd lecture1` doesn't return anything but it changes where currrent directory is so the next line ends up looking like this: 
`[user@sahara ~/lecture1] $`


<img width="215" alt="cd" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/cd6a528f-a2bc-464b-a649-e79909729384">


`[user@sahara ~] $ ls ./messages` after setting the directory to lecture1 returns the following:
`en-us.txt  es-mx.txt  german.txt  zh-cn.txt`


<img width="316" alt="screen2" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/7dbfd53a-7285-4008-be9a-49cc3eddd02a">


`[user@sahara ~] $ cat ./messages/en-us.txt ./messages/es-mx.txt` after putting in the two directories returns the following:
the screenshot of the result is this: 


<img width="532" alt="screen1" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/c1c11931-d913-46d9-94bf-5a4f98917e08">

# Share an example of using the command with a path to a file as an argument.

When we try to use the path to a file for the `cd` command we get an *error* saying it's a directory since cd doesn't take in paths to files:


<img width="387" alt="Screens" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/5ef28450-bcf3-4579-a5fb-660f2fb748f9">

When we try to to the same thing with `ls` we get the file path since it will just list the path for the text file:


<img width="349" alt="screen10" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/e6240360-286d-4b3f-9eb0-f83ea509626a">

Lastly when we `cat` with the file path to the text file we get the contents of the file since it concactenates them. If we had added another path we would
have gotten the contents of both files in the result: 


<img width="362" alt="scr" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/91380181-6995-4d30-b6cc-42148c489415">



