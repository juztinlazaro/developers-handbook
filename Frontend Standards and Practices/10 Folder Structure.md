# Folder Structure

### rootApp

    - routes - all about routing / private or public route
    - app.js which is the root application component

### Assets

    - all about css and image or future assets like fonts and etc.
     * CSS
       ```
       - components
         -- usable styles

       - modules
         -- Pages or modules styles

       - partials
         -- variables -> all about branding, example color scheme, font or etc.
         -- global -> global styles example: .text-primary { ... }

       - styles.scss
         -- css root file.
       ```

### Components

    - dumb components or presentational components that are global or reusable and shared components

### Modules

    - smart components or container, application pages

### hoc

    - higher order components

### Stores

    -  all about handling our application state in redux which is actions and reducers


```
        store ->
          module
           - module.actions.jsx
           - module.reducer.jsx
           - module.epics.jsx
           - module.types.jsx
           - module.model.jsx
```

### Common

    * config - application configuration
      example: application environment of development, production and testing or something.

    * constants - something not change or static
      example: company number, company email, API endpoints, headers in request and etc.

    * utils - application utility and helpers function
      example: ellipsis, methods, validations and etc
