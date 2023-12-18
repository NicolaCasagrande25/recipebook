# Device-Agnostic Design Course Project II - 12563757-9152-41de-aa81-953971bc4df1

Write your documentation for the project below.

### Name of the application
RecipeBook

### Brief description of the application
RecipeBook is a web application that allows users to search for recipes based on their name and category to find what they want to cook. Each recipe has a list of ingredients and instructions on how to cook it. Users can also add their own recipes to RecipeBook and edit the ones they added if they are logged in. Furthrmore, users can also add recipes to their favourites list and view them later.

### 3 key challenges faced during the project
1. Implementing the search functionality
It has been difficult to understand how the content of the page could change when the user started to input text in the search bar. The problem was solved by creating a skeleton for the page that shows its body when the search bar is empty and shows the search results when the user starts typing in the search bar.

2. Implementing the favourites functionality
Implementing the favourites mechanisms has been quite complex, since it requires to update the page when the user adds or removes a recipe from their favourites list. The problem was that the provider could not just be refreshed since that would cause a reload of all the information on the page, but just the information on whether the recipe was in the favourite list or not had to be changed.

3. Implementing the scrolling mechanism
Adding the scrolling mechanism was not easy, there were many providers in my application and the recipe list page did not know which provider it received information from. It only knew which recipes to display, for this reason it was complex to understand how to proceed.

### 3 key learning moments from working on the project
1. Having many providers makes things complex
Riverpod makes it possible to pass a parameter to the provider with the .family modifier, this gives the possibility to create many providers that work in the same way but make use of this different parameter. This was very useful, but it also makes things complex when you have to update all of these providers or to autodispose them in order to avoid having information that is not updated.

2. Initialising information in providers with information from the database 
Editing the recipe required to insert information in some providers, this information came from the database and was retrieved asynchronously. This caused problems because the providers were initialised before the information was retrieved from the database, so the information was not available when the providers were initialised. This problem was solved by passing the information to the providers from a previous page that already had the information available. This however is probably not the best solution.

3. Responsiveness 
Adapting the information to different screen sizes is not very easy, code in Flutter becomes very long and full of conditions, for this reason I opted for creating different classes for the different device sizes. This approach requires to copy paste a lot of code, which is not a good practice. However, neither having a lot of conditions in the code nor having a lot of classes which contain similar code seems to be a good solution to me.

### list of dependencies and their versions (from pubspec.yaml)
dependencies:
  flutter:
    sdk: flutter
  cupertino_icons: ^1.0.2
  http: ^1.1.0
  flutter_riverpod: ^2.4.5
  go_router: ^12.0.1
  firebase_core: ^2.22.0
  firebase_auth: ^4.1.0
  cloud_firestore: ^4.13.1
  google_fonts: ^6.1.0

dev_dependencies:
  flutter_test:
    sdk: flutter
    flutter_lints: ^2.0.0


### database structure 
/categories
id: string
name: string

/recipes
id: string
name: string
creatorId: string
description: string
categories: array of strings
likedBy: array of strings
likes: number
ingredients: array of map (name: string, quantity: number, unit: string)
steps: array of map (title: string, description: string)