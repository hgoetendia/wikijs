<!-- TITLE: Flexbox -->

# xs, sm, md, lg, xl 

Based: https://stackoverflow.com/questions/43445592/what-is-the-meaning-of-xs-md-lg-in-css-flexbox-system

*   Extra small xs < 576px 
*   Small       sm < 768px 
* 	Medium      md < 992px 
* 	Large       lg < 1200px
* 	Extra Large xl > 1200px


Let us assume that our screen is divided into 12 columns.

The xs part takes up when screen is extra small, Similarly small, medium and large classes as well, based on their respective screen size definition in CSS.

The example you provided:


```javascript
<Row>
  <Col xs={12} sm={3} md={2} lg={1} />
  <Col xs={6} sm={6} md={8} lg={10} />
  <Col xs={6} sm={3} md={2} lg={1} />
</Row>
```

For our sake lets assume these three columns are named as col-1, col-2 and col-3

On an extra small screen:

col-1 takes up all the 12 columns and the rest two of them take 6 each(on a new row) enter image description here

On small screens

col-1 and col-3 takes up 3, while the middle one col-2 takes 6 enter image description here

Similarly
Medium screens enter image description here

Large screens enter image description here

P.S. Images are screenshots of the link you provided (by resizing the browser for each screen size)