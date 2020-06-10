# vat-checker


## Build Locally 

```bash
# Clone repo
$ git clone https://github.com/EricTalv/vat-checker.git

# Install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

```


-------

# Documentation 

This is a VAT-ID Identification application using ERPLY's API's.

Underneath you'll find all my documentation regarding the app.

## MVP TO:DO 

Here is my MVP Todo list: 

```
[X] Setup Environment

[X] Simple Front-End
[X] Send succesful request to Endpoint
 [X] Return Data 
 [X] Validate Data (Meaning organize the data)

[X] Front-end additions
 [X] Country drop-down component
 [X] Loading animation

[X] Simple animations

[X] Components
    [X] Vat-Identifier
        [X] Retrieve data
        [X] Add data to prop
    [X] Data-Organizer
        [X] Retrieve Data
        [X] Organize Data
        [X] Display Data
    [X] Country drop-down component
        [X] Create a country Array 
        [X] Display countries in drop-down menu
        [X] Make country value Short
    [X] Vat Compiler

[X] Error Handeling
[X] Documentation

[X] Fix CSS bugs

-Stretch Goals

[ ] Turn into PWA
[ ] Write some Tests 
[ ] Add External Country-list source

```
 
## Components Architecture

To make the code re-usable and organized, I have divided
the main logic into components.

This would allow us to use the component in future applications. 

#### Vat-Compiler

To pass data between components I need a Parent component to
pass on certain data pieceses.

Vat-Compiler acts as the middle-man between the Vat-identifier and Data Organizer.

#### Vat-Identifier

This is the primary logic component that retrieves
data from the given URL.

Here I send the request to the API and return the data I get.

#### Data-Organizer 

Here I get data and organize it however I want and display the data.

#### Country-dropdown 

Here I create my custon country-dropdown component.

I made this into a component so I can manipulate set the countries
I need and additionally separate countryCode from countryName

I didn't know how many countries would be needed for this project,
Ideally I would have a *country-data file* and serve that to this
component. 

## Errors

On google chrome if you were to send a bad request to the API link 
for example:

> 
>  RU999999
>

Chrome will always show an error in the console.

[see this post for more information](https://github.com/axios/axios/issues/1947)


