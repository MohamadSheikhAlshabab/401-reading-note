# React 2 [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read32.md)

## Conditional Rendering

  - Conditional rendering in React works the same way conditions work in JavaScript. 
  - Use JavaScript operators like if or the conditional operator to create elements representing the current state, and let React update the UI to match them.
  - 
  
          function UserGreeting(props) {
          return <h1>Welcome back!</h1>;
        }

        function GuestGreeting(props) {
          return <h1>Please sign up.</h1>;
        }
        
        
        function Greeting(props) {
        const isLoggedIn = props.isLoggedIn;
        if (isLoggedIn) {
          return <UserGreeting />;
        }
        return <GuestGreeting />;
      }

      ReactDOM.render(
        // Try changing to isLoggedIn={true}:
        <Greeting isLoggedIn={false} />,
        document.getElementById('root')
      );
      
      
- Element Variables

  - You can use variables to store elements. This can help you conditionally render a part of the component while the rest of the output doesn’t change.
  - 
  
        function LoginButton(props) {
        return (
          <button onClick={props.onClick}>
            Login
          </button>
        );
      }

      function LogoutButton(props) {
        return (
          <button onClick={props.onClick}>
            Logout
          </button>
        );
      }
      
      class LoginControl extends React.Component {
      constructor(props) {
        super(props);
        this.handleLoginClick = this.handleLoginClick.bind(this);
        this.handleLogoutClick = this.handleLogoutClick.bind(this);
        this.state = {isLoggedIn: false};
      }

      handleLoginClick() {
        this.setState({isLoggedIn: true});
      }

      handleLogoutClick() {
        this.setState({isLoggedIn: false});
      }

      render() {
        const isLoggedIn = this.state.isLoggedIn;
        let button;
        if (isLoggedIn) {
          button = <LogoutButton onClick={this.handleLogoutClick} />;
        } else {
          button = <LoginButton onClick={this.handleLoginClick} />;
        }

        return (
          <div>
            <Greeting isLoggedIn={isLoggedIn} />
            {button}
          </div>
        );
      }
      }

      ReactDOM.render(
        <LoginControl />,
        document.getElementById('root')
      );
      
- Inline If with Logical && Operator

  - You may embed expressions in JSX by wrapping them in curly braces. This includes the JavaScript logical && operator.
  - 
        
          function Mailbox(props) {
          const unreadMessages = props.unreadMessages;
          return (
            <div>
              <h1>Hello!</h1>
              {unreadMessages.length > 0 &&
                <h2>
                  You have {unreadMessages.length} unread messages.
                </h2>
              }
            </div>
          );
        }

        const messages = ['React', 'Re: React', 'Re:Re: React'];
        ReactDOM.render(
          <Mailbox unreadMessages={messages} />,
          document.getElementById('root')
        );
        
        render() {
        const count = 0;
        return (
          <div>
            { count && <h1>Messages: {count}</h1>}
          </div>
        );
       }

- Inline If-Else with Conditional Operator
  - Another method for conditionally rendering elements inline is to use the JavaScript conditional operator condition ? true : false.
  - 
          
          render() {
          const isLoggedIn = this.state.isLoggedIn;
          return (
            <div>
              The user is <b>{isLoggedIn ? 'currently' : 'not'}</b> logged in.
            </div>
          );
        }
        
  - It can also be used for larger expressions although it is less obvious what’s going on:
  
        render() {
        const isLoggedIn = this.state.isLoggedIn;
        return (
          <div>
            {isLoggedIn
              ? <LogoutButton onClick={this.handleLogoutClick} />
              : <LoginButton onClick={this.handleLoginClick} />
            }
          </div>
        );
       }

- Preventing Component from Rendering

  - In rare cases you might want a component to hide itself even though it was rendered by another component.
  - To do this return null instead of its render output.
  
    
          function WarningBanner(props) {
            if (!props.warn) {
              return null;
            }

            return (
              <div className="warning">
                Warning!
              </div>
            );
          }

          class Page extends React.Component {
            constructor(props) {
              super(props);
              this.state = {showWarning: true};
              this.handleToggleClick = this.handleToggleClick.bind(this);
            }

            handleToggleClick() {
              this.setState(state => ({
                showWarning: !state.showWarning
              }));
            }

            render() {
              return (
                <div>
                  <WarningBanner warn={this.state.showWarning} />
                  <button onClick={this.handleToggleClick}>
                    {this.state.showWarning ? 'Hide' : 'Show'}
                  </button>
                </div>
              );
            }
          }

          ReactDOM.render(
            <Page />,
            document.getElementById('root')
          );
