- since we will export css files to javascript, we will not use dash naming in the names of the selectors, will use camelCasing instead
- to import styles using `styles.classname` , we have to name the css page `page.module.css` and store in `/app` directory
- have to close all tags in `jsx` like `</>`
- cannot put `route.js` and `page.jsx` in the same page
- for child component to talk/communicate to parent component, then will pass callback function to the child from the parent
- use `<link>` instead of `<a>` tag, so changing pages is faster
# Server Side vs Client Side
- server side data is pre-rendered, or we can say it is fast
- to make `page.jsx` into a client side script, will add `'use client'` line at the beginning of the script
