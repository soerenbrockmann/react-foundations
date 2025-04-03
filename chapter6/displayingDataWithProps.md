# Displaying Data with Props

Regular HTML elements have attributes that you can use to pass pieces of information that change the behavior of those elements. For example, changing the src attribute of an <img> element changes the image that is shown. Changing the href attribute of an <a> tag changes the destination of the link.

In the same way, you can pass pieces of information as properties to React components. These are called props.

Similar to a JavaScript function, you can design components that accept custom arguments (or props) that change the component's behavior or what is visibly shown when it's rendered to the screen. Then, you can pass down these props from parent components to child components.

In your HomePage component, you can pass a custom title prop to the Header component, just like you'd pass HTML attributes:

 <Header title="React" />

And Header, the child component, can accept those props as its first function parameter:

```jsx
function Header(props) {
  console.log(props); // { title: "React" }
  return <h1>{props.title}</h1>;
}
```

Since props is an object, you can use object destructuring to explicitly name the values of props inside your function parameters.

```jsx
function Header({ title }) {}
```

Then you can replace the content of the <h1> tag with your title variable.
To use the title prop, add curly braces {}. These are a special JSX syntax that allows you to write regular JavaScript directly inside your JSX markup.

```jsx
return <h1>{title}</h1>;
```

You can think of curly braces as a way to enter "JavaScript land" while you are in "JSX land". You can add any JavaScript expression (something that evaluates to a single value) inside curly braces. For example:

1. An object property with dot notation:

```jsx
function Header(props) {
  return <h1>{props.title}</h1>;
}
```

2. A template literal:

```jsx
function Header({ title }) {
  return <h1>{`Cool ${title}`}</h1>;
}
```

3. The returned value of a function:

```jsx
function createTitle(title) {
  if (title) {
    return title;
  } else {
    return "Default title";
  }
}

function Header({ title }) {
  return <h1>{createTitle(title)}</h1>;
}
```

4. Or ternary operators:

```jsx
function createTitle(title) {
  if (title) {
    return title;
  } else {
    return "Default title";
  }
}

function Header({ title }) {
  return <h1>{createTitle(title)}</h1>;
}
```

You can now pass any string to your title prop, or, if you used the ternary operator, you could even not pass a title prop at all, since you've accounted for the default case in your component:

```jsx
function Header({ title }) {
  return <h1>{title ? title : "Default title"}</h1>;
}

function HomePage() {
  return (
    <div>
      <Header title="React" />
      <Header title="A new title" />
    </div>
  );
}
```

### Iterating through lists

It's common to have data that you need to show as a list. You can use array methods to manipulate your data and generate UI elements that are identical in style but hold different pieces of information.

```jsx
function HomePage() {
  const names = ["Ada Lovelace", "Grace Hopper", "Margaret Hamilton"];

  return (
    <div>
      <Header title="Develop. Preview. Ship." />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>
    </div>
  );
}
```
