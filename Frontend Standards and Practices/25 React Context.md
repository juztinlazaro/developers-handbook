# React Context

Context is designed to share data that can be considered “global” for a tree of React components,

Every Context object comes with a Provider React component that allows consuming components to subscribe to context changes.

*setting up context provider*
```
interface IAppState {
  isLoggedIn: boolean;
}

class App extends Component<{}, IAppState> {
  state = {
    isLoggedIn: false,
  };

  componentDidMount() {
    const isLoggedIn = localStorage.getItem('isLoggedIn');
    this.setState({
      isLoggedIn: isLoggedIn === 'true',
    });
  }

  handleLogin = () => {
    this.setState({ isLoggedIn: true });
    localStorage.setItem('isLoggedIn', 'true');
  };

  handleLogout = () => {
    this.setState({ isLoggedIn: false });
    localStorage.removeItem('isLoggedIn');
  };

  render() {
    const { isLoggedIn } = this.state;

    return (
      <AppContext.Provider
        value={{
          isLoggedIn,
          onLogin: this.handleLogin,
          onLogout: this.handleLogout,
        }}
      >
        <Layout>
          <Router isLoggedIn={isLoggedIn} />
        </Layout>
      </AppContext.Provider>
    );
  }
}
```

*setting up useContext*
```
import React from 'react';

export interface IAppContext {
  isLoggedIn: boolean;
  onLogin: () => void;
  onLogout: () => void;
}

export const AppContextDefaultValue = {
  isLoggedIn: false,
  onLogin: () => false,
  onLogout: () => false,
};

const AppContext = React.createContext<IAppContext>(AppContextDefaultValue);

export const useAppContext = () => React.useContext(AppContext);

export default AppContext;
```

*useContext consumer*
```
import React from 'react';
import { Link } from 'react-router-dom';
import { useAppContext } from 'appRoot/App.context';

const Navigation = () => {
  const { isLoggedIn, onLogin, onLogout } = useAppContext();

  return (
    <div className="item link-items">
      {isLoggedIn ? (
        <>
          <Link to="/" className="link">
            Home
          </Link>

```