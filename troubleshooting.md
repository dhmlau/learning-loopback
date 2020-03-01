# Troubleshooting

## Quick Tips
- If you get an error but it doesn't provide enough information, you can turn on debug mode. That is, instead of starting the application using `npm start`, use this: 
    ```sh
    DEBUG=loopback:* npm start
    ```

    _TODO_: Should have something like this? https://loopback.io/doc/en/lb3/Setting-debug-strings.html


### Error about a binding key not bound
```
500 Error: The key 'services.hasher' is not bound to any value in context application
```

#### What does that mean?
The error means the binding key is not bound to a value. 

#### How to fix?
Set the value for the binding key in the application. i.e. Go to your application, typically it is in `src/application.ts`, 
```ts
// if your binding key is meant to bind to a class 
this.bind(SOME_BINDING_KEY).toClass(AClass)
```

See more details in [Binding documentation page](https://loopback.io/doc/en/lb4/Binding.html).

### I deleted a Controller but it keeps complaining about it

#### What does that mean?
The transpiled JavaScript files probably didn't get updated properly. 

#### How to fix?
Run `npm run clean` to delete all the transpiled files. By doing so, it forces the build to generate the transpiled JS files next time when you start the application using `npm start` or call `npm run build`.