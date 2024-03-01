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

## Feed.js

`Feed.js` is a functional component rendering a list of posts using the `Post` component. It maps through an array of posts and displays individual posts using the `Post` component.

**Props:**
- `posts`: Array of post objects.

**Functionality:**
- Maps through posts and renders `Post` component for each.

**Purpose:**
Displays a feed of posts with a focus on reusability through the `Post` component.
## Footer.js

`Footer.js` is a functional component that displays the count of blog posts. It utilizes the `useStoreState` hook from `easy-peasy` to retrieve the `postCount` state.

**Functionality:**
- Retrieves the `postCount` state using `useStoreState`.
- Displays the total count of blog posts in the footer.

**Purpose:**
Provides a simple and informative footer with the count of blog posts for the users.

## Header.js

`Header.js` is a functional component responsible for rendering the header of the React blog application. It uses icons from the `react-icons/fa` library to represent different device views (mobile, tablet, laptop). The component also dynamically adjusts its layout based on the window width using the `useWindowSize` hook.

**Functionality:**
- Displays the title passed as a prop in an `<h1>` tag.
- Renders a device icon (mobile, tablet, or laptop) based on the window width.
- Uses the `useWindowSize` hook to dynamically respond to changes in the window size.

**Purpose:**
Provides a visually appealing header with the blog title and an icon representing the current device view. The layout adapts to different screen sizes, enhancing the user experience.

## Home.js

`Home.js` is a functional component that serves as the main content area of the React blog application. It utilizes the `Feed` component to display blog posts and provides status messages for loading, fetch errors, and no posts found. It relies on the `useStoreState` hook from the `easy-peasy` state management library to access the application state.

**Functionality:**
- Renders a loading message while posts are being fetched.
- Displays an error message if there is a fetch error.
- Shows a message when no posts are found.
- Renders the `Feed` component to display the blog posts.

**Purpose:**
Acts as the main content area, providing feedback to users about the loading status and displaying the blog posts when available. Handles different scenarios gracefully, improving the user experience.

## Missing.js

`Missing.js` is a functional component that represents a 404 Not Found page. It provides a message indicating that the requested page is not found and suggests visiting the homepage using a link. The component uses the `Link` component from `react-router-dom` for navigation.

**Functionality:**
- Renders a message indicating that the page is not found.
- Includes a link to the homepage using the `Link` component.

**Purpose:**
Serves as the component to be displayed when a user navigates to a non-existent page, providing a friendly and navigational message.

## Nav.js

`Nav.js` is a functional component representing the navigation bar of the React blog application. It consists of a search input field and navigation links.

**Functionality:**
- Provides a search input field for filtering blog posts based on their title or body.
- Uses `useEffect` to filter and set search results when the posts or search term changes.
- Displays navigation links using the `Link` component from `react-router-dom` for navigating between Home, Post, and About pages.

**Purpose:**
Serves as the navigation component, allowing users to search for posts and navigate to different sections of the blog application. The search functionality dynamically updates the displayed posts based on the user's input.

## NewPost.js

`NewPost.js` is a functional component representing the page for creating a new blog post. It provides a form for users to input the title and body of the new post.

**Functionality:**
- Utilizes `useNavigate` from `react-router-dom` to navigate to different pages.
- Retrieves the current state of posts, post title, and post body using `useStoreState` from `easy-peasy`.
- Defines actions (`savePost`, `setPostTitle`, `setPostBody`) using `useStoreActions` to update the state.
- Handles the form submission using the `handleSubmit` function, which creates a new post object and triggers the `savePost` action.
- Redirects the user to the homepage (`'/'`) after submitting the new post.

**Purpose:**
Serves as the interface for users to create and submit new blog posts. The component dynamically updates the state based on user input and uses state management actions to handle post creation and navigation.

## Post.js

`Post.js` is a functional component responsible for rendering a single blog post in a summarized format. It provides a link to the detailed view of the post.

**Functionality:**
- Accepts a `post` object as a prop, which includes properties like `id`, `title`, `datetime`, and `body`.
- Utilizes the `Link` component from `react-router-dom` to create a hyperlink to the detailed view of the post (`/post/:id`).
- Displays the post title (`h2`), date (`p` with the class `postDate`), and a truncated version of the post body (`p` with the class `postBody`). The body is truncated to 25 characters with an ellipsis (...) if the length exceeds 25 characters.

**Purpose:**
Serves as a reusable component for rendering individual blog posts in a summarized format. This allows for a concise display of multiple posts, providing users with a quick overview before navigating to the detailed view by clicking on the post title.

## PostPage.js

`PostPage.js` is a React functional component responsible for rendering the detailed view of a single blog post. It allows users to view the complete content of a post, delete the post, and navigate to the edit page.

**Functionality:**
- Retrieves the `id` parameter from the URL using the `useParams` hook.
- Uses `useStoreActions` and `useStoreState` from `easy-peasy` to manage the state and actions related to blog posts.
- Fetches the specific post data using the `getPostById` selector.
- Provides conditional rendering based on whether the post is found:
  - If the post is found, it displays the post's title, date, body, and includes buttons to edit or delete the post.
  - If the post is not found, it displays a message stating "Post Not Found" and provides a link to the homepage.
- Utilizes the `Link` component from `react-router-dom` for navigation to the homepage and the edit page.
- Deletes the post when the "Delete Post" button is clicked.

**Purpose:**
This component serves as the detailed view for a single blog post. It provides users with the ability to read the complete content of a post, edit the post, or delete it. The conditional rendering ensures a user-friendly experience, handling scenarios where the requested post is not found.

## Store.js

The `Store.js` file configures the state management for the application using the `easy-peasy` library. It defines a store with actions, computed properties, and thunks to manage the application state related to blog posts.

**State Properties:**
1. `posts`: Array to store blog posts.
2. `postTitle`: String to store the title of a new post.
3. `postBody`: String to store the body of a new post.
4. `editTitle`: String to store the title during post editing.
5. `editBody`: String to store the body during post editing.
6. `search`: String to store the search term.
7. `searchResults`: Array to store search results.
8. `postCount`: Computed property to calculate the number of blog posts.
9. `getPostById`: Computed property to get a post by its ID.

**Actions:**
1. `setPosts`: Updates the `posts` array with the payload.
2. `setPostTitle`: Updates the `postTitle` with the payload.
3. `setPostBody`: Updates the `postBody` with the payload.
4. `setEditTitle`: Updates the `editTitle` with the payload.
5. `setEditBody`: Updates the `editBody` with the payload.
6. `setSearch`: Updates the `search` with the payload.
7. `setSearchResults`: Updates the `searchResults` with the payload.

**Computed Properties:**
1. `postCount`: Calculates the number of blog posts in the `posts` array.
2. `getPostById`: Returns a function to find a post by its ID.

**Thunks:**
1. `savePost`: Async function to save a new post. Sends a POST request to the API and updates the state with the new post.
2. `deletePost`: Async function to delete a post. Sends a DELETE request to the API and updates the state by removing the deleted post.
3. `editPost`: Async function to edit a post. Sends a PUT request to the API and updates the state with the edited post.

**Purpose:**
The purpose of this file is to define the global state and actions needed for the React application. It provides a centralized store to manage and update the state related to blog posts. The use of easy-peasy makes it easy to define and manage the state, actions, and thunks in a clean and organized manner.




