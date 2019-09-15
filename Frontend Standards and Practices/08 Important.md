# Important

We use alias in app src. So we don't need to have a deep location digging.

example:

### importing Actions

```
 // hard way
 import todoAction from '../../stores/actions/todoAction';
 // easy way
 import todoAction from '@app/action/todoAction';
```

### importing Components

```
 // hard way
 import todoComponent from '../../Component/todoComponent ';
 // easy way
 import todoComponent from '@app/Component/todoComponent ';
```

### importing Images

```
 // hard way
 import logo from '../../Assets/images/icon/logo.png';
 // easy way
 import logo from '@app/assets/images/icon/login.png';
```

and same with Common, Modules.
