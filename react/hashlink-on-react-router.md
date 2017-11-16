# HashLink(example.com/#hashlink) does not working on React Router

It's deeper issue.

[Hash links · Issue \#394 · ReactTraining/react\-router](https://github.com/ReactTraining/react-router/issues/394)

I fixed using this wrapper library.

[rafrex/react\-router\-hash\-link: Hash link scroll functionality for React Router](https://github.com/rafrex/react-router-hash-link)

``` js
// In YourComponent.js
...
import { HashLink as Link } from 'react-router-hash-link';
...
// Use it just like a RRv4 link (to can be a string or an object, see RRv4 api for details):
<Link to="/some/path#with-hash-fragment">Link to Hash Fragment</Link>
```
