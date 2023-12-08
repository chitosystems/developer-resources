#Steps to migrate CRA to Vite

1. Remove the react-scripts dependency from the package.json.  
```json
"react-scripts": "5.0.1"
```

3. Add sass in package.json, if you are using CSS or SCSS.  
>`npm i --save-dev sass`  

5. Add vite, @vitejs/plugin-react and etc as dev dependencies.  
  ```json
"devDependencies": {
    "path": "^0.12.7",
    "@vitejs/plugin-react-swc": "^3.5.0",
    "eslint-plugin-react": "^7.33.2",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.4",
    "vite": "^5.0.0"
}
```

4. Replace the start and build scripts as below:
```json
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint . --ext js,jsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview"
  }
````

5. Create a file vite.config.js in the root of the project with the below code:<br>
```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import viteTsconfigPaths from 'vite-tsconfig-paths'

export default defineConfig({
  plugins: [react(), viteTsconfigPaths()],
  server: {
    open: true,
    port: 3000,
  },
})
```

6. Move the index.html file from the public folder to the root of the project.
7. Remove all the occurrences of %PUBLIC_URL% from index.html.
The lines affected should look like the following lines after the change:
```html
<link rel="icon" href="/favicon.ico" />
<link rel="manifest" href="/manifest.json" />
```
8. Add the script tag below into the body of index.html:
```html
<script type="module" src="/src/index.jsx"></script>
```

9. Change the extension of .js files to .jsx, if they contain jsx syntax.  
10. Update all environment variables from REACT_APP to VITE.
  > Replace REACT_APP_HOST_URL to VITE_HOST_URL
> 
11. ```code
    npm install
    ```
