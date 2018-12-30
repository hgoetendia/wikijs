<!-- TITLE: Iterating & Rendering with Loops in React components  -->



Ref: https://thinkster.io/tutorials/iterating-and-rendering-loops-in-react
# Problem


```javascript
var Hello = React.createClass({
    render: function() {
        return (
            <ul>
                <li>Juan</li>
                <li>Luis</li>
                <li>Pedro</li>
            </ul>
        )
    }
});
```


# Solution


```javascript
var Hello = React.createClass({
    render: function() {
        var names = ['Juan', 'Luis', 'Pedro'];
        return (
            <ul>
                {names.map(function(name, index){
                    return <li key={ index }>{name}</li>;
                  })}
            </ul>
        )
    }
});
```


---

```javascript
var Hello = React.createClass({
    render: function() {
        var names = ['Juan', 'Luis', 'Pedro'];
        var namesList = names.map(function(name){
                        return <li>{name}</li>;
                      })

        return  <ul>{ namesList }</ul>
    }
});
```

