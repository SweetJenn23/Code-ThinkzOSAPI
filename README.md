# Building your own website with Node-Red

We have created a website which you can use to create a simple website for your own company. In this exercise,
you will learn how it is built and how you can change the layout. 

The sample you will start off with was made for our company idea, ReutiliZe. The website looks like this. ![ReutilizeWebsite](img/website.png)

In the image above, make note of the following:

* On the top horizontal bar, you will find the name and logo of our company.
* Below on the main site there are 3 sections.
  * Column 1: vertical menu buttons
  * Column 2: input form
  * Column 3: A search form with the output screen.

We are providing you with step-by-step directions to create this website for your. Just follow the actions
below.

## Create a Node-Red service on IBM Cloud
Watch the video installing Node-red and follow the steps yourself.

You will end with a Node-Red
instance which looks like this. If
you look at the screen you will
see the building blocks, called
“nodes” on the left side. In the
middle you have the area where
you can drag and drop your
building blocks to and connect
them together. Feel free to play
around a bit. You can delete a
Node by hitting the “delete”
button after selecting it.


**2 - Install additional Nodes**
Open the hamburger menu on the upper right
corner(1). This opens a menu like this.
Choose the option “manage palette” (2).
`
The “M anage Palette ”opens a screen where you can
find all the Nodes which are installed, and an option to
search and install additional Nodes.

3 - Select the “install” tab and in the search field
type the word “dashboard”. This gives you all the
nodes and node collections for the Dashboard
usage.
Select the one called “ **Node-Red-Dashboard”**
and hit install.


Now some additional Nodes are being installed. This may take up to one minute.
Please note that in some occasions a red error will occur saying that the installation
has failed. You need to try again until you get a large green message that the
installation was successful. This is a bug which can happen sometimes depending on
your location.

4 - Close the field and return to the main screen. Inspect the left side
of the screen and look for the nodes installed under “ **dashboard** ”.

The Dashboard Nodes are being used to build a Graphical screen
which you can use to interact. This will be our website. I have
created the example website for you which uses these Nodes.
```
## 1

## 2


```
The next step is to import the example website so you do not have to build it
yourself from scratch... lets go.
```
```
Import an existing flow
Open the file website.txt. The file is provided in the Github repository
```
```
You can open it with any text editor installed on
your computer. When opening it, it will look
most probably weird and not understandable.
don’t worry. This is why we use Node-Red, so
we don’t need to understand the coding
language.
```
5 - Please open the file an select all the text
(pressing ctrl +a) and then copy (ctrl + c).

6 - R to your Node-Red environment and select the hamburger menu on the upper right
corner. This opens the menu we already used.
7 - Select “ **Import** ”.
This opens a screen where you can “paste” the code from the website.txt.

```
Paste the code with ctrl + v. Now you will
see the code appearing in the pink colored
middle section.
```
8 - Press “ **Import** ”.

```
If you look at your Node-Red screen you will see that a new tab has appeared on the
top. You can click on it and this will open a new page with nodes already connected.
```

9 - Press the **“deploy”** button to save and activate the flow.

```
The Nodes are used to build the website which I have showed at the beginning. The
white blocks are text fields to explain what the nodes below do. Take a moment to
see how it is related to the website.
```
```
Tip: In order to see the webpage you need the same internet address as used for
your Node-Red environment BUT instead of having the / red/ at the end use / ui/.
UI means User Interface. The URL should look something like this:
```
```
Node-Red environment- https://node-red-xxxxxxxx.mybluemix.net/red/
Node-Red website- https://node-red-xxxxxxxxx.mybluemix.net/ui/
```
```
Changing the website
It is now easy to change the website look and name by double clinking on the nodes
and change the codes.
```
10 - Click on the right side on the small thick line which you can drag to the left and open
an option menu(1).

11 - O the third button with the little bar Graph you
will see the options for the website(2).

12 - Select the “edit” button and change the name to
your company

13 - look at the tab called “ **Theme** ” and change the
colors of the website.

## 1

## 2

## 3

## 4


**Bonus**
If you look at the Nodes there is a Node
called”template”. If you click on the node
you will see coding which controls the little
logo of the website and the background picture. You can change the website URL to
anything else as long as it is pointing to a picture on the internet.

In my case the links will direct to the logo image and background image. Try to click
on the link and you will see:
https://github.com/jorismertens/Node-Red_API_Dashboard/blob/master/images/Reutilize_logo.png?raw=true

https://github.com/jorismertens/Node-Red_API_Dashboard/blob/master/images/wallpaper.jpg?raw=true

Now try to change URL address to a different picture. For example another
background image.

**Tip: Do not forget to close and deploy the Node-Red flow after every change!**


