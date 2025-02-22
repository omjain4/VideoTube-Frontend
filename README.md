# VideoTube Frontend: A React-based Video Sharing Platform

VideoTube Frontend is a comprehensive React-based web application that provides a feature-rich video sharing platform. It offers a wide range of functionalities including video uploading, playlist management, user authentication, and social interactions.

The application is built using modern web technologies and best practices, leveraging the power of React, Redux, and React Router for a seamless user experience. It incorporates features such as video playback, user channels, comments, likes, subscriptions, and a dashboard for content creators.

## Repository Structure

```
.
├── src/
│   ├── app/
│   │   ├── Slices/
│   │   └── store.js
│   ├── assets/
│   ├── components/
│   ├── helpers/
│   ├── hooks/
│   ├── pages/
│   ├── App.jsx
│   └── main.jsx
├── index.html
├── package.json
├── postcss.config.js
├── tailwind.config.js
├── vercel.json
└── vite.config.js
```

### Key Files:
- `src/main.jsx`: The entry point of the application, setting up routing and Redux store.
- `src/App.jsx`: The main application component, handling initial loading and theme.
- `src/app/store.js`: Redux store configuration, combining all slices.
- `vite.config.js`: Vite configuration for development and build processes.
- `vercel.json`: Vercel deployment configuration.

### Important Integration Points:
- Redux store (`src/app/store.js`): Central state management.
- API connections: Handled through axios in various slice files.
- React Router: Defined in `src/main.jsx` for client-side routing.

## Usage Instructions

### Installation

Prerequisites:
- Node.js (v14 or later)
- npm (v6 or later)

Steps:
1. Clone the repository:
   ```
   git clone <repository-url>
   cd videotube-frontend
   ```
2. Install dependencies:
   ```
   npm install
   ```

### Getting Started

1. Start the development server:
   ```
   npm run dev
   ```
2. Open your browser and navigate to `http://localhost:5173` (or the port shown in your terminal).

### Configuration

The application uses environment variables for configuration. Create a `.env` file in the root directory with the following variables:
```
VITE_API_BASE_URL=<your-api-base-url>
```

### Common Use Cases

1. User Authentication:
   ```javascript
   import { login } from './app/Slices/authSlice';
   
   // In your component
   const dispatch = useDispatch();
   dispatch(login({ username, password }));
   ```

2. Fetching Videos:
   ```javascript
   import { getAllVideos } from './app/Slices/videoSlice';
   
   // In your component
   const dispatch = useDispatch();
   dispatch(getAllVideos(userId));
   ```

3. Creating a Playlist:
   ```javascript
   import { createPlaylist } from './app/Slices/playlistSlice';
   
   // In your component
   const dispatch = useDispatch();
   dispatch(createPlaylist({ data: playlistData }));
   ```

### Testing & Quality

To run linting:
```
npm run lint
```

### Troubleshooting

1. API Connection Issues:
   - Problem: Unable to connect to the backend API
   - Solution: 
     1. Check if the API server is running
     2. Verify the `VITE_API_BASE_URL` in your `.env` file
     3. Check for any CORS issues in the browser console

2. Build Errors:
   - Problem: Build fails with module resolution errors
   - Solution:
     1. Delete the `node_modules` folder
     2. Run `npm install` again
     3. If the issue persists, check for any conflicting dependencies in `package.json`

### Debugging

To enable debug mode:
1. Set `localStorage.setItem('debug', 'true')` in the browser console
2. Refresh the page
3. Check the browser console for detailed logs

Log files are not applicable for this frontend application.

### Performance Optimization

- Use the React DevTools profiler to identify performance bottlenecks
- Implement lazy loading for route components to reduce initial load time
- Use memoization techniques (e.g., `useMemo`, `useCallback`) for expensive computations

## Data Flow

The application follows a unidirectional data flow pattern using Redux:

1. User interactions trigger actions (e.g., `login`, `getAllVideos`)
2. Actions are dispatched to the Redux store
3. Reducers process these actions and update the state
4. React components re-render based on the updated state

```
User Interaction -> Action Creator -> Action -> Reducer -> Updated State -> React Component
```

Important technical considerations:
- Async operations are handled using Redux Thunk middleware
- State updates are immutable to ensure predictable behavior
- Components use selectors to efficiently access and derive data from the state

## Deployment

The application is configured for deployment on Vercel:

1. Ensure you have the Vercel CLI installed: `npm i -g vercel`
2. Run `vercel` in the project root to deploy
3. Follow the prompts to link your Vercel account and project

The `vercel.json` file configures routing for the single-page application, ensuring all non-file requests are handled by the main `index.html`.