## Blog JSON-Server

A json-server for a react-native blog program for the storage of persistent data.

---

## Initial Setup

1. Navigate to the folder in your terminal that you want the new file in then run the following commands to navigate into the folder and initialize the npm package lock files:

```
$ mkdir file_name
$ cd file_name
$ npm init
```

_At this point it will ask you a series of setup questions, it will setup whether you answer them or not so it is up to you._

2. Run the following commands to bring in the files necessary for it to run and open in vscode:

```
$ npm install json-server ngrok
$ code .
```

_"$ code ." is optional and used to open that location in vscode_

3. In your editor create a file named db.json, in it initialize the object structure you want for your database:

```json
{
    "object": [
        "inner_object",
        "more_inner_objects
    ]
}
```

_This is only an example and not meant to be literal_

4. In the file named package.json find the object named "scripts" and edit it to show the following:

```json
"scripts": {
    "db": "json-server -w db.json",
    "tunnel": "ngrok http 3000"
  }
```

_3000 is the default port to use for json-server_

5. To test the database at this point run the following command:

```
$ npm run db
```

6. If you get an error at this point it is probably a port conflict, check that nothing else is running on localhost:3000 OR modify the package.json file as follows to update the port your server runs on:

```json
"scripts": {
    "db": "json-server -w db.json -p 3001",
    "tunnel": "ngrok http 3001"
  }
```

_The change does not have to be 3001, just whatever number you want to use. Both the "db" and "tunnel" must have matching numbers though._

7. To make use of the server... In another terminal run the following command to make it accessible from a mobile device:

```
$ npm run tunnel
```

_Tunnel will have to be reinitialized after the session expires and a new forwarding address will be created, update your app appropriately_

8. It will bring up up the following information, the Forwarding address is the one you need to access the locally stored database:

```
Session Status      online
Session Expires     1 hour, 57 minutes
Version             2.3.38
Region              United States (us)
Web Interface       http://127.0.0.1:4040
Forwarding          http://d5dbd87cc0.ngrok.io -> http://localhost:3000
Forwarding          https://d5dbd87cc0.ngrok.io -> http://localhost:3000
```
