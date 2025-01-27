Steps I followed:

Install Node JS
Check version `node -v`
Check if npm is installed `npm -v`

Create new site on Local
Open WP Admin
Install the WPGraphQL plugin and within it Enable Debug Mode

Clone repo into desired location on your device
`npm install`
`npm run dev`

Navigate to --- and upload xml file from the repo
That will populate your page with dummy blog posts.

Create .env.local file within repo.
`NEXT_PUBLIC_WORDPRESS_API_URL=`
Set variable equal to your site domain found on Local
Stop and restart your local run of the site for updates.

*Follow tutorial for page imports and code changes.*

Use GraphQL's IDE within WP Admin
Within GraphiQL use the query composer.
```
const GET_POSTS = gql`
      query GetAllPosts {
            posts {
                nodes {
                    title
                    content
                    uri
                    date
                }
            }
        }
   `
   ```
Add to pages > index.js inside the getStaticProps() function.

*Follow tutorial for page imports and code changes.*

Back to the query composer.
```
const GET_POST_BY_URI = gql`
        query GetPostByURI($id: ID!) {
            post(id: $id, idType: URI) {
                title
                content
                date
                uri
                author {
                    node {
                        firstName
                        lastName
                    }
                }
            }
        }
   `
```
Add to pages > [uri].js inside the getStaticProps() function.

https://www.youtube.com/watch?v=wfy51nhjfUQ
