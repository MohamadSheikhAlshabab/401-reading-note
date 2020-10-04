#  React 1 [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read31.md)

## ES6 Syntax and Feature Overview

  - Legend:
    - Variable: x
    - Object: obj
    - Array: arr
    - Function: func
    - Parameter, method: a, b, c
    - String: str
    
  - Table of contents
    - Variable declaration
    - Constant declaration
    - Arrow function syntax
    - Template literals
    - Implicit returns
    - Key/property shorthand
    - Method definition shorthand
    - Destructuring (object matching)
    - Array iteration (looping)
    - Default parameters
    - Spread syntax
    - Classes/constructor functions
    - Inheritance
    - Modules - export/import
    - Promises/callbacks
    
  - Variables and constant feature comparison
      | Keyword	| Scope	        | Hoisting	| Can Be Reassigned	| Can Be Redeclared |
      | ---     | ---           | ---       |  ---              | ---               |
      | var	    | Function scope|	Yes       |	Yes	              | Yes               |
      |let	    | Block scope   | No	      | Yes	              | No                |
      |const	  | Block scope	  | No        |	No	              | No                |
      
  - Arrow functions
    - __ES5__
      - function func(a, b, c) {} // function declaration
      - var func = function (a, b, c) {} // function expression
    
    - __ES6__
      - let func = (a) => {} // parentheses optional with one parameter
      - let func = (a, b, c) => {} // parentheses required with multiple parameters 
      
  - Template literals
    - __ES5__
      - var str = 'Release date: ' + date
      
    - __ES6__
      - let str = `Release Date: ${date}`
      
   - Multi-line strings
   - __ES5__
     - var str = 'This text ' + 'is on ' + 'multiple lines'
     
  - __ES6__
    - let str = 
      ``` 
          `This text
            is on
           multiple lines`
      ```
  - Implicit returns
    - __ES5__
    
                      function func(a, b, c) {
                        return a + b + c
                      }
                      
    - __ES6__
    
                      let func = (a, b, c) => a + b + c // curly brackets must be omitted
                      
  - Key/property shorthand
    - __ES5__
    
                  var obj = {
                        a: a,
                        b: b,
                      }
    - __ES6__
    
                  let obj = {
                          a,
                          b,
                        }
- Method definition shorthand
  - __ES5__
  
                      var obj = {
                        a: function (c, d) {},
                        b: function (e, f) {},
                      }
                      
  - __ES6__
  
                    let obj = {
                      a(c, d) {},
                      b(e, f) {},
                    }
                    obj.a() // call method a
                    
- Destructuring (object matching) 
  - var obj = {a: 1, b: 2, c: 3} 
  
  - ES5
  
          var a = obj.a
          var b = obj.b
          var c = obj.c
          
  - ES6

          let {a, b, c} = obj
          
- Array iteration (looping)
  - var arr = ['a', 'b', 'c']
  - __ES5__
  
                      for (var i = 0; i < arr.length; i++) {
                        console.log(arr[i])
                      }
                      
  - __ES6__
  
                          for (let i of arr) {
                            console.log(i)
                          }
  
---

## Hello World
  
  
                ReactDOM.render(
                      <h1>Hello, world!</h1>,
                      document.getElementById('root')
                    );
- Introducing JSX
      
            const element = <h1>Hello, world!</h1>;
            
- Embedding Expressions in JSX

                  const name = 'Josh Perez';
                  const element = <h1>Hello, {name}</h1>;

                  ReactDOM.render(
                    element,
                    document.getElementById('root')
                  );
                  
- JSX is an Expression Too
  
          function getGreeting(user) {
                      if (user) {
                        return <h1>Hello, {formatName(user)}!</h1>;
                      }
                      return <h1>Hello, Stranger.</h1>;
                    }
                    
                    
- Specifying Attributes with JSX

        const element = <div tabIndex="0"></div>;
        const element = <img src={user.avatarUrl}></img>;
        
        
- JSX Represents Objects

            const element = (
            <h1 className="greeting">
              Hello, world!
            </h1>
          );
          
          const element = React.createElement(
            'h1',
            {className: 'greeting'},
            'Hello, world!'
          );
          
          
          // Note: this structure is simplified
          const element = {
            type: 'h1',
            props: {
              className: 'greeting',
              children: 'Hello, world!'
            }
          };

---

##  Rendering Elements
  
  - Rendering an Element into the DOM
      
        <div id="root"></div>
        
        const element = <h1>Hello, world</h1>;
        ReactDOM.render(element, document.getElementById('root'));
        
  - Updating the Rendered Element
  
          function tick() {
          const element = (
            <div>
              <h1>Hello, world!</h1>
              <h2>It is {new Date().toLocaleTimeString()}.</h2>
            </div>
          );
          ReactDOM.render(element, document.getElementById('root'));
        }

        setInterval(tick, 1000);
        
  - React Only Updates What’s Necessary
    - ![img](https://reactjs.org/c158617ed7cc0eac8f58330e49e48224/granular-dom-updates.gif)
    
---

## Components and Props

  - Function and Class Components
  
        function Welcome(props) {
          return <h1>Hello, {props.name}</h1>;
        }
      
      class Welcome extends React.Component {
          render() {
            return <h1>Hello, {this.props.name}</h1>;
          }
        }
        
  - Rendering a Component
  
        const element = <div />;
        
        const element = <Welcome name="Sara" />;
        
        function Welcome(props) {
        return <h1>Hello, {props.name}</h1>;
      }

      const element = <Welcome name="Sara" />;
      ReactDOM.render(
        element,
        document.getElementById('root')
      );
      
  - Composing Components
  
        function Welcome(props) {
          return <h1>Hello, {props.name}</h1>;
        }

                      function App() {
                        return (
                          <div>
                            <Welcome name="Sara" />
                            <Welcome name="Cahal" />
                            <Welcome name="Edite" />
                          </div>
                        );
                      }

                      ReactDOM.render(
                        <App />,
                        document.getElementById('root')
                      );
                      
  - Extracting Components
  
    
          function Comment(props) {
            return (
              <div className="Comment">
                <div className="UserInfo">
                  <img className="Avatar"
                    src={props.author.avatarUrl}
                    alt={props.author.name}
                  />
                  <div className="UserInfo-name">
                    {props.author.name}
                  </div>
                </div>
                <div className="Comment-text">
                  {props.text}
                </div>
                <div className="Comment-date">
                  {formatDate(props.date)}
                </div>
              </div>
            );
          }
          
          
          function Avatar(props) {
            return (
              <img className="Avatar"
                src={props.user.avatarUrl}
                alt={props.user.name}
              />
            );
          }
          
          
          function Comment(props) {
            return (
              <div className="Comment">
                <div className="UserInfo">
                  <Avatar user={props.author} />
                  <div className="UserInfo-name">
                    {props.author.name}
                  </div>
                </div>
                <div className="Comment-text">
                  {props.text}
                </div>
                <div className="Comment-date">
                  {formatDate(props.date)}
                </div>
              </div>
            );
          }
          
          
          function UserInfo(props) {
            return (
              <div className="UserInfo">
                <Avatar user={props.user} />
                <div className="UserInfo-name">
                  {props.user.name}
                </div>
              </div>
            );
          }
          
          
          function Comment(props) {
          return (
            <div className="Comment">
              <UserInfo user={props.author} />
              <div className="Comment-text">
                {props.text}
              </div>
              <div className="Comment-date">
                {formatDate(props.date)}
              </div>
            </div>
          );
        }
        
  - Props are Read-Only
  
  
        function sum(a, b) {
            return a + b;
          }
          
          
          function withdraw(account, amount) {
            account.total -= amount;
          }
          
---

## State and Lifecycle

  - Converting a Function to a Class
  
      - 1 - Create an ES6 class, with the same name, that extends React.Component.
      - 2 - Add a single empty method to it called render().
      - 3 - Move the body of the function into the render() method.
      - 4 - Replace props with this.props in the render() body.
      - 5 - Delete the remaining empty function declaration.
      
                class Clock extends React.Component {
                    render() {
                      return (
                        <div>
                          <h1>Hello, world!</h1>
                          <h2>It is {this.props.date.toLocaleTimeString()}.</h2>
                        </div>
                      );
                    }
                  }
                  
  - Adding Local State to a Class
  
    - Replace this.props.date with this.state.date in the render() method:
    
                class Clock extends React.Component {
                  render() {
                    return (
                      <div>
                        <h1>Hello, world!</h1>
                        <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
                      </div>
                    );
                  }
                }
                
      - Add a class constructor that assigns the initial this.state:
      
                  class Clock extends React.Component {
                    constructor(props) {
                      super(props);
                      this.state = {date: new Date()};
                    }

                    render() {
                      return (
                        <div>
                          <h1>Hello, world!</h1>
                          <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
                        </div>
                      );
                    }
                    
                    constructor(props) {
                    super(props);
                    this.state = {date: new Date()};
                  }
                  
                  
            - Remove the date prop from the <Clock /> element:
            
                      ReactDOM.render(
                        <Clock />,
                        document.getElementById('root')
                      );
                      
                      class Clock extends React.Component {
                      constructor(props) {
                        super(props);
                        this.state = {date: new Date()};
                      }

                      render() {
                        return (
                          <div>
                            <h1>Hello, world!</h1>
                            <h2>It is {this.state.date.toLocaleTimeString()}.</h2>
                          </div>
                        );
                      }
                    }

                    ReactDOM.render(
                      <Clock />,
                      document.getElementById('root')
                    );
                                       
             - 
