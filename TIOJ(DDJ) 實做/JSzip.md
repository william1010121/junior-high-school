是一個 `javascript` 的`module`它可以將文件進行壓縮

## 引入
```javascript
<script src="https://cdnjs.cloudflare.com/ajax/libs/jszip/3.6.0/jszip.min.js"></script>
```

## `JSzip`對`.in`, `.out` 檔案預設不會有壓縮行為
需要自行設置
```javascript
zip_file_object.file(file.name, file, {compression: "DEFLATE"});
```

## `zip_file.generateAsync`之後就需要用到`promise`了
因為`.zip`檔案可能會產生很久,所以他是非阻塞式的,如果沒有用`.then()`的會你的瀏覽器什麼都不會拿到

如果需要同時上傳兩個`zip_file`可以利用`Promise.all([])`
```javascript
Promise.all([
testInputZip.generateAsync({type:"blob"}),
testOutputZip.generateAsync({type:"blob"})
]).then( function(result) {
	do_something
})
```

