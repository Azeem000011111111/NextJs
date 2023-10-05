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

<Link> Component
<Link> is a built-in component that extends the HTML <a> tag to provide prefetching and client-side navigation between routes. It is the primary way to navigate between routes in Next.js.















<h1>Prefetching is not enabled in development, only in production</h1>

You can use it by importing it from next/link, and passing a href prop to the component:

app/page.tsx

TypeScript

import Link from 'next/link'
 
export default function Page() {
  return <Link href="/dashboard">Dashboard</Link>
}
There are other optional props you can pass to <Link>. See the API reference for more.

Examples
Linking to Dynamic Segments
When linking to dynamic segments, you can use template literals and interpolation to generate a list of links. For example, to generate a list of blog posts:

app/blog/PostList.js

import Link from 'next/link'
 
export default function PostList({ posts }) {
  return (
    <ul>
      {posts.map((post) => (
        <li key={post.id}>
          <Link href={`/blog/${post.slug}`}>{post.title}</Link>
        </li>
      ))}
    </ul>
  )
}
Checking Active Links
You can use usePathname() to determine if a link is active. For example, to add a class to the active link, you can check if the current pathname matches the href of the link:

app/components/links.tsx

TypeScript

'use client'
 
import { usePathname } from 'next/navigation'
import Link from 'next/link'
 
export function Links() {
  const pathname = usePathname()
 
  return (
    <nav>
      <ul>
        <li>
          <Link className={`link ${pathname === '/' ? 'active' : ''}`} href="/">
            Home
          </Link>
        </li>
        <li>
          <Link
            className={`link ${pathname === '/about' ? 'active' : ''}`}
            href="/about"
          >
            About
          </Link>
        </li>
      </ul>
    </nav>
  )
}
Scrolling to an id
The default behavior of the Next.js App Router is to scroll to the top of a new route or to maintain the scroll position for backwards and forwards navigation.

If you'd like to scroll to a specific id on navigation, you can append your URL with a # hash link or just pass a hash link to the href prop. This is possible since <Link> renders to an <a> element.


<Link href="/dashboard#settings">Settings</Link>
 
// Output
<a href="/dashboard#settings">Settings</a>
Disabling scroll restoration
The default behavior of the Next.js App Router is to scroll to the top of a new route or to maintain the scroll position for backwards and forwards navigation. If you'd like to disable this behavior, you can pass scroll={false} to the <Link> component, or scroll: false to router.push() or router.replace().


// next/link
<Link href="/dashboard" scroll={false}>
  Dashboard
</Link>

// useRouter
import { useRouter } from 'next/navigation'
 
const router = useRouter()
 
router.push('/dashboard', { scroll: false })
