# **Welcome to my Lab Report 2 Page !**

# Lab 2 : Servers and Bugs 

## Part 1: Servers


## Part 2: Bugs 

SearchEngine Code
--------------------------
>
    import java.io.IOException;
    import java.net.URI;

    class Handler implements URLHandler {
        String message = "Hello";

        public String handleRequest(URI url) {
            if (url.getPath().equals("/")) {
                return String.format(message);
            } else if (url.getPath().equals("/addSmiley")) {
                message += " there :) ";
                return String.format(message);
            } else {
                System.out.println("Path: " + url.getPath());
                if (url.getPath().contains("/addCheckup")) {
                    String[] parameters = url.getQuery().split("=");
                    if (parameters[0].equals("Name")) {
                        message += "\n" + parameters[1];
                        message += " hope you are doing well!";
                        return String.format(message);
                    }
                }
                return "Not Found!";
            }
        }
    }

    public class SearchEngine {
        public static void main(String[] args) throws IOException {
            if (args.length == 0) {
                System.out.println("Missing port number! Try any number between 1024 to 49151");
                return;
            }
            int port = Integer.parseInt(args[0]);
            Server.start(port, new Handler());
        }
    }

ScreenShot 1
--------------------------

ScreenShot 2
--------------------------

ScreenShot 3
--------------------------


### 1. 


Linked List: Append Method
--------------------------
FAILURE INDUCING INPUT : A linked list with elements {2, 3, 4}

![Image](LL_Append_FII.png)

SYMPTOM : Produced an infinite while loop, because n.next was being set to a new Node inside rather than outside the loop. --> Resulted in an error of "Java heap space"

![Image](LL_Append_Symptom.png)

BUG : Moved  "n.next = new Node(value, null);" from in inside the while loop to outside the while loop 

![Image](LL_Append_Bugs.png)

CHANGED : Method after making change

![Image](LL_Append_Changed.png)


### 2. 


Files: GetFiles Method
--------------------------

FAILURE INDUCING INPUT : A list of file paths and a folder path

![Image](Files_GetFiles_FII.png)
![Image](Files_GetFiles_FII2.png)


SYMPTOM : The expected order of the files in the list was different that tht order of the files outputed by the method. 

![Image](Files_GetFiles_Symptoms.png)

BUG : The method .listFiles() from the Files class does not put files in any particular order when adding them to an array. Therefore our expected outcome was different. To fix this I used the .sort method from the Arrays class to order the files alphabetically after they have been added to the array

![Image](Files_GetFiles_Bugs.png)

CHANGED : Method after making change

![Image](Files_GetFiles_Changes.png)

