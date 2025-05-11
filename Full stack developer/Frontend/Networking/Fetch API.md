The Fetch API is a modern interface that allows you to make asynchronous HTTP requests to servers. It provides a way to fetch resources (including across the network) similar to XMLHttpRequest, but with a more powerful and flexible feature set. It is built into the global window object and is designed to be more powerful and flexible than its predecessor, XMLHttpRequest.

Here are some key points to understand about the Fetch API:

1. **Simpler syntax:** The Fetch API offers a simpler and more powerful syntax compared to the traditional XMLHttpRequest. It uses the `fetch()` method to make requests and returns a Promise.
    
2. **Promise-based:** Asynchronous operations using the Fetch API are based on Promises, which allow you to handle the results in a more convenient and consistent way, using `then()` and `catch()` methods.
    
3. **Request and response:** When making a request, you can provide various options including the HTTP method, headers, and body data. Once a request is sent, the API returns a response object that represents the response from the server. You can then use methods like `json()`, `text()`, or `blob()` to extract the data from the response.
    
4. **Handling errors:** The Fetch API also allows you to handle network errors and HTTP error status codes in a more elegant way compared to traditional approaches. You can use the `catch()` method to catch any errors that might occur during the fetch operation.
    
5. **Cross-origin resource sharing (CORS):** Like XMLHttpRequest, the Fetch API is subject to the same-origin policy. However, it also supports Cross-Origin Resource Sharing (CORS), which allows you to make requests to servers on different domains, provided the server is configured to allow such requests.
    

Here is a basic example of using the Fetch API to make a GET request:

Fetch alternatives

- Axios
- Superagent