<h1 style={color:red}>Defining Routes</h1>
<h2>Advanced Routing Patterns</h2>
The App Router also provides a set of conventions to help you implement more advanced routing patterns. These include:

<h2>Parallel Routes:</h2> Allow you to simultaneously show two or more pages in the same view that can be navigated independently. You can use them for split views that have their own sub-navigation. E.g. Dashboards.

<h2>Intercepting Routes:</h2> Allow you to intercept a route and show it in the context of another route. You can use these when keeping the context for the current page is important. E.g. Seeing all tasks while editing one task or expanding a photo in a feed.


<h1>Linking and Navigating</h1>
There are two ways to navigate between routes in Next.js:
<ul>
<li>Using the <Link> Component</li>
<li>Using the useRouter Hook<li>
</ul>
