# Kashyap worklog

# 08/22/2023 - first class meeting
Today, we met in class for the first time. It was an extremely important meeting because I learned about conflict management and method's of brainstorming. These are very important skills to have as a I get a group for this class and start to figure out what project I want to do. The most important takeaway from this session to remember for the rest of the semester is to always be open to ideas from other team members.

# 08/24/2023 - initial web board post
Today, I submitted my initial web board post. I read through a ton of ideas and responded to one that I thought was especially relevant. After reading through these ideas, I plan to pitch an idea that includes some sort of app development that can control some key hardware when I speak with my group.

# 08/31/2023 - project submission
My group met for the first time today and brainstormed various ideas. We are going to go with the following idea at the moment. A bookshelf that can rotate on the x-y axis to show different shelves to the user. At the moment, we do not have all the details planned out but plan to explore this idea further. Here is an initial example of an image we were looking at to figure out how to structure our bookshelf:
![Image]([http://url/a.png](https://m.media-amazon.com/images/I/61TPHUMPPIL._AC_UF894,1000_QL80_.jpg)https://m.media-amazon.com/images/I/61TPHUMPPIL._AC_UF894,1000_QL80_.jpg)

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
![Image](/Users/kash/Desktop/block.png)

# 09/13/2023 - Visual Aid
Later in the day, after the block diagram, we met up again to finish our visual aid. The visual aid basically takes the block diagram and makes it into its visual component. Here it is:
![Image](/Users/kash/Desktop/visualaid.png)

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
![Image](/Users/kash/Desktop/CAD.png)
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
![Image](/Users/kash/Desktop/routes.png)

# 09/27/2023 - Home page design
Today, I completed the home page design for the website. This page contains the buttons for the website to navigate to the various other pages as defined in the image from the last entry. Here is an image showing how the home page is setup. As can be seen, there are 4 buttons. The buttons are self explanatory except for calibrate. Calibrate is essentially used to help the ESP32 figure out whether the user is manually going to rotate the bookshelf or not.
![Image](/Users/kash/Desktop/home.png)

