
# Lab Report 3

# Part 1

**SearchEngine Code:**

```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> s = new ArrayList<String>();
    
    public String handleRequest(URI url) {
        
        System.out.println("Path: " + url.getPath());
        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                s.add(parameters[1]);
                return String.format("String added! The String List is now: " + s);
            }
        }
        else if (url.getPath().contains("/search")) {
            ArrayList<String> subarr=new ArrayList<String>();
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                String containString = parameters[1];
                for(int x = 0; x < s.size(); x++){
                    if(s.get(x).contains(containString)){
                        subarr.add(s.get(x));
                    }
                }
                return String.format("These words in the list contain " + containString + ": " + subarr);
            }
            
        }
        return "404 Not Found!";
        
    }
}

class SearchEngine {
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

When you include the path, `/add?s=<String>`, then it adds `<String>` to the list. The code calls the handlerRequest method. Since the path contains `add`, it immediately iterates through the first if statement. Then it takes the argument `<String>` and adds it to the list.

![Search Engine add](/images/searchengineadd1.jpg)

WHen you include the path, `/search?s=<String>`, it returns an array of words that contains `<String>`. The code calls the handlerRequest method. Since the path contains `search`, it iterates through the else if statement, where it returns an array of strings that contain `<String>`

![Search Engine search](/Images/searchenginesearch.jpg)

Otherwise, any other path will return an error message, including having no path at all. All it does is call the handlerRequest method. Since the path doesn't have `add` or `search`, it doesn't iterate through any if-else statements and immediately returns an error message.
![Search Engine error](/Images/searchengineerror.jpg)







# Part 2

## Testing the Reversed method from the array class

**Failure Inducing Input**

![reversed input](/Images/reversedfailinput.png)

**Symptom**

![reversed symptom](/Images/reversedsymptom.png)

The reason why there is a bug because the programmer assigned the values of the new array to the current array rather than the other way around. Then he returns the wrong array as well. Since newArray is uninitialized, all the values in tis array are gonna be 0. Therefore, the values in the arr array are replaced with 0 and a method of arrays of 0's is returned.

![reversed wrong code](/Images/reversedwrongcode.jpg)

To fix this, you simply need to switch `newArray[arr.length-i-1]` with `arr[i]` like this. Then you `return newArray` rather than `return arr`

![reversed correct code](/Images/reversedgoodcode.jpg)

![reversed success message](/Images/reversedsuccessmessage.jpg)

## Testing the Filter method from the list class

**Failure Inducing Input**

![filter input](/Images/filtererrorfailinduceinput.png)

**Symptom**

![filter symptom](/Images/filtersymptom.png)

The reason why there is a bug in this code is because rather than append the element to the array, it prepends it. Therefore, the returned array is the reverse of what it is supposed to be.

![fixed code for filter method](/Images/filtererrorcode.jpg)

To fix this, you simply just need to remove the "0" parameter in add like this:

![fixed code for filter method](/Images/filterfixed.jpg)

![filter successful message](/Images/filtersuccessful.jpg)