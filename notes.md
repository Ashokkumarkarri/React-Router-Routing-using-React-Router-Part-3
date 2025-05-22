


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

