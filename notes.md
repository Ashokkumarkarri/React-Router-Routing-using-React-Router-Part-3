


# 📝 Commit 1: Navigating to Specific Blog

##Navigating to specific Blog:
1. Add Link for BlogItem
2. Add BlogItemDetails Route
3. Make API call for Blog Specific BlogItemDetails

## ✅ Step 1: Add Link for BlogItem

➡️ First, we imported `Link` from `react-router-dom`  
```js
import { Link } from 'react-router-dom'
```
➡️ Then, we wrapped the blog item div with Link.
This makes the entire blog item clickable.

➡️ We used the to prop to tell React Router which path it should navigate to when the blog is clicked.
In this case, the path is /blogs/:id, and the actual URL becomes something like /blogs/1 based on the blog's id.

```js
<Link to={`/blogs/${id}`} className="blog-item-link">
  {/* Blog content */}
</Link>
```
📌 Now, when the user clicks on a blog item,
the browser URL changes to something like /blogs/1
(based on that blog's ID)

✅ This sets up the navigation.
In the next step, we’ll add a route to display the full blog details.

---

## ✅ Step 2: Add BlogItemDetails Route

➡️ In `App.js` or your main routing file, we added a new route for individual blog items.

```js
<Route exact path="/blogs/:id" component={BlogItemDetails} />
```
🛣️ Here, /blogs/:id is a dynamic route — :id acts like a variable called a route param.

This param captures the id from the URL when a user clicks a blog.

🧠 For example:

If the user clicks a blog with id 1, the URL becomes /blogs/1.

React Router matches this path and renders the BlogItemDetails component.

📌 Inside BlogItemDetails, you can access this id param to fetch or display the specific blog details.

✅ This route helps us display details for each specific blog item on a new page.

---