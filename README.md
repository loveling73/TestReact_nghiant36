# TestReact

#Test ReactJS EC, Fork this repo and show us your development progress via a Pull Request

## Reorder

Complete the List component, which accepts an items prop and moves the clicked element to the first place in the list.
For example, if the component has the list prop ["A", "B", "C"], the list should look like:
```html
<ul>
  <li>A</li>
  <li>B</li>
  <li>C</li>
</ul>
```

When item C is clicked in the list above, the list should be reordered, resulting in the following order:
```html
<ul>
  <li>C</li>
  <li>A</li>
  <li>B</li>
</ul>
```

Exam:
```javascript
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const List = (props) => {
  // Yоur cоdе gоеs hеrе
  return  null;
}

document.body.innerHTML = "<div id='root'> </div>";
  
const rootElement = document.getElementById("root");
ReactDOM.render(<List items={["A", "B", "C"]} />, rootElement);

let listItem = document.querySelectorAll("li")[2];
if(listItem) {
  listItem.click();
}
setTimeout(() => console.log(document.getElementById("root").innerHTML));
```

## Cards Widget

An HTML widget for a children's game represents a clickable card row. Initially, all cards are face down. Whenever a card is clicked, it is turned over to face up, and any card that was previously face up is turned over to face down. Only one card can be face up at one time. Cards that are face up should have the content 'up' while face down cards should have the content 'down'. When an 'up' card is clicked, it remains 'up'.

Implement the React component Cards that accepts the amount prop which defines how many cards there should be. The component should be rendered as a table element. 

For example, after clicking the second cell on the Cards component, rendered as:
```html
<Cards amount={4} />
```

the page should contain the following table:
```html
<table>
  <tbody>
    <tr>
      <td>down</td>
      <td>up</td>
      <td>down</td>
      <td>down</td>
    </tr>
  </tbody>
</table>
```

Exam: 
```javascript
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const Cards = (props) => {
  return null;
};

document.body.innerHTML = "<div id='root'> </div>";
  
const rootElement = document.getElementById("root");
ReactDOM.render(<Cards amount={4} />, rootElement);

let row = document.getElementById("root").getElementsByTagName("tr")[0];
if(row) {
  let cell = row.getElementsByTagName("td")[1];
  if(cell) {
    cell.click();
  }
}
setTimeout(() => console.log(document.getElementById("root").innerHTML));
```

## Theme Context Switcher

Finish the Content and App components so that the section has its class set appropriately. When the user clicks the button, class should toggle between "theme-light" and "theme-dark" values. Note the following criteria:

The ThemeContext Context provider should be used in your implementation. No additional prop-passing is needed.
The Content component should use the React.useContext function to pass the Context between components.
For example, after the first render, the section element should look like this:
```html
<section class="theme-dark"><span>Current theme: dark</span><button>Switch Theme</button></section>
```
After the first click, the section element should look like this:
```html
<section class="theme-light"><span>Current theme: light</span><button>Switch Theme</button></section>
```

```javascript
// React is loaded and is available as React and ReactDOM
// imports should NOT be used
const ThemeContext = React.createContext();

const Content = () => {
  const context = {}; // change this
  return (
    <section className={`theme-${context.theme}`}>
      <span>Current theme: {context.theme}</span>
      <button onClick={context.switchTheme}>Switch Theme</button>
    </section>
  );
};

function App() {
  const [theme, setTheme] = React.useState("dark");
  const switchTheme = () => {
    theme === "dark" ? setTheme("light") : setTheme("dark");
  };
  return (
    <ThemeContext.Provider value={{/* implement */}}>
      <Content />
    </ThemeContext.Provider>
  );
}

document.body.innerHTML = "<div id='root'></div>";
const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```
