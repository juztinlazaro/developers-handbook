# SNIPPETS

## Creating your own snippets

You can define your own snippets, either global snippets or snippets for a specific language. To open up a snippet file for editing, select User Snippets under File > Preferences (Code > Preferences on macOS) and select the language (by language identifier) for which the snippets should appear or create a new global snippet (New Global Snippets file...).

## Snippets Format

```
{
    "For_Loop": {
        "prefix": "for",
        "body": [
          "for (const ${2:element} of ${1:array}) {",
          "\t$0",
          "}"
        ],
        "description": "For Loop"
    },
}

```

## Action, Types, Reducer, Epic snippets

```
{
    /*
    // Place your snippets for JavaScript React here. Each snippet is defined under a snippet name and has a prefix, body and
    // description. The prefix is what is used to trigger the snippet and the body will be expanded and inserted. Possible variables are:
    // $1, $2 for tab stops, $0 for the final cursor position, and ${1:label}, ${2:another} for placeholders. Placeholders with the
    // same ids are connected.
    // Example:
    "Print to console": {
        "prefix": "log",
        "body": [
            "console.log('$1');",
            "$2"
        ],
        "description": "Log output to console"
    }
*/
    "Reducer request": {
        "prefix": "rr",
        "body": [
            "[ACTION.getBlogSuccess]: (state, action) => ({",
            "...state,",
            "blogs: action.payload,",
            "loading: false,",
            "}),",
            "[ACTION.getBlogLoading]: (state, action) => ({",
            "...state,",
            "loading: true,",
            "}),",
            "[ACTION.getBlogError]: (state, action) => ({",
            "...state,",
            "error: action.payload,",
            "loading: false,",
            "}),",
            "[ACTION.getBlogCancel]: (state, action) => ({",
            "...state,",
            "loading: false,",
            "}),",
        ],
        "description": "Reducer request template"
    },
    "Action creator": {
        "prefix": "ac",
        "body": [
            "export const getBlogEpic = createAction(TYPES.GET_BLOG_EPIC);",
            "export const getBlogLoading = createAction(TYPES.GET_BLOG_LOADING);",
            "export const getBlogSuccess = createAction(TYPES.GET_BLOG_SUCCESS);",
            "export const getBlogError = createAction(TYPES.GET_BLOG_ERROR);",
            "export const getBlogCancel = createAction(TYPES.GET_BLOG_CANCEL);"
        ],
        "description": "action creator template"
    },
    "Action types": {
        "prefix": "at",
        "body": [
            "export const GET_BLOG_EPIC = 'GET_BLOG_EPIC';",
            "export const GET_BLOG_LOADING = 'GET_BLOG_LOADING';",
            "export const GET_BLOG_SUCCESS = 'GET_BLOG_SUCCESS';",
            "export const GET_BLOG_ERROR = 'GET_BLOG_ERROR';",
            "export const GET_BLOG_CANCEL = 'GET_BLOG_CANCEL';",
        ],
        "description": "action type template"
    },
    "action epic": {
        "prefix": "ae",
        "body": [
            "const postBlogUrl = 'https://jsonplaceholder.typicode.com/posts';",
            "export const postBlogEpic = action$ =>",
            "action$.ofType(TYPES.POST_BLOG_EPIC).switchMap(() => {",
            "const loading = of(ACTION.postBlogLoading());",
            "const success = ACTION.postBlogSuccess;",
            "const cancel = action$.ofType(TYPES.POST_BLOG_CANCEL);",
            "const error = ACTION.postBlogError;",
            "const formBody = JSON.stringify({",
            "title: 'foo',",
            "body: 'bar',",
            "userId: 1,",
            "});",
            "return concat(",
            "loading,",
            "postRequest(postBlogUrl, formBody, headers, success, cancel, error),",
            ");",
            "});",
        ],
        "description": "action epic template"
    },
}
```
