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


# Example

  
```javascript
render() {    
	
    var graphList = this.state.dashboardUsersData.map(function (userInfo, index) {
      return <Row style={rowStyle} gutter={0} justify="start" key={index}>
        <Col md={24} sm={24} xs={24} style={colStyle}>
          <ContentHolder>
            <DashboardCharts data={userInfo.dataOfMonth} title={userInfo.userInfo.name} />
          </ContentHolder>
        </Col>
      </Row>
    });


    return (
          {
            <ul>{graphList}</ul>
          }
    );
}
```


