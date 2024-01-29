# **Lab Report 2**

## Part 1

```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    String messages = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("&");

            String[] temp1 = parameters[0].split("=");
            String[] temp2 = parameters[1].split("=");

            String message = temp1[1];
            String user = temp2[1];

            messages += String.format("%s: %s" + "\n", user, message);
            return messages;
            }
        return messages;
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
