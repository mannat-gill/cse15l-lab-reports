# **Welcome to my Lab Report 2 Page !**

# Lab 2 : Servers and Bugs 

## Part 1: Servers

SearchEngine Code
--------------------------
>

    import java.io.IOException;
    import java.net.URI
    class Handler implements URLHandler {
        String message = "Hello";

        public String handleRequest(URI url) {
            if (url.getPath().equals("/")) {
                return String.format(message);
            } else if (url.getPath().equals("/addSmiley")) {
                message += " there :) ";
                return String.format(message);
            } else if(url.getPath().equals("/remove")) {
                if(message.length()>5){
                    message = message.substring(0, 5); 
                }
                return String.format(message);
            }
            else {
            
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/addPerson")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("Name")) {
                    names.add(parameters[1]);
                    return "Added: "+ parameters[1];
                }
                else if(parameters[0].equals("printPersons")){
                        String outputFriends = ""; 
                        for(String x: names){
                            if(x.contains(parameters[1])){
                                outputFriends += x + " "; 
                            }
                        }
                        return outputFriends; 
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

ScreenShot 1 : Opening Link
--------------------------
When you first run the SearchEngine.java class using this following command (shown in the picture) wth any value (in my case 4444). It will generate a link. 

![Image](Lab_Report_2_Photos/Server_callingServer.png)

Opening the link will show you the following. When creating the link it calls on the method start from the Server class, passing in the integer value we entered along with a Handler object. When the Handler object is created it declares and initializes the string message to Hello. 

![Image](Lab_Report_2_Photos/Server_OpeningLink.png)

ScreenShot 2 : addSmiley
--------------------------
When you add the path "addSmiley", it goes into the method handleRequest and by going through the if statements, when the first if else statement comes back true for the path being "addSmiley", it adds " there :)" to the message. 

![Image](Lab_Report_2_Photos/Server_AddUse.png)

ScreenShot 3 : remove
--------------------------
When you add the path "remove", the else if statement comes back true for the path being "remove" and then changes the String message back to the original initilization of it being just "Hello"

![Image](Lab_Report_2_Photos/UsingRemove.png)

ScreenShot 4 : addPerson
--------------------------
When you add the path "addPerson", it checks to see if the query is "Name" or "printPersons" by checking the array of Strings at index 0, where we stored the arguments of the query after splitting them. For the case of it being "Name", it adds the name you entered. 

For Example: "/addPerson?Name=sachi" will add sachi 

![Image](Lab_Report_2_Photos/addPerson_sachi.png)

Then I added the following two more

![Image](Lab_Report_2_Photos/addPerson_puneet.png)
![Image](Lab_Report_2_Photos/addPerson_sherry.png)

Now using "printPersons" we will search the list of people we added to filter out ones not containg the substring we passed through. 

For Example: "/addPerson?printPersons=h" will output the names containing the substring 'h'

![Image](Lab_Report_2_Photos/printPersons_with_h.png)

## Part 2: Bugs 

### 1. 


Linked List: Append Method
--------------------------
FAILURE INDUCING INPUT : A linked list with elements {2, 3, 4}

![Image](Lab_Report_2_Photos/LL_Append_FII.png)

SYMPTOM : 

![Image](Lab_Report_2_Photos/LL_Append_Symptom.png)

BUG : Moved  "n.next = new Node(value, null);" from inside the while loop to outside the while loop 

![Image](Lab_Report_2_Photos/LL_Append_Bugs.png)

SYMPTOM & BUG CONNECTION: When you append a value, and neither the root nor the next node after the root is null, then it enters the while loop. However it produces an infinite while loop, because n.next was being set to a new Node inside rather than outside the loop. --> Resulted in an error of "Java heap space". 


CHANGED : Method after making change (shown below)

![Image](Lab_Report_2_Photos/LL_Append_Changed.png)



### 2. 


File: GetFiles Method
--------------------------

FAILURE INDUCING INPUT : A list of file paths and a folder path

![Image](Lab_Report_2_Photos/Files_GetFiles_FII.png)
![Image](Lab_Report_2_Photos/Files_GetFiles_FII2.png)


SYMPTOM : The expected order of the files in the list was different than the order of the files outputed by the method. 

![Image](Lab_Report_2_Photos/Files_GetFiles_Symptoms.png)

BUG : The method .listFiles() from the Files class.

![Image](Lab_Report_2_Photos/Files_GetFiles_Bugs.png)

SYMPTOM & BUG CONNECTION: Since the method .listFiles() from the Files class does not put files in any particular order, when adding them to an array, our expected outcome is different. To fix this I used the .sort method from the Arrays class to order the files alphabetically after they have been added to the array

CHANGED : Method after making change

![Image](Lab_Report_2_Photos/Files_GetFiles_Changes.png)

