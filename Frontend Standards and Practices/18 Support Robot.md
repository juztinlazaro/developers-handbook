# Support Automated testing ROBOT

## We have an automated testing, created by QA.

## Rules

##### 1. We need to add a special unique `ID` in every element that has event that we use.

##### 2. ID convention `robot`-`elementType`-`elementTitle`. example: `robot-input-jobTitle`

## Don'ts

```
Never change and remove  the special unique ID. or if needed please inform our QA for the changes.
```

### Example:

1. We have a `textarea` in clarification comment, we need to add a special ID

```
<textarea id="robot-textArea-clarificationComment" />
```

2. We have a submit button for upload cv.

```
<button id="robot-btn-submitCV"> Submit </button>
```

## SYNTAX LIBRARY

| ELEMENT           |               SYNTAX               |
| ----------------- | :--------------------------------: |
| **Input**         |     robot-input-_elementTitle_     |
| **Input Number**  |   robot-input-num-_elementTitle_   |
| **Text Area**     |   robot-text-area-_elementTitle_   |
| **Button**        |      robot-btn-_elementTitle_      |
| **Select**        |    robot-select-_elementTitle_     |
| **Select Option** | robot-select-option-_elementTitle_ |
| **Tree Select**   |  robot-tree-select-_elementTitle_  |
| **Menu**          |     robot-menu-_elementTitle_      |
| **SubMenu**       |   robot-sub-menu-_elementTitle_    |
| **NavLink**       |   robot-nav-link-_elementTitle_    |
| **Radio Button**  |     robot-radio-_elementTitle_     |
| **Checkbox**      |   robot-checkbox-_elementTitle_    |
| **Switch**        |    robot-switch-_elementTitle_     |
| **Dropdown**      | robot-dropdown-menu-_elementTitle_ |
| **Date Picker**   |  robot-date-picker-_elementTitle_  |
