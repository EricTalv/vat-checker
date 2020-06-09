# vat-checker


## Build Locally 

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```




### MVP TO:DO 

I usually start my work by setting up 
a simple MVP TO-DO List.

Later I might add stretch goals. 

```
[X] Setup Environment

[X] Simple Front-End
[X] Send succesful request to Endpoint
 [X] Return Data 
 [X] Validate Data (Meaning organize the data)

[ ] Front-end additions
 [ ] Country drop-down component
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
```
 
### Components 

To make the code re-usable and organized, I have divided
the main logic into components.

This would allow us to use the component in future applications. 

#### Vat-Identifier

This is the primary logic component that retrieves
data from the given URL.

Here we send the request to the API and return the data we get.

#### Data-Organizer 

Here we get data and organize it however we want and display the data.

#### Country-dropdown 

Here we just get all countries and put them into a drop-down 
element.
I made this into a component so I can manipulate how many
countries are added and so on.

## Errors

On google chrome if you were to send a bad request to the API link 
for example:

> 
>  RU999999
>

Chrome will always console.log an error.

[see this post](https://github.com/axios/axios/issues/1947)


