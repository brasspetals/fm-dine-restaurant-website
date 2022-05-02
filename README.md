# Frontend Mentor - Dine Website Challenge Solution

![Design preview for the Dine Website coding challenge](./preview.jpg)

This is a solution to the [Dine Website Challenge challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/dine-restaurant-website-yAt7Vvxt7). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The Challenge](#the-challenge)
  - [Links](#links)
- [My Process](#my-process)
  - [Built With](#built-with)
  - [What I Learned](#what-i-learned)
  - [Useful Resources](#useful-resources)

## Overview

### The Challenge

Users should be able to:

- View the optimal layout for each page depending on their device's screen size
- See hover states for all interactive elements throughout the site
- See the correct content for the Family Gatherings, Special Events, and Social Events section when the user clicks each tab
- Receive an error message when the booking form is submitted if:
  - The `Name` or `Email Address` fields are empty should show "This field is required"
  - The `Email Address` is not formatted correctly should show "Please use a valid email address"
  - Any of the `Pick a date` or `Pick a time` fields are empty should show "This field is incomplete"

### Links

- Solution URL: [https://www.frontendmentor.io/solutions/dine-restaurant-site-svelte-parallax-effect-Ska7Z5Or9](https://www.frontendmentor.io/solutions/dine-restaurant-site-svelte-parallax-effect-Ska7Z5Or9)
- Live Site URL: [https://fm-dine-restaurant-website.vercel.app/](https://fm-dine-restaurant-website.vercel.app/)

## My Process

### Built With

- [Svelte.js](https://svelte.dev/) 
- [svelte-routing](https://github.com/EmilTholin/svelte-routing)

### What I Learned

#### **Parallax Effect with Svelte Window Bindings:**
I really wanted to use a parallax effect on this project given the "layered" images throughout the design. In order to achieve this, I used [Svelte window bindings](https://svelte.dev/tutorial/svelte-window-bindings), which allowed me to get the user's scroll position. With that I was able to use inline styling to add a `transform` on the parallax items, which include some calculations to set the position (-`y` + some value) as well as the "speed" (the number the `y` calculation is divided by).

```html
<svelte:window bind:scrollY={y}/>

<img style="transform: translate(0,{(-y + 850) / 15}px)">
```

In order to account for both `prefers-reduced-motion` and to also adjust the parallax effect on different screens, I heavily abused [Svelte else-if blocks](https://svelte.dev/tutorial/else-if-blocks) in conjunction with `svelte:window` bindings - this time to keep track of the `innerWidth`. 

```html
<svelte:window bind:innerWidth={width}/>

<!-- no parallax effect for prefers-reduced-motion and mobile screens -->
{#if $reducedMotion || width < 600}
  <img src="default.png">
<!-- parallax for tablet layout (600px-1050px) -->
{:else if width < 1050}
   <img style="transform: translate(0,{(-y + 850) / 15}px)" alt="parallax for tablet layout">
<!-- parallax for desktop layout (1050px+) -->
{:else}
  <img style="transform: translate(0,{(-y + 700) / 9}px)">
{/if}
```

Since I needed to check for `prefers-reduced-motion` across multiple components, I used [this tutorial by Geoff Rich](https://geoffrich.net/posts/svelte-prefers-reduced-motion-store/) to set up a Svelte reactive store for its value (`$reducedMotion` in the code above).

#### **Events "Tabbed" Interface:**
Another first in this project was creating a "tabbed" interface for the `Events` component. I decided to use `button` elements for the tabs to show that they were interactable and used `aria-selected` to indicate which tab button was "active". When clicked, the buttons change the value of the `activeItem` variable, which is used extensively as both a class directive and attribute in order to change the content. 

To animate the content change, I originally wanted to use [Svelte's 
key blocks](https://svelte.dev/tutorial/key-blocks), which would automatically apply a Svelte transition on content change. However, I encountered an issue where the new item would take up space before the old one had left the DOM, even with the `delay` property on the `transition` set. This shifted content below it farther down the DOM and would briefly create a large gap. The problem stems from the fact that Svelte transitions create/destroy items in the DOM. [This Svelte REPL](https://svelte.dev/repl/78bee610166a486a9304b9bfbeb77887?version=3.20.1) demonstrates the issue if you remove `position: absolute` from the img & button styles.

After a lot of trial and error, I decided against using key blocks in this case. What I wanted was to animate the content change, so creating and removing elements from the DOM wasn't necessary. I instead used the class directive paired with a `setTimeout` function to add and remove animation classes on tab click.

#### **Booking Form:**
While the design of the form is definitely aesthetically pleasing, it did create a fair bit of complication. Because of the design, I could not use `date` or `time` inputs. They had to be custom, essentially turning what could have been two inputs into six. 😭

The form validation is where it got tricky. To save my sanity, I used a mixture of both browser and custom validation. The challenge only requires you to check that all fields are filled and that the email address is valid. Although I didn't do *complete* validation, I did take it a few steps further. My version checks for the following:

- All fields are filled.
- Email address is valid.
- All number inputs are numbers and within their specified range. (Browser validation)
- The date of reservation is today or later.
- The time of reservation is during opening hours, and accounts for the hours being different on weekends.

For the number of people selection, I've prevented the number from being less than one and also have "people" change to "person" if the number is one. 

The only thing I didn't manage to match was the AM/PM selector. I couldn't style the `select` and `option` elements like the design, but wanted to use them for the sake of accessibility.

#### **Safari Issues**
Finally, it seems I can't do a project without discovering a new Safari/iOS quirk. 😆 This time I found out that Safari doesn't recognize the `overflow` property if set on the `body`. [To be fair, this apparently applies to any browser that uses](https://stackoverflow.com/questions/14270084/overflow-xhidden-doesnt-prevent-content-from-overflowing-in-mobile-browsers) `<meta name ="viewport">`, but still adds fuel to my ever growing desire to burn Safari to the ground. Easy fix: Wrap all the content in a container div and add the `overflow` to that rather than the `body`. 👍 

### Useful Resources

- [Video Tutorial Playlist: The Net Ninja  Svelte Tutorial for Beginners](https://youtube.com/playlist?list=PL4cUxeGkcC9hlbrVO_2QFVqVPhlZmz7tO) 
- [Svelte Window Bindings Tutorial](https://svelte.dev/tutorial/svelte-window-bindings)
- [Svelte prefers-reduced-motion Store Tutorial](https://geoffrich.net/posts/svelte-prefers-reduced-motion-store/)
- [Setting up Svelte Routing](https://medium.com/globant/walking-down-the-svelte-route-67922ae16762)
  - Tip #1: The article mentions needing to add `hydratable: true` to the rollup.config.js, but doesn't say where it's supposed to go. Answer: Under the Svelte `compilerOptions`.
    ```JS
    plugins: [
		svelte({
			compilerOptions: {
				dev: !production,
				hydratable: true
			}
      ```
  - Tip #2: If you've set up your routing according to the instructions but are still tearing your hair out because nothing seems to be working, try restarting your dev server.  
