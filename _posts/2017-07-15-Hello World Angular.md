---
layout: post
title:  "HelloWorld Angular"
excerpt: "Gives you an insight of the Angular Framework and guides to create your 'HelloWorld' application via Angular.."
---

### Prerequisites:


**Setting up the Development Environment**

 - Angular requires node 6.9.x and npm 3.x.x for proper functioning.
 - Check if you have `node` and `npm` installed on your system. To do this, run the following commands in a terminal/console window.
 
 For node:
 ```
 node -v
 ```
 For npm:
 ```
 npm -v
 ```

 - Install [Node.js and npm][1] if they are not already installed on your machine. 

 - Install the [Angular CLI][2]  globally using `npm install -g @angular/cli`.


----------


### Step 1: Creating a new project ##

Open a terminal window or Node.js command prompt if you are on Windows.

We create a new project and skeleton application using the command:

    ng new my-app

Here the `ng` is for Angular.
We get a file structure something like this.

[![File Structure_1][3]][3]

[![File Structure_2][4]][4]

There are lots of files. We need not worry about all of them now.

### Step 2: Serving the application ##

We launch our application using following command:
 

    ng serve

We may use a flag `-open`( or simply `-o`) which will automatically open our browser on `http://localhost:4200/`

    ng serve --open

Navigate browser to the address `http://localhost:4200/`. It looks something like this:

[![Welcome To App][5]][5]


### Step 3: Editing our first Angular component ##

The CLI created the default Angular component for us. This is the root component and it is named `app-root`. One can find it in `./src/app/app.component.ts`.

Open the component file and change the title property from `Welcome to app!!` to `Hello World`.

Original Code : Notice the `title = 'app';`

[![Original Code][6]][6]


Modified Code : Value of `title` is changed.

[![Modified Code][7]][7]

Similarly there is a change in `./src/app/app.component.html`.

Original HTML

[![enter image description here][8]][8]

Modified HTML

[![enter image description here][9]][9]

Notice that the value of `title` from the `./src/app/app.component.ts` will be displayed. The browser reloads automatically when the changes are done. It looks something like this.

[![Hello World][10]][10]

To find more on the topic, visit this link [here][11].


  [1]: https://nodejs.org/en/download/
  [2]: https://cli.angular.io/
  [3]: https://i.stack.imgur.com/0crAT.jpg
  [4]: https://i.stack.imgur.com/zEtsK.jpg
  [5]: https://i.stack.imgur.com/Ssupw.jpg
  [6]: https://i.stack.imgur.com/fVVWw.jpg
  [7]: https://i.stack.imgur.com/ycTba.jpg
  [8]: https://i.stack.imgur.com/gwEFE.jpg
  [9]: https://i.stack.imgur.com/Sgpwj.jpg
  [10]: https://i.stack.imgur.com/4MWP9.jpg
  [11]: https://angular.io/guide/quickstart#whats-next
