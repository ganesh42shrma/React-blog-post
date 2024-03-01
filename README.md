## App.js

**Overview:**
`App.js` is the main entry point for the React blog post application. It manages global state, renders components based on routes, and fetches data from the API.

**Components Import:**
- **Header:** Renders the application header.
- **Nav:** Renders the navigation bar.
- **Footer:** Renders the footer.
- **Home:** Displays a list of blog posts.
- **NewPost:** Provides a form for creating a new blog post.
- **EditPost:** Allows editing an existing blog post.
- **PostPage:** Displays details of a specific blog post.
- **About:** Renders the about page.
- **Missing:** Renders a 404 error page.

**Hooks and Libraries:**
- **useEffect:** Executes actions after component mounts (e.g., updating global state).
- **useAxiosFetch:** Custom hook for making API requests using Axios.
- **useStoreActions:** Dispatches actions to modify global state.
- **BrowserRouter, Routes, Route, useNavigate:** Handles client-side routing.

**Functionality:**
1. **Fetching Data:** Uses `useAxiosFetch` to get blog post data from `http://localhost:5000/posts`.
2. **Global State Management:** Updates global state with fetched data using 'easy-peasy'.
3. **Routes Configuration:** Uses 'react-router-dom' for client-side routing based on URL.

**Rendering:**
Renders the application structure, including header, navigation, content based on the route, and footer.

**Purpose:**
Acts as a central configuration point for the application structure, routing, and global state management.

## EditPost.js

**Overview:**
`EditPost.js` is a component responsible for editing existing blog posts. It retrieves the post details, allows the user to modify the title and body, and updates the post accordingly.

**Hooks and Libraries:**
- **useEffect:** Executes actions after component mounts (e.g., setting initial post values).
- **useParams:** Extracts parameters from the URL.
- **useNavigate:** Navigates to a different route.
- **useStoreState, useStoreActions:** Accesses and modifies global state using 'easy-peasy'.
- **format:** Formats date using the 'date-fns' library.

**Global State Management:**
- **editTitle, editBody:** Store state representing the title and body being edited.
- **getPostById:** Retrieves a specific post from global state by its ID.
- **editPost, setEditTitle, setEditBody:** Actions to update global state with edits.

**Functionality:**
1. **Fetching Post Data:** Uses `useParams` to get the post ID from the URL and `getPostById` to fetch the post details.
2. **Setting Edit Values:** Uses `useEffect` to set initial values for editing (title and body).
3. **Editing Post:** Updates the post title and body using `setEditTitle` and `setEditBody`.
4. **Handling Edit:** Executes `handleEdit` on the 'Submit' button click, updating the post with edited values and navigating to the post page.

**Rendering:**
- **Edit Form:** Renders a form with input fields for title and body.
- **Conditional Rendering:** Checks if `editTitle` exists; if not, displays a message indicating that the post was not found.
- **Link to Home:** Provides a link to the home page in case the post is not found.

**Purpose:**
Facilitates the editing of existing blog posts, updating both the UI and global state with the modified content.
