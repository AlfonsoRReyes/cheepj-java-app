
## Run

### Locally
Assumes you have an `index.html` with this line:
```js
await cheerpjRunJar("/app/TextDemo.jar");
```

1. Start `http-server` on the current local folder. Example `http-server -p 8080`  
2. Click on one of the IP addresses provided by the script. Example: http://127.0.0.1:8080
3. When your internet browser opens the page, wait for few seconds until the Java application is converted to WebAssembly


### Remotely
This assumes you have this folder in GitHub. We will need to change `index.html` file on the line cited above as this:
```js
await cheerpjRunJar("/app/cheerpj-java-app/TextDemo.jar");
```
where we have added the name of the repository `cheerpj-java-app` to the path.


1. Enable **GitHub Pages** for this repository, with *Settings | Pages*; Build and Deployment Source: **Deploy from a branch**;  Branch: `main / root`
2. Wait few seconds until the build finishes. You will see a web address at GitHub Pages. Something like this: `https://username/github.io/cheerpj-java-app`
3. Wait few seconds for cheerpJ to build the application


