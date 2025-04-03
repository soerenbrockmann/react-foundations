# Adding Interactivity with State

### Handling events

You can define a function to "handle" events whenever they are triggered. Create a function before the return statement called handleClick():

```jsx
function HomePage() {
  // 	...
  function handleClick() {
    console.log("increment like count");
  }

  return (
    <div>
      {/* ... */}
      <button onClick={handleClick}>Like</button>
    </div>
  );
}
```

### State and hooks

React has a set of functions called hooks. Hooks allow you to add additional logic such as state to your components. You can think of state as any information in your UI that changes over time, usually triggered by user interaction.

- The first item in the array is the state value, which you can name anything. It's recommended to name it something descriptive.

- The second item in the array is a function to update the value. You can name the update function anything, but it's common to prefix it with set followed by the name of the state variable you're updating.

- You can also take the opportunity to add the initial value of your likes state to 0.

```jsx
function HomePage() {
  // ...
  const [likes, setLikes] = React.useState(0);

  function handleClick() {
    setLikes(likes + 1);
  }

  return (
    <div>
      {/* ... */}
      <button onClick={handleClick}>Likes ({likes})</button>
    </div>
  );
}
```

Clicking the button will now call the handleClick function, which calls the setLikes state updater function with a single argument of the current number of likes + 1.
