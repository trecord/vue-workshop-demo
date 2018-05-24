# vue-workshop-demo

> This project is meant to be the end state of a walkthrough of how to get build an beginner web application with Vue JS that connects to an API. It makes use of Vue-cli 3 and vuetify.

## Initial Setup
### Install Vue CLI

To start off with, we'll open our terminal. You'll want to have NPM or Yarn installed. Then you'll want to install vue-cli:

``` bash
# Install .
npm install -g @vue/cli
# or
yarn global add @vue/cli
```

Once that is done you should have the newest version of Vue-cli. Check that you do by running the following:

``` bash
vue -V
```

This should return should be 3.0.0-beta.x. If it does, we're ready to start getting set up. 

### Install the project
Enter the following in your terminal: 

``` bash
vue create vvjs
```

You'll be given a set of options. You will want to "manually" select features. Make sure to add Vuex and Router. Here's the setup that we will use for our installation:

1) Manually select features
2) Vuex and Router should be selected. Press space to select them.
![Vue Setup: Installing Vue](static/images/vue_setup_1.png)
3) Config should be in package.json
![Vue Setup: Installing Vue](static/images/vue_setup_2.png)
4) "n" do not save
5) Use NPM
![Vue Setup: Installing Vue](static/images/vue_setup_4.png)


Once the initial installation is completed, you'll have a working project! You can already see something if you run the following:

``` bash
cd vvjs
npm run serve
```

Now go to in your browser. You can press control + C in your terminal to stop the process running the development instance of your site.

### Install Vuetify/Babel/Axios

Before we go any further, we're going to install a couple of dependencies to allow us to bootstrap our project a little further. The first of these is Vuetify, which will give us an interface for our project. You won't have to use Vuetify on all of your projects! But it will give us a navigation bar and some basic styling when we first load up our application. Enter the following to see your starting place:

``` bash
cd vvjs
vue add vuetify
```
1) "y" allow Vuetify to replace app.vue and helloworld.vue
2) "y" use custom theme
3) "n" use a la carte components
 "y" use babel/polyfilly
![Vue Setup: Vuetify](static/images/vue_setup_1.png)

There are two dependencies that we'll be adding to the project: Babel, and Axios. Istall them with the following commands.

``` bash
npm install --save @babel/polyfill
npm install --save axios vue-axios
```

Then open src/main.js and add the following:

``` main.js
import router from './router' // Add everything after .router:
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)
```
We'll be moving on to actually getting started on building something now!

## Getting started

Vue has a wide variety of core and add-on features, so let's start with some of the basics.

### Reading a Vue file

Right now, when we launch our app, the navigation bar defaults to being open. That's annoying! We'll want to change that.

If you open up the folder "src" in your vvjs folder you'll see an "App.vue" file, a file which serves as the root component of this application. A .vue files is broken into three sections: the template, the scripts, and the styles (App.vue only has the templates and the scripts). If you look at the template section for App.vue, you'll see that there's a component called "v-navigation-drawer" that has something called a "v-model" which is set to "drawer." If you scroll down a little to the "scripts" section, you will see that there is a set of "data" which includes "drawer"... and it is set to "true". The values in the data here are what is controlling whether the nav bar should be displayed or not!

![Vue Nav: Drawer](static/images/nav_1.png)
![Vue Data: Drawer](static/images/nav_3.png)

Let's change that set of data. Set "drawer" to false. While we're at it, let's also change the "title" to 'Vancity_Vue.js'. This is what our data now looks like:
```javascript
export default {
  name: 'App',
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [{
        icon: 'bubble_chart',
        title: 'Vancity Vue JS'
      }],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vancity_Vue.js'
    }
  }
}
```
If you reload your page, that annoying nav won't be open by default, and we'll have our new title. How did the title change? If you scroll back up to the template, you'll see a "v-toolbar-title" element that has a v-text attribute set to "title." 
![Vue Data: Drawer 2](static/images/nav_4.png)

### Data Binding and Methods

 introduces a few concepts that we'll want to go over. The first: data binding.

#### Two-way binding

#### Methods

If you looked closely at App.vue, you'd have seen there is also a button with the element name "v-toolbar-side-icon" that has an attribute called "@click.stop" that was setting the "drawer" to != "drawer".
![Vue Data: Drawer](static/images/nav_2.png)

This is what was toggling the display of the nav item.

#### Repeating data sets


### Routing
<router-link to="home">Home</router-link>

### Axios & connectivity

### Computed Properties

