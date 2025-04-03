# Server and Client Components

### Server and Client Environments

In the context of web applications:

- The client refers to the browser on a user’s device that sends a request to a server for your application code. It then turns the response it receives from the server into an interface the user can interact with.

- The server refers to the computer in a data center that stores your application code, receives requests from a client, does some computation, and sends back an appropriate response.

Each environment has its own set of capabilities and constraints. For example, by moving rendering and data fetching to the server, you can reduce the amount of code sent to the client, which can improve your application's performance. But, as you learned earlier, to make your UI interactive, you need to update the DOM on the client.

Therefore, the code you write for the server and the client is not always the same. Certain operations (e.g. data fetching or managing user state) are better suited for one environment over the other.

### Network Boundary

The Network Boundary is a conceptual line that separates the different environments.

In React, you choose where to place the network boundary in your component tree. For example, you can fetch data and render a user's posts on the server (using Server Components), then render the interactive LikeButton for each post on the client (using Client Components).

Similarly, you can create a Nav component that is rendered on the server and shared across pages, but if you want to show an active state for links, you can render the list of Links on the client.

Behind the scenes, the components are split into two module graphs. The server module graph (or tree) contains all the Server Components that are rendered on the server, and the client module graph (or tree) contains all Client Components.

After Server Components are rendered, a special data format called the React Server Component Payload (RSC) is sent to the client.

The RSC payload contains:

- The rendered result of Server Components.
- Placeholders (or holes) for where Client Components should be rendered and references to their JavaScript files.
- React uses this information to consolidate the Server and Client Components and update the DOM on the client.
