# Datatable Vue

[![Build Status](https://travis-ci.com/DanielUche/brite-core-test.svg?branch=develop)](https://travis-ci.org/joemccann/dillinger)

A challenge to implement a customizable vue.js datatable.

link https://contactlist-209a9.firebaseapp.com/


![datatable](https://github.com/DanielUche/vue-data-table/blob/develop/screenshot.png)


# Usage

From your parent component 

##### import the component

```
import Datatable from 'pathtopaginatorcomponent';
```
##### Add Datatable to your components list
DataTable
 
 ##### Add Datatable to your template
 ```
 <DataTable
  @deleteDataTableItem="deleteRecord"
  v-if="payments.length"
  :items="payments"
  keyField="ID" hasActions
  columns="columns"
  :asyncTask="asynctask"/>
 ```
 
 ### Datatable Properties

| Property | Description | Required
| ------ | ------ | ------ |
| deleteDataTableItem | A function that deletes item from the table | required if hasActions is specified
| items | A array of object to display on the table | required
| keyField | A string that identifies the key field provided list. This is used to select an item from the list and also serves as a parameter to the delete and edit methods of the datatable  | required if hasActions is specified
| asyncTask | identifies different stages of an async operation. Possible values are ``` 1. success 2. pending 3. failed ```   | required if hasActions is specified
| columns | identifies columns in your dataset | required |


#### Column Format

columns: [
        { name: 'Key', key: true, sortable: true },
        { name: 'Name', sortable: true, editable: true }],

# The Aproach
A datatable should at the minimum consist of 
  - A paginator component.
  - A table to display the data.
  - A dropdown to change number of items displayed per page.
  - A textbox to enable filtering the table.
  - Ability to export data in different formats.
  - Actionable column contaning buttons to perform an operation on items on the table.
##### Advanced features can include but not limited to:
-   Adavance and user composable filter.
-   Customizable table i.e allow user to determine table, paginator styling.

### Implementation Detail

My implimentation uses.
- A **Paginator** component to determine how many items to display per page, the paginator also handles:
  - Setting current page.
  - buttons to display per page
  - A dropdown to change number of items displayed per page.

 **NB**: The paginator component serves as the parent container for both the table and input controls for the datatabe. The paginator uses emitters and listeners internally.

- A **Table** component:
  - Present the data to the user.

  **NB**: Data is passed to the table component as props from the paginator component.

- A **Modal** component:
  - Present currently selected item to the user and allows a user to edit it.

**NB**: Data is passed to the modal component as props from the table component component.

Other Components Include:
A Pager component that sets items to display per page.
An input component to search the list.
**NB** this components are not standalone but form part of the paginator or table component.


### Development

1. Clone repo.
2. Rename .env.template to .env and provide values.
3. node src/init-db.js to initialize firestore database.

```
npm run serve
````

##### Testing
```
npm run test-unit
```

### How Long I Spent on the project ?
A week

### In what ways would you adapt your component so that it could be used in many different scenarios where a data table is required?

1. I will add ability for the users to provide custom styling for the component.
2. Add functionality for async and server side pagination.


### What CSS property did you recently learn about that helped you on a project?

animation-delay

I used this to add the page loader on the landing page.



### What is your favorite modern Javascript feature? Why?

My favourite JS library is vue.js because of its simplicity. Coming from an angular and react background vue.js proved much more easier.


### What is your favorite third-party Vue.js library? Why?

Buefy https://buefy.org/ because it provides me with a lot of components out of the box

