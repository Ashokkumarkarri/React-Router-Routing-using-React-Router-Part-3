


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

## ✅ Step 3: Make API Call for Specific BlogItemDetails

🧩 When a component is rendered using `Route`, React Router automatically provides some built-in **props** like:

- `match` – info about how the route matched
- `location` – current URL info
- `history` – browser history methods

➡️ We used `match` to get **route parameters** (in our case, the `id` from `/blogs/:id`).

```js
const { match } = this.props
const { params } = match
const { id } = params
```
📌 Here’s what happens:

match.params gives us the id that was clicked (e.g., /blogs/3 → id = 3)
We use this id to fetch data for that specific blog

🔄 Making the API Call on Mount
When the component loads (mounts), we call the API using the extracted id.

```js
componentDidMount() {
  this.getBlogItemData()
}

getBlogItemData = async () => {
  const { match } = this.props
  const { params } = match
  const { id } = params

  const response = await fetch(`https://apis.ccbp.in/blogs/${id}`)
  const data = await response.json()

  const updatedData = {
    imageUrl: data.image_url,
    title: data.title,
    auther: data.auther,
    avatarUrl: data.avatar_url,
    content: data.content,
    id: data.id,
    topic: data.topic,
  }

  this.setState({ blogData: updatedData })
}

```
We converted snake_case keys from the API to camelCase

We stored the cleaned blog data in the component’s state using setState

✅ This ensures that each blog page loads and displays its own content based on the URL id.