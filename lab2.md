CS15L Lab Report 2

To create a string server that takes in a string to add as text on the webpage. We create a similar script as that to NumberServer.java from the second lab.
We create a few conditional statements in the URLHandeler class on the StringServer.java file. The first conditional checks to make sure the path is `/add-message` which 
is what shows up at the end of the domain of a website path. Next we check to make sure the query is `?s` at which point we add the string the user writes at the end of 
the website path to a string which we return to be displayed on the website.

``
class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String str = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            System.out.println("Path: " + url.getPath());
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    str += parameters[1] + " \n";
                    return str;
                }
        }
        return "Try adding /add-message?s=<text> to the end of the webpath";
    }
}
``
Here is an example of using the website to add strings to the screen. 

We are greeted by this page before we add any queries or paths to the end of the website domain.

We add `/add-message?s=apple` to the end of the webpath and `apple` is displayed.

We change `/add-message?s=apple` to `/add-message?s=tree` the end of the webpath and 
`apple`
<br />
`tree`
<br />
is displayed.
