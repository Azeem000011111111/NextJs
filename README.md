<h1>Advanced Routing Patterns</h1>
The App Router also provides a set of conventions to help you implement more advanced routing patterns. These include:

<h2>Parallel Routes:</h2> Allow you to simultaneously show two or more pages in the same view that can be navigated independently. You can use them for split views that have their own sub-navigation. E.g. Dashboards.

<h2>Intercepting Routes:</h2> Allow you to intercept a route and show it in the context of another route. You can use these when keeping the context for the current page is important. E.g. Seeing all tasks while editing one task or expanding a photo in a feed.


Creating UI
Special file conventions are used to create UI for each route segment. The most common are pages to show UI unique to a route, and layouts to show UI that is shared across multiple routes.
For example, to create your first page, add a page.js file inside the app directory and export a React component:


(app/page.tsx)

export default function Page() {
  return <h1>Hello, Next.js!</h1>
}



