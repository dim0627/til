# How to interpolate all props in collection's function such as map.

``` react
<ul>
  {todos.map((todo, index) => (
    <Todo key={index} {...todo} onClick={() => onTodoClick(index)} />
  ))}
</ul>
```
