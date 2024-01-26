## CSE 15L Lab 1
# Using no arguments

The comman `cd` lets us establish which directory we want to go to
`[user@sahara ~] $ cd` When we use cd it takes us back to the home directory. When we try going into a different directory beforehand and then use cd on it, it'll take us back to the home directory as well.

`[user@sahara ~] $ ls` returns `lecture1` since that is the current list of what we have under the directory.

`[user@sahara ~] $ cat` When we use cat it shows nothing but that is because it's waiting for user input to concactenate sicne it's function is to concactenate the files and show us what is in the file passed in by the user.

Note: the current directory for all of these commands (`cd`, `ls`, `cat`) is the ~ which is the home directory. This is for all of the three commands we did above including cs, ls, and cat.

The image below shows all three results:

<img width="219" alt="screen3" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/5508e894-09f8-4288-aafd-f29e2f37c107">


# example of using the command with a path to a directory as an argument

`[user@sahara ~] $ cd lecture1` doesn't return anything but it changes where currrent directory is so the next line ends up looking like this: 
`[user@sahara ~/lecture1] $`


<img width="215" alt="cd" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/cd6a528f-a2bc-464b-a649-e79909729384">

The current working directory for `cd` this is the ~ which is the home directory.

`[user@sahara ~] $ ls ./messages` after setting the directory to lecture1 returns the following:
`en-us.txt  es-mx.txt  german.txt  zh-cn.txt`


<img width="316" alt="screen2" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/7dbfd53a-7285-4008-be9a-49cc3eddd02a">

The current working directory for the `ls` that we used above is also ~ which is the home directory.


`[user@sahara ~] $ cat ./messages/en-us.txt ./messages/es-mx.txt` after putting in the two directories returns the following:
the screenshot of the result is this: 


<img width="532" alt="screen1" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/c1c11931-d913-46d9-94bf-5a4f98917e08">

The current working directory for the `cat` is the ~ which is also the home directory.

# Share an example of using the command with a path to a file as an argument.

When we try to use the path to a file for the `cd` command we get an *error* saying it's a directory since cd doesn't take in paths to files:


<img width="387" alt="Screens" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/5ef28450-bcf3-4579-a5fb-660f2fb748f9">

The current working directory for what we did with `cd` was the ~ which goes back to the home directory.

When we try to to the same thing with `ls` we get the file path since it will just list the path for the text file:


<img width="349" alt="screen10" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/e6240360-286d-4b3f-9eb0-f83ea509626a">

The current working directory for what we did with `ls` is also the ~ which is the home directory.

Lastly when we `cat` with the file path to the text file we get the contents of the file since it concactenates them. If we had added another path we would have gotten the contents of both files in the result: 


<img width="362" alt="scr" src="https://github.com/keerthinalabotu/cse15l-lab-reports/assets/144857467/91380181-6995-4d30-b6cc-42148c489415">

The current working directory for `cat` is also the ~ which is the home directory. The contents that are passed into the `cat` have their contents displayed.

