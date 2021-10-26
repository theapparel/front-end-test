# Manufactured - Front-end test

Welcome to the technical test for front-end developers. For this test, you'll need to make a React front-end that integrates with a GraphQL API.

## Requirements

- Make a private repo on Github
- Use React with TypeScript, other than that you can freely choose which libraries you use
- Integrate with the GraphQL API at https://dev.gql.manufactured.net/graphql
- Make a "Sign In" screen that calls the `signIn` mutation with an email & password from the user
- Make an "Identification" page with an email input, when submitted it should call `requestSignUp` with it. If you get an error with `code` `CONFLICT`, you need to redirect to the "Sign In" page
- Otherwise, you will get an email with a link that includes a query string with a JWT like: `?token=$JWT`
- Make a "Sign Up" page that gets the same querystring as above, asks the missing fields from the user and calls `signUp` with `token` (the JWT), `firstName`, `lastName` (optional), `password`, and an `organization` with `name`, `title`. Ignore the rest.
- When you call `signIn` or `signUp` successfully, you'll get a `User`. You need to include its `token` which will be a session JWT.
- From then on, you need to include the session JWT for all requests in the `Authorization` header as `Authorization: Bearer $JWT` (Do not use the JWT from the email/query string here)
- In both cases, redirect the user to a "Homepage". It should call `me` to get the `User` and show the following fields from it:
  1. Email
  1. First Name
  1. Last Name
  1. Created At
  1. `Memberships`, for each one show the `role` and the `Organization`'s (`org`):
    - Name
    - Kind
    - Created At
- If you clear the JWT and get `null` from the `me` query, you need to redirect back to the "Identification" page
- You are done! invite [flesler](https://github.com/flesler/) to the repo for reviewing and email your point of contact

## Bonus points

You'll get bonus points the more you include from the following list:

- Make sessions remain even after refreshing the page
- Make the user re-type the `password` when signing up and compare it
- When redirected to the "Sign In" page from the "Identification" page, prefill the email that was already typed
- Add some nice styling to the pages
- Make the "Sign Up" page show the `email` field as disabled and fill its value with the email inside the JWT (`identifier`)
- Properly handle errors in the pages, when missing fields or not passing them correctly
- Generate the TypeScript types based on the API (for example, using [this tool](https://www.graphql-code-generator.com/))
- Generate strongly typed queries & mutations (for example, using [this plugin](https://www.graphql-code-generator.com/docs/plugins/typescript-react-apollo) or similar)

## Final Notes

Please use **REAL** email addresses that you control when testing. If you need more than one, you use `+` in it. e.g. `myemail+2@gmail.com`.

If you have any questions or something in the API is not working as expected, feel free to consult us via email.

