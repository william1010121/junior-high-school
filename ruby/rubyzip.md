是一個`ruby`中可以壓縮/解壓縮檔案的一個`moudule`

## 使用
可以再`gem file` 中加入
```gem
gem `rubyzip`
```
然後運行
```shell
bundle install
```
就可以順利安裝了
使用的話則是要再`ruby`裡面
```ruby
require 'zip'
```

## 打開 `Zip file`
可以使用 `Zip::file.open`
```ruby
require 'zip'
Zip::file.open(zip_file_path) do |zip|
	zip.each do |entry|
		entry.extract( extract_file_path )
	end
end
```
