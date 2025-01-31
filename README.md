# Ember-Blog

## ci-ember-demo

[![Build status](https://ci.appveyor.com/api/projects/status/wu9m922q4hu8231x/branch/master?svg=true)](https://ci.appveyor.com/project/shijiezhou1/ember-blog/branch/master) [![CircleCI](https://circleci.com/gh/shijiezhou1/ember-blog.svg?style=svg)](https://circleci.com/gh/shijiezhou1/ember-blog) [![Maintainability](https://api.codeclimate.com/v1/badges/d56d8c23aacdead09f5d/maintainability)](https://codeclimate.com/github/shijiezhou1/Ember-Blog/maintainability) [![Test Coverage](https://api.codeclimate.com/v1/badges/d56d8c23aacdead09f5d/test_coverage)](https://codeclimate.com/github/shijiezhou1/Ember-Blog/test_coverage) [![Build Status](https://travis-ci.com/shijiezhou1/Ember-Blog.svg?branch=master)](https://travis-ci.com/shijiezhou1/Ember-Blog) [![License](https://img.shields.io/github/license/shijiezhou1/Ember-Blog.svg?style=flat)](https://github.com/shijiezhou1/Ember-Blog/blob/master/LICENSE.md) [![Coverage Status](https://coveralls.io/repos/github/shijiezhou1/Ember-Blog/badge.svg?branch=master)](https://coveralls.io/github/shijiezhou1/Ember-Blog?branch=master)

demo: https://bloging.netlify.com/
or: https://shijiezhou1.github.io/Ember-Blog/

**TL;DR;**

This README outlines the details of collaborating on this Ember application.
A short introduction of this app could easily go here.

## Prerequisites

You will need the following things properly installed on your computer.

- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/) (with npm)
- [Ember CLI](https://ember-cli.com/)
- [Google Chrome](https://google.com/chrome/)
- [Docker](https://www.docker.com/)

## Installation

- `git clone <repository-url>` this repository
- `cd ember-blog`
- `npm install`

notes - docker :

- `docker pull danlynn/ember-cli`

## Running / Development

- `ember serve`
- Visit your app at [http://localhost:4200](http://localhost:4200).
- Visit your tests at [http://localhost:4200/tests](http://localhost:4200/tests).

### Code Generators

Make use of the many generators for code, try `ember help generate` for more details

### Running Tests

- `ember test`
- `ember test --server`

### Linting

- `npm run lint:hbs`
- `npm run lint:js`
- `npm run lint:js -- --fix`

### Building

- `ember build` (development)
- `ember build --environment production` (production)

### Deploying

Specify what it takes to deploy your app.

## Further Reading / Useful Links

- [emberjs](https://emberjs.com/)
- [ember-cli](https://ember-cli.com/)
- Development Browser Extensions
  - [ember inspector for chrome](https://chrome.google.com/webstore/detail/ember-inspector/bmdblncegkenkacieihfhpjfppoconhi)
  - [ember inspector for firefox](https://addons.mozilla.org/en-US/firefox/addon/ember-inspector/)

## Ember Component Life Cycles

```javascript 1.8
Touch
touchStart()
touchMove()
touchEnd()
touchCancel()
Keyboard
events

keyDown()
keyUp()
keyPress()
Mouse
events

mouseDown()
mouseUp()
contextMenu()
click()
doubleClick()
mouseMove()
focusIn()
focusOut()
mouseEnter()
mouseLeave()
Form
submit()
change()
focusIn()
focusOut()
input()
HTML5
drag
and
drop
dragStart()
drag()
dragEnter()
dragLeave()
dragOver()
dragEnd()
drop()
```

```javascript
import Component from "@ember/component"

export default Component.extend({
  // on initial Render

  init() {
    this._super(...arguments)
  },

  didUpdateAttrs() {
    this._super(...arguments)
  },

  willRender() {},

  didInsertElement() {},

  didRender() {},

  // ON Re-render

  didUpdateAttrs() {},

  didReceiveAttrs() {},

  willUpdate() {},

  willRender() {},

  didUpdate() {},

  didRender() {},

  // On Component Destory

  willDestroyElement() {},

  willClearRender() {},

  didDestoryElement() {},

  actions: {
    required(event) {},
  },
})
```

## Controller Lifecycle hook

```javascript
import Ember from 'ember';

// Ember 1.10

export default Ember.Route.extend({

    //---fire in order on route enter---

    beforeModel(transition) {
    //empty by default
    //Primarily for redirecting before the model is fetched
    },

    model(params, transition) {
    //empty by default
    // fetch the model from server here
    // return a model
    },

    afterModel(model, transition) {
    //empty by default
    //accepts model for optional model setup
    },

    serialize(model, params) {
    //has default behavior that serializes parameter out of passed model
    //works perfectly if naming scheme is followed. More on this later.
    //override to implement custom behavior
    return {paramName: paramValue};
    }

    redirect(model, transition) {
    //empty by default
    // almost identical to afterModel
    //but route is now considered active
    },

    activate() {
    // empty by default
    // used for optional setup after all model hooks
    },

    setupController(controller, model) {
    //default implmentation sets model as property on controller
    //must keep default behavior an optionally do more controller setup

    controller.set('model', model);
    },

    renderTemplate(controller, model) {
    //default implementation renders the template with the same name as the route
    //with the default controller
    // template name is passed as string
    // override the function to customize which template and controller
    // or to render mutiple templates

    this.render(this.routeName, {
    into: 'applcation',
    controller: controller,
    model: model
    });

},

//----on route exit----

resetController(controller, isExiting, transition) {
//empty by default
//fires when route changes or model is refreshed
// isExiting property true when exiting (obviously)
},

deactivate() {
//empty by default
//fires on route exit
}

});

export default Controller.extends({

  appName: '',

  actions: {
    yourmethod() {

    }
  }

})
```

## Route Lifecylce hook

```javascript
import Ember from 'ember'; // Ember 1.10
export default Ember.Route.extend({ //---fire in order on route enter---
    beforeModel(transition) {
      //empty by default
      //Primarily for redirecting before the model is fetched
    },
    model(params,transition) {
      //empty by default
      // fetch the model from server here
      // return a model
    },
    afterModel(model, transition) {
      //empty by default
      //accepts model for optional model setup
    },
    serialize(model, params) {
      //has default behavior that serializes parameter out of passed model
      //works perfectly if naming scheme is followed. More on this later.
      //override to implement custom behavior
      return {paramName: paramValue};
    }
    redirect(model, transition) {
      //empty by default
      //almost identical to afterModel
      //but route is now considered active
    },
    activate() {
      // empty by default
      // used for optional setup after all model hooks
    },
    setupController(controller, model) {
      //default implmentation sets model as property on controller
      //must keep default behavior an optionally do more controller setup
      controller.set('model',model);
    },
    renderTemplate(controller, model) {
      //default implementation renders the template with the same name as the route
      //with the default controller
      // template name is passed as string
      // override the function to customize which template and controller
      // or to render mutiple templates
      this.render(this.routeName, {
        into: 'applcation',
        controller:controller,
        model: model
      });
    }, //----on route exit----
    resetController(controller, isExiting, transition) {
      //empty by default
      //fires when route changes or model is refreshed
      // isExiting property true when exiting (obviously)
    },
    deactivate() {
      //empty by default
      //fires on route exit
    }

    });
```
