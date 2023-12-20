[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/RqhuAf8n)
# Shopping List App: Vue

## Directions

For this project, you will build a single-page application using Vue.js that allows a user to keep a number of shopping lists, and to create, edit, and delete lists and list items. Shopping Lists are made up of a title, items, and the date/time most recently updated. 

The design of this app is up to you. You're welcome to reuse the design from the previous project, or you can come up with something new. You can also use [Tailwind](https://tailwindcss.com/) or another CSS framework if you'd like.

## Getting started

To get started, you will need to clone this repository and install the dependencies using `npm`.

```sh
npm install
```

This application uses [json-server](https://github.com/typicode/json-server) to provide you with an API. It uses a `db.json` file in the root of this project, which you will have to create using the sample file that is included in this repo. To copy the sample file, run the following command:

```sh
cp sample-db.json db.json
```

This application uses two different servers: one for the API, and one for the Vue application, using a build tool called Vite. To start both servers, run the following command:

```sh
npm start
```

This will start `json-server` and the Vite development server. It should open a browser window at the same time. You will need to leave this running while you are working on this application.

The URL for your web application is `http://localhost:5173`.

The URL for your shopping lists API is `http://localhost:3000/lists/`.

### Using Vue

In the main.js file, a new Vue application is created and attached to the DOM. The application's root component is currently called App and is imported from `App.vue`. In App.vue, you'll see a [Single-File Component](https://vuejs.org/guide/scaling-up/sfc.html) with tags for `script`, `template`, and `style`. You are welcome to edit this file or change it in any way you see fit. You can also create new components and import them into App.vue.

Be sure to use the Vue DevTools extension for Chrome or Firefox to inspect your Vue application.

### Using the shopping list API

To get a list of all shopping lists, make a `GET` request to `http://localhost:3000/lists/`.

To add a new list, make a `POST` request to `http://localhost:3000/lists/`. You will need to send a body and headers. Your request will look like this:

```js
fetch('http://localhost:3000/lists/', {
  method: 'POST', 
  headers: {"Content-Type": "application/json"}, 
  body: JSON.stringify({ title, items, updatedAt: new Date() })
})
.then(res => res.json())
.then(
  data => console.log(data)
  // or whatever you need to do
)
```

The `headers` attribute lets json-server know you will be sending JSON to it for it to read. The `body` attribute is the JSON you are sending. If you have an object, then you must call `JSON.stringify` with that object.

To **create a new list**, make a `POST` request to `http://localhost:3000/lists/` as shown above. Notice that you do not need to include the `id` key, since JSON server will automatically generate an id for you. You will need to include the `title` and `body` keys, and you will need to include the `updatedAt` key with the current date and time. 

You can store the date in date time string format, using the `new Date()` constructor. When you want to display the date in the UI, you can format it then using the [Date object's methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date) or, more conveniently, using a library like [Day.js](https://day.js.org/).

To **edit a list**, make a `PATCH` request to `http://localhost:3000/lists/:id` where `:id` is the id of the list. This will also require the same headers and body as the above request.

To **delete a list**, make a `DELETE` request to `http://localhost:3000/lists/:id`.

## Requirements

Your application should have the following functionality:

1. A user can see a list of their shopping lists displayed on the page, including at least the number of items on the list.
2. A user can click on a list to see all items displayed, and those purchased will appear crossed off the list (but not deleted) - and users can cross off items.
3. A user can add a new list. When they do, their list should be added to the existing list of lists without a page refresh.
4. A user can edit a list they have already created. When they do, their list (or at least list count) should be updated in the list of lists without a page refresh.
5. A user can delete an existing list. When a list is deleted, it should automatically be removed from the list of lists without a page refresh.

## 🌶️ Spicy options

- allow a user to remove items from their shopping lists (without editing the full list)
- allow users to share and/or move items between lists

