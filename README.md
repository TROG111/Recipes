# Recipes
LUA application for DU which displays recipes and ingredients.  Requires 11 databanks, 3 screens (recommend m size), 3 Programme Boards.

This LUA suite of applications provides a list of all DU recipes, displays their details and a list of their required ingredients.  For each ingredient, the application displays the number of items required and (if you have a databank containing your container/stores information) the quantity of the relevant stock you have in store.  Recipes can be filtered by All / Elements / Condumables / Parts.  Clicking on an ingredient for a recipe will display the details of that ingredient in the 2nd screen, along with a list of its ingredients (requirement number and stock).  A third screen displays the total ore quantities (for each ore type) needed to manufacture the recipe selected and an estimate cost (this is based on manual entry of the current market prices for each ore).

# Installation:
(it is very important that you link all databanks in the correct order for each PB, therefor I suggest arranging the databanks in the following order: a group of 8 databanks - the database, a single databank - the menu databank, another single databank - the comms databank, a final databank - the stores databank)

1) The first Programming Board will be used to upload the database.  Link this PB (in the following order) to the 8 database databank, then to the menu databank.

2) Copy the content of the Database.txt file in this repository and (using the rightclick/advanced/Paste Lua Code in game option for the PB) paste the content of the file into the first PB.  Due to limitation in DU the code in this PB is not saved when you log out - but dont worry, we will only use this PB once during the database setup.

3) Execute the code on this PB - it will take a minute or so to run completely (at the end it will list the databank and database IDs linked to the PB for you reference)

4) Now we need to link the databank to the second PB, in the following order: the 8 database databanks, followed by the menu databank and finally the comms datbank.  This PB acts as a 'server' for queries from the display PB.

5) Next copy the content of the Server.txt file in this repository (again using the LUA Paste Cope in game function) into the second PB.

6) Finally, we need to link the screens and databanks to the third PB, in the following order: menu databank, screen 1, 2, 3, the stores databank, the cooms databank

7) Then copy the content of the Client.txt file in this repository (again using the LUA Paste Cope in game function) into the third PB.

# Running the Application

The UI should be relatively straight forward.

1) Filter the content of the recipe list using the 4 buttons below the list (All/Elements/Consumable/Parts)

2) Scroll up/down through the list of recipes using the arrow buttons below the list.

3) Click on a specific recipe in the list displayed to select it - the recipe details will then be displayed (including the ore costs on the third screen)

4) Click on a specific ingredient from the list of ingredients (to the right of the recipe list) to select it and display its details on the second screen.

# Integrating with a stores monitor application

In the installation above we used a 'dummy' stores databank.  If you already have a LUA application that populates a databank with information about your factory stores, then this can be integrated with this recipe application.  Doing so will provide additional information for ingredient - the quantity of that ingredient you have in stores.

To integrate:

1) replace the stores databank with you own stores databank

2) edit the LUA code in the UI PB. Access the unit.start code (with the first line: 'stringMap={}').  Scroll down though this LUA code until you reach the section containing 'storeMap'.  'storeMap' is a mapping between the internal names that the recipe application uses and the content of your stores databank.  For example the line:

storeMap["Bsc RobA S"]="sbroboticarm"

maps the 'Basic Robotic Arm S' recipe in the application with a variable in my stores databank called "sbroboticarm".

# Good Luck




