# How to use react-router on Netlify.

When using react-router on Netlify, direct access to under the sub directory was 404 notfound.

Because Netlify's server does not redirect sub directories to `index.html`.

## Conclusion

Netlify was supported define redirect rules.

`./public/_redirects`

```
/* /index.html 200
```
