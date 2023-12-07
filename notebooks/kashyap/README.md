# Kashyap worklog

# 08/22/2023 - first class meeting
Today, we met in class for the first time. It was an extremely important meeting because I learned about conflict management and method's of brainstorming. These are very important skills to have as a I get a group for this class and start to figure out what project I want to do. The most important takeaway from this session to remember for the rest of the semester is to always be open to ideas from other team members.

# 08/24/2023 - initial web board post
Today, I submitted my initial web board post. I read through a ton of ideas and responded to one that I thought was especially relevant. After reading through these ideas, I plan to pitch an idea that includes some sort of app development that can control some key hardware when I speak with my group.

# 08/31/2023 - project submission
My group met for the first time today and brainstormed various ideas. We are going to go with the following idea at the moment. A bookshelf that can rotate on the x-y axis to show different shelves to the user. At the moment, we do not have all the details planned out but plan to explore this idea further. Here is an initial example of an image we were looking at to figure out how to structure our bookshelf:
![Image](https://m.media-amazon.com/images/I/61TPHUMPPIL._AC_UF894,1000_QL80_.jpg)

# 09/01/2023 - Project brainstorming
We have added to our original idea with the following components:
1. We will have an app to control the bookshelf's movements. This will most likely be an IPhone app
2. We are thinking of adding insertion detection. This would be include something like a photoresistor or QR code to notify the app when an item has been inserted.
3. We will be using a motor to rotate the bookshelf on the app's command.
4. We will be using a wall outlet to power our bookshelf

# 09/05/2023 - Dividing up work
We have decided the following breakup of the work for the project based on the skills and strengths of the group:
1. Kashyap will work on the software end of things. This includes the connection of the app to the ESP32
2. Vraj will work on PCB design and motor control
3. Atharv will assist with the PCB design and will also be in charge of the mechanical design and anything related to the bookshelf itself.

# 09/12/2023 - Team meeting with Nikhil
Today, we met with our TA for the first time. In this meeting, we were able to solidify the types of hardare to use, listed below, and confirm that our idea is plausible. Here are important notes from the meeting:
1. We will be using an ESP32 with wifi/bluetooth capabilities in order to connect the bookshelf hardare to the app.
2. We will be getting power from an outlet
3. We will use a stepper motor in order to maintain how much to spin by to get to different shelves
I also learned what an H-Bridge is. It is basically a controller to help a stepper motor take "steps" when turning.
Here is an image of the type of motor we will use:
![Image](https://a.pololu-files.com/picture/0J5063.1200.jpg?da4f96943763edca37a753be15b56798)

# 09/13/2023 - Block Diagram finalized
Today, we completed our block diagram. The diagram contains all of our components and how they will be connected to each other. Here it is:
![Image](/block.png)

# 09/13/2023 - Visual Aid
Later in the day, after the block diagram, we met up again to finish our visual aid. The visual aid basically takes the block diagram and makes it into its visual component. Here it is:
![Image](/visualaid.png)

# 09/14/2023 - Proposal work
We met up today to work through our project proposal. Here are key details from this proposal:
1. The bookshelf will be 4 feet tall and around 2 feet wide and will have a cylindrical shape
2. Each shelf will have 4 more vertical shelves to allow for maximum storage space
3. We will be using a QR code to identify what shelf the user will input items. The user will scan the code using their phone camera

# 09/15/2023 - Machine Shop conversation
We met with the machine shop today. Here are the biggest updates
1. We are scaling the size of the bookshelf down a ton. It will now be around 8 inches tall and 8 inches wide, and there will only be one vertical shelf per side
2. The machine shop gave us a stepper motor that we could use in our design
3. There will be a control box underneath the bookshelf that will contain the PCB, LED, and motor
We are now going to work on the CAD design

# 09/16/2023 - CAD Design
Here is the CAD design that we developed based on the conversation with the machine shop:
![Image](/CAD.png)
As it can be seen, the CAD design is extremely simplified. It follows exactly what the machine shop recommended that we do.

# 09/18/2023 - Team meeting with Nikhil
We went over some key design choices with Nikhil. Here are my notes for the software portion:
1. Use an already made package to develop the app
2. Conencting the app to the bookshelf shouldn't be too difficult as there are packages for that as well
3. Use the Arduino IDE to figure out how to control the motor and LEDs
4. We will now be using a shelfID instead of a QR code to identify shelves. The user can basically insert this shelfID into the app when inserting an item
Right now, I'm thinking of using Apple Homekit to develop the app as it would simplify the project a ton from an app perspective. I have not figured out how to establish the connection between the app and the ESP32 yet though.

# 09/20/2023 - App Design Change
After attempting to create an IPhone app, I've realized that IOS is extremely difficult to develop apps in. As a result, I have decided to change the phone app to a web app. I have experience in web design so I plan to use ReactJS to develop this application. I have referring to the following link to figure out how to approach this problem:
[Link](https://react.dev/learn)

# 09/23/2023 - Backend Development
After a ton of research, I have figured out how to connect the app to the ESP32. The control process is as follows:
1. When retrieving an item, find which shelf that item is located in
2. Using Express, send that shelfID to a backend server using an HTTP Post Request. Server is created using Render
3. On the ArduinoIDE side, send an HTTP Get request to the same server at polling periods to retrieve the next shelfID
4. Use that shelfID to rotate the bookshelf
Websites I referred to for help:
[Link](https://render.com/)
[Link](https://expressjs.com/)
[Link](https://forum.arduino.cc/t/easy-way-to-https-get/1006294)

# 09/25/2023 - Beginning the web design
Today, I began working on the web application. I started off slow, but today all I completed was setting up the routes between different web pages. The web pages include help for insertion, retrieval, and checking storage
Here is a snippet of code to illustrate how the web pages are connected:
![Image](/routes.png)

# 09/27/2023 - Home page design
Today, I completed the home page design for the website. This page contains the buttons for the website to navigate to the various other pages as defined in the image from the last entry. Here is an image showing how the home page is setup. As can be seen, there are 4 buttons. The buttons are self explanatory except for calibrate. Calibrate is essentially used to help the ESP32 figure out whether the user is manually going to rotate the bookshelf or not
![Image](/home.png)

# 09/29/2023 - Insert page design
The insert page is complete and works as such:
1. The user clicks insert on the homepage
2. The user enters the shelfID of the shelf that they want to insert intoo
3. The user enters the name of the item they want to insert
Here is an image of the React Code that illustrated the process
![Image](/insert.png)

# 10/01/2023 - Insert Success page design
I realized that there was an important piece missing in the app so I added the following functionality. When a user enters an item, I follow up with a page that lets the user know that their item was successfully inserted. Without this, I figured there would be confusion on the users end on whether or not their item was inserted. Here is a snippet of the code used to do this:
![Image](/insertSuccess.png)

# 10/03/2023 - Invalid shelfID
There was another part of the code I was missing. When the user enters a shelfID, there has to be a check to see whether or not that shelfID was actually correct. So, I added a snippet of code in that checks the validity of the code first, then allows them to insert an item. Here is the snippet of code that illustrates this:
![Image](/invalidID.png)

# 10/05/2023 - Check Storage
I added in the component that allows users to check the storage of the bookshelf. Basically, when the user adds an item, the item name is added to a storage unit within the frontend framework. Then, on the storage page, this information is printed from the storage unit. This will be updated everytime there is something inserted. Here is the snippet of code that illustrates this:
![Image](/checkStorage.png)

# 10/07/2023 - Shelf Storage
I now added the page that actually prints the individual shelf items. Now, when the user goes to check current storage, they will see 4 buttons for shelves 1 to 4. When the user selects a shelf, they will only see the items located in that shelf. I thought this would be much simpler for the user to figure out where to retrieve an item from. Here is the snippet of code that does exactly that:
![Image](/shelf1Storage.png)

# 10/10/2023 - Retrieval
Now, I added the page to allow the user to retrieve an item. Although I haven't written this code completely yet, the function is as follows:
1. On this webpage, the user will enter the name of the item they want to retrieve
2. The app will search for this item within its storage unit and tell the user whether or not the item was found.
Here is a snippet of code that shows the current functionality:
![Image](/retrieve.png)

# 10/13/2023 - Finding the item using retrieve
I finally finished the code for finding an item within the bookshelf. Originally, I wasn't sure how to locate the item, but I came up with the following algorithm to avoid any issues with searching for the item:
1. There is a for loop that basically searched for the first occurrence of the item within the storage unit
2. Once the item is found, the for loop breaks and returns the shelf ID of the shelf that the item is located in
3. If the item is not found, the user sees a retrieval unsuccessful page.
Here is the snippet of code that handles finding the item in the storage unit:
![Image](/findItem.png)

# 10/15/2023 - Backend server created
I created the backend server using a website called Render. Render allows users to publish their server to the public so that the server can be accessed from different devices over various servers. This server connects to the app and allows the app to send HTTP Post requests to the server and HTTP Get requests from the ArduinoIDE. I have not implemented the REST API calls yet, but plan to do so in the future. Here is an image of the website Render for my application:
![Image](/render.png)

# 10/20/2023 - Backend created
I created the backend today using ExpressJS. I was debating between a couple different platforms to host the backend, but decided that Express had all the functonal requirements that I need to get the backend setup. The code is relatively simple and works as follows:
1. Establish that we are using Express
2. Connect to the backend server
3. Send the data to the server using a POST request
![Image](/expressDev.png)

# 10/25/2023 - HTTP Call
I updated the code today to include the HTTP Post request on the frontend side. The idea behind this is as follows:
1. When the user retrieves an item, the shelf ID of the shelf that the item is stored in is stored in a variable
2. That variable is then sent in an HTTP Post request to the backend server on Render
3. The shelf ID is essentially resent everytime the user retrieves a new item.
Here is an image of the code that send the POST request:
![Image](/httpCall.png)

# 10/30/2023 - Wifi connection on ESP32
I finished working on getting the ESP32 dev board to connect to my hotspot. I had not known how to connect the ESP32 to hotspot, but did a lot of research and it turned out to be simpler than I had previously predicted. The code basically starts up a wifi connection, checks if it works by connecting using the correct wifi name and password, and lets the user know if the device has been connected. The code is relatively simple right now, but will be used in the future to receive shelf IDs. Here is a snippet of code that establishes the connection:
![Image](/wifiConnection.png)

# 11/08/2023 - Motor control complete on ESP32
The code to spin the motor has been completed. Although this code doesn't work on the actual motor itself, having the basic design done already will help streamline the process in the future. This code basically takes in the new shelf id and the old shelf id, compares them, and figures out how much to spin the motor by. For example, if the old shelf ID is 1 and the new shelf ID is 3, the motor will spin by 180 degrees. Here is the snippet of code to illustrate that algorithm:
![Image](/motorControl.png)

# 11/11/2023 - Homepage and Insert Page CSS
I finished making the homepage and insert page look pretty. As a part of the frontend code, I added in a ton of CSS code in order to make the app look nice. Previously, it was the bare bones JS code, which looked extremely ugly and unappealing. I researched a ton of CSS through the following link: [Link](https://www.w3schools.com/css/) and then applied it to the app. Here is what the insert and homepage look like now:
![Image](/homeOnApp.png)
![Image](/insertOnApp.png)

# 11/13/2023 - Retrieve and Strorage on App
Similarly to the previous entry, I have now finished the CSS for the retrieval and storage pages. I followed the same color scheme and button design so this part did not take as long as the previous pages did. Here is what they look like now:
![Image](/retrievalOnApp.png)
![Image](/storageOnApp.png)

# 11/15/2023 - Breadboard integration
Now that the app and arduino code is completely done, I'm moving on to helping with integrating this code onto the breadboard. Vraj and Atharv built an H-bridge on the breadboard and we are trying to hook up the app to control the motor. The H-Bridge isn't really working so we plan to debug this in the coming days. Here is a schematic of the H-Bridge circuit that we are basing our circuit off of:
![Image](https://www.build-electronic-circuits.com/wp-content/uploads/2018/11/H-bridge.png)

# 11/17/2023 - Breadboard H-Bridge IC
Breadboarding the H-Bridge by hand was not working out. As a result, we replaced the H-bridge with an IC that can essentially do the same thing. The motor can now spin even though we don't have full control over it. This is extremely important as we can now move forward past issues that aren't even important. The plan is to get full control over the motor now on the hardware side.

# 11/21/2023 - Breadboard almost working
The PCB soldering doesn't seem to be going well, but we are moving in a good direction with the breadboard. We can now rotate the bookshelf, although by incorrect amounts, based on the shelfID and then light up the LED to follow our high level requirements. We are trying to debug this issue and figure out why the motor doesn't spin properly but it seems to just be an issue of the poor motor. The plan is to have this working by the end of the week as our demo is next Wednesday.

# 11/24/2023 - Breadboard working
Today marks an extremely important accomplishment. The bookshelf now completely works with the breadboard. We are able to do the following with our design:
1. Insert items into the bookshelf based on the shelf ID
2. Retrieval of items spins the bookshelf to the correct location
3. LED lights up after the bookshelf stops rotating
4. Storage on the app correctly displays contents of the bookshelf
5. Calibrate button puts bookshelf into free rotate mode, which allows user to calibrate device.

# 11/29/2023 - PCB does not work
After a ton of work put into soldering the PCB, it simply would not work for our demo. The ESP32 kept breaking or something else on the circuit would not work. As a result, our demo only used the breadboard. Luckily, during our demo, everything worked perfectly, just without a PCB. We are being given a second chance to complete the PCB by the final presentation date and get the points back, so we will be sure to work on that in the coming days.

# 12/04/2023 - Project Complete
After a long semester, the project is complete. We didn't get it to work on the PCB, but it is fully functional on the breadboard. We had a glimpse of hope when the PCB was fully functional, but the power regulator blew up and the PCB didn't work anymore. Overall, it was a successful semester
