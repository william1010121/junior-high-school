  
在 Ruby 中，你可以使用 File 类和相关的方法来处理文件。以下是一些常见的文件处理操作：

## 打開文件
使用`File.open`方法打開文件,並且可以指定打開模式
```ruby 
File.open(file_pos, "r") do |file|
	#再內部處理文件
end
```

## 讀取文件
```ruby
content = File.read(file_pos)
# type(content) = string
```

## 逐行讀取文件
```ruby
File.foreach(file_pos) do |line|
	#do something
end
```

## 寫入文件

```ruby
File.open(file_pos, "w") do |file|
	# file.write()
	# file.puts()
end
```

## 追加內容到文件

```ruby
File.open("file.txt", "a") do |file|
	# file.write()
	# file.puts()
end
```


## 如何遍歷`folder`

```ruby
Dir.foreach( folder_path )
	.reject{ |item| item == '.' or item == '..'} # 這可以避免到訪問到當前目錄跟前一個目錄
```

### 例子
```ruby
test_input = Dir.foreach(test_input_folder)
				.reject{ |item| item == '.' or item == '..' }
				.select{ |item| item.end_with?(".in") }
				.map{ |file_name| File.join(test_input_folder, file_name) }
				.sort{ |a, b| a <=> b}
				.map{ |file_name| File.open(file_name, 'rb')}
```
