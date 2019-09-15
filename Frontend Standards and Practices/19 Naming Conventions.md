# What is Naming Conventions?

Naming conventions are general rules applied when creating text scripts for software programming. They have many different purposes, such as adding clarity and uniformity to scripts, readability for third-party applications, and functionality in certain languages and applications. They range from capitalization and punctuation to adding symbols and identifiers to signify certain functions.

# Types of Naming Conventions

### 1. Kebab Case

is a type of naming style where a word is separated by a hypen(-) and in a lower case.

### 2. Camel Case

is the practice of writing compound words or phrases such that each word or abbreviation in the middle of the phrase begins with a capital letter, with no intervening spaces or punctuation.

### 3. Snake Case

is the practice of writing compound words or phrases in which the elements are separated with one underscore character (\_) and no spaces, with each element's initial letter usually lowercased within the compound and the first letter either upper- or lowercase—as in "foo_bar" and "Hello_world".

### 4. UPPERCASE

is the practice of writing compound words or phases in all uppercase letters and each word is separated with one underscore. Used primarily to identify constant variables.

## Examples:

| Types      |             Good Practice              |        Bad Practice |
| ---------- | :------------------------------------: | ------------------: |
| Kebab Case |          button-delete-action          | button-deleteAction |
| Camel Case | handleRemoveClass or HandleRemoveClass |  handleRemove-Class |
| Snake Case |          handle_remove_class           | handle_Remove-Class |

Never mix two types of naming style in naming any variables, classnames, ids, components, folder, and files. It will create confusion in other developers.

# Naming Standards

In order for naming to be more understandable we recommend it to be more descriptive and to prevent confusion with other developers we created a standard for naming.

### For Variables:

- it is in **camel case**.

#### `const fooVariable = 'foo';`

### For Constant Variables:

- it is in **UPPERCASE**.

#### `const PI = '3.14'`

#### `const STANDARD_USER_ACCOUNT = 'Standard User Account';`

#### `const AUTH_CONNECTION = GetBaseUrl('authConnection');`

### For ClassNames and Ids:

- it is in **kebab case**.

#### `className = "delete-button"`

#### `Id = "test-save-button"`

### except for ids that is being use for robot. ex. id="robot-btn-trBuilder"

### For Folders and Files in component and modules:

- it is the same for variables but the **camel case in every words is capitalize** except the index files (index.js, index.scss, index.jsx, etc.).

#### `Folder: AuctionCard, Files: AuctionCard.jsx`
