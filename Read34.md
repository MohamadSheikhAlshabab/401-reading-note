# React 3 [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read33.md)

## Quick Start

  - npx create-react-app demo-app
  - cd demo-app
  - Installation: `npm install react-router-dom`
  
  - EXAMPLE 1:
      
            
            import React from "react";
            import {
              BrowserRouter as Router,
              Switch,
              Route,
              Link
            } from "react-router-dom";

            export default function App() {
              return (
                <Router>
                  <div>
                    <nav>
                      <ul>
                        <li>
                          <Link to="/">Home</Link>
                        </li>
                        <li>
                          <Link to="/about">About</Link>
                        </li>
                        <li>
                          <Link to="/users">Users</Link>
                        </li>
                      </ul>
                    </nav>

                    {/* A <Switch> looks through its children <Route>s and
                        renders the first one that matches the current URL. */}
                    <Switch>
                      <Route path="/about">
                        <About />
                      </Route>
                      <Route path="/users">
                        <Users />
                      </Route>
                      <Route path="/">
                        <Home />
                      </Route>
                    </Switch>
                  </div>
                </Router>
              );
            }

            function Home() {
              return <h2>Home</h2>;
            }

            function About() {
              return <h2>About</h2>;
            }

            function Users() {
              return <h2>Users</h2>;
            }
            
  - EXAMPLE 2:
          
          import React from "react";
          import {
            BrowserRouter as Router,
            Switch,
            Route,
            Link,
            useRouteMatch,
            useParams
          } from "react-router-dom";

          export default function App() {
            return (
              <Router>
                <div>
                  <ul>
                    <li>
                      <Link to="/">Home</Link>
                    </li>
                    <li>
                      <Link to="/about">About</Link>
                    </li>
                    <li>
                      <Link to="/topics">Topics</Link>
                    </li>
                  </ul>

                  <Switch>
                    <Route path="/about">
                      <About />
                    </Route>
                    <Route path="/topics">
                      <Topics />
                    </Route>
                    <Route path="/">
                      <Home />
                    </Route>
                  </Switch>
                </div>
              </Router>
            );
          }

          function Home() {
            return <h2>Home</h2>;
          }

          function About() {
            return <h2>About</h2>;
          }

          function Topics() {
            let match = useRouteMatch();

            return (
              <div>
                <h2>Topics</h2>

                <ul>
                  <li>
                    <Link to={`${match.url}/components`}>Components</Link>
                  </li>
                  <li>
                    <Link to={`${match.url}/props-v-state`}>
                      Props v. State
                    </Link>
                  </li>
                </ul>

                {/* The Topics page has its own <Switch> with more routes
                    that build on the /topics URL path. You can think of the
                    2nd <Route> here as an "index" page for all topics, or
                    the page that is shown when no topic is selected */}
                <Switch>
                  <Route path={`${match.path}/:topicId`}>
                    <Topic />
                  </Route>
                  <Route path={match.path}>
                    <h3>Please select a topic.</h3>
                  </Route>
                </Switch>
              </div>
            );
          }

          function Topic() {
            let { topicId } = useParams();
            return <h3>Requested topic ID: {topicId}</h3>;
          }
          
---

## Styling and CSS
  
  - How do I add CSS classes to components?
  - Pass a string as the className prop:

            render() {
              return <span className="menu navigation-menu">Menu</span>
            }
            
      
          render() {
          let className = 'menu';
          if (this.props.isActive) {
            className += ' menu-active';
          }
          return <span className={className}>Menu</span>
          }
        
        
  - Can I use inline styles?
    - Yes, see the docs on styling here.

 - Are inline styles bad?
    - CSS classes are generally better for performance than inline styles.

 - What is CSS-in-JS?
  - “CSS-in-JS” refers to a pattern where CSS is composed using JavaScript instead of defined in external files.
  - Note that this functionality is not a part of React, but provided by third-party libraries. React does not have an opinion about how styles are defined; if in doubt, a good starting point is to define your styles in a separate *.css file as usual and refer to them using className.

- Can I do animations in React?
  - React can be used to power animations. See React Transition Group and React Motion or React Spring, for example.
  
---
## Create a Next.js App
  
  - To build a complete web application with React from scratch:
    - 1 -  Code has to be bundled using a bundler like webpack and transformed using a compiler like Babel.
    - 2 -  You need to do production optimizations such as code splitting.
    - 3 -  You might want to statically pre-render some pages for performance and SEO. You might also want to use server-side rendering or client-side rendering.
    - 4 -  You might have to write some server-side code to connect your React app to your data store.
  - Next.js has the best-in-class "Developer Experience" and many built-in features; a sample of them are:
    - 1 - An intuitive page-based routing system (with support for dynamic routes)
    - 2 - Pre-rendering, both static generation (SSG) and server-side rendering (SSR) are supported on a per-page basis
    - 3 - Automatic code splitting for faster page loads
    - 4 - Client-side routing with optimized prefetching
    - 5 - Built-in CSS and Sass support, and support for any CSS-in-JS library
    - 6 - Development environment with Fast Refresh support
    - 7 - API routes to build API endpoints with Serverless Functions
    - 8 - Fully extendable
    
---
## Sass Basics

  -  If you wanted to watch (instead of manually build) your input.scss file, you'd just add the watch flag to your command, like so: `sass --watch input.scss output.css`
  - Variables:
    - scss 
    
            SCSS SYNTAX
            $font-stack:    Helvetica, sans-serif;
            $primary-color: #333;

            body {
              font: 100% $font-stack;
              color: $primary-color;
            }
            
    - Sass
    
          $font-stack:    Helvetica, sans-serif
          $primary-color: #333

          body
            font: 100% $font-stack
            color: $primary-color
            
      - css
      
            body {
            font: 100% Helvetica, sans-serif;
            color: #333;
            }
    
    - Nesting
    
        - scss
        
              SCSS SYNTAX
              nav {
                ul {
                  margin: 0;
                  padding: 0;
                  list-style: none;
                }

                li { display: inline-block; }

                a {
                  display: block;
                  padding: 6px 12px;
                  text-decoration: none;
                }
              }
              
      - sass
      
                    nav
                ul
                  margin: 0
                  padding: 0
                  list-style: none

                li
                  display: inline-block

                a
                  display: block
                  padding: 6px 12px
                  text-decoration: none
                  
                  
      - css
      
                      nav ul {
                      margin: 0;
                      padding: 0;
                      list-style: none;
                    }
                    nav li {
                      display: inline-block;
                    }
                    nav a {
                      display: block;
                      padding: 6px 12px;
                      text-decoration: none;
                    }
                    
  - Modules
  
       - scss
      
            // _base.scss
            $font-stack:    Helvetica, sans-serif;
            $primary-color: #333;

            body {
              font: 100% $font-stack;
              color: $primary-color;
            }
            // styles.scss
            @use 'base';

            .inverse {
              background-color: base.$primary-color;
              color: white;
            }
            
      - sass
      
      
              // _base.sass
              $font-stack:    Helvetica, sans-serif
              $primary-color: #333

              body
                font: 100% $font-stack
                color: $primary-color

              // styles.sass
              @use 'base'

              .inverse
                background-color: base.$primary-color
                color: white
                
      - css
      
          
          
                body {
                font: 100% Helvetica, sans-serif;
                color: #333;
              }

              .inverse {
                background-color: #333;
                color: white;
              }

  - Mixins: Some things in CSS are a bit tedious to write, especially with CSS3 and the many vendor prefixes that exist. A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. A good use of a mixin is for vendor prefixes. Here's an example for transform.
  - Extend/Inheritance: This is one of the most useful features of Sass. Using @extend lets you share a set of CSS properties from one selector to another.
  - Operators:Doing math in your CSS is very helpful. Sass has a handful of standard math operators like +, -, *, /, and %. In our example we're going to do some simple math to calculate widths for an aside & article.
  
--- 
## Sass cheatsheet [url](https://devhints.io/sass)
