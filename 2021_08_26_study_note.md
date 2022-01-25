## 1. promise object
### definition: gets a message for an asynchronous operation
```
const p1 = new Promise(function(resolve,reject){
    resolve("成功");
    reject("失败");
})
p1.then(function(value){
    console.log(value);
});
```
## 2. fetch()
### definition: get resources asynchronously across the network
```
fetch('https://jsonplaceholder.typicode.com/comments/1')
    .then( makeResponse => makeResponse.json())
    .then(makeData => console.log(makeData))
```
## 3.async & await
### definition: async suspends execution if it encounters await
```
function testAwait(){
 console.log("testAwait");
 }
 async function helloAsync(){
    await testAwait();
    console.log("helloAsync");
 }
 helloAsync();
 ```
## 4. set()
### definition: can create a new set object
```
const a = new Set([1,2,3]);
console.log(a.size);
```