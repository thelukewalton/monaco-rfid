# Phase 1: Built to take live RFID data and display these times in a table

# Build the docker image

docker build -t my-node-app .

# Run the docker image

docker-compose up

# Run the frontend - just in React/typescript

- cd frontend
- npm start

# Info

Cors is enabled by default on the server
TODO

- connect to RFID APIs
- TODO: call POST API after each lap

### Setting up the RFID reader

1. Connect to the same network as it. I was able to simply connect the ethernet cable into my laptop but you may need to use the wifi dongle.
2. Ensure it is set up in the web ui -

   - Log into https://169.254.39.234/index.html with the credentials in server.js. I had to do this in Safari; other browsers did not work. Good luck.
   - Navigate to Communication -> Zebra IOT Connector -> Configuration
   - Select the local config
   - Change the URL to be the ipv4 of your machine, and set the port to either 3000 for local node or 13000 for docker
   - Save
   - Navigate to Communication -> Zebra IOT Connector -> Connection
   - Select connect. This will take a minute

Once the connection is ready, you can connect the server side to it. If you ever want to change any of these settings (IP address, port etc), you need to Disconnect from the connection screen, wait, and then edit the connection settings as above.

3. Start the server. Send a GET request to /start to start the connection to the RFID reader.
