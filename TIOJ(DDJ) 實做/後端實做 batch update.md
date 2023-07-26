# 問題
## 問題一(前端判斷)

前端除了檢查檔案數量外，還要先檢查檔名有沒有對到 然後如果要壓縮檔案應該在傳輸前就壓縮

## 問題二(顯示上傳檔案配對)

```html
<div class="form-control flat">
	<div class="fold-container">
		<div class="fold-header">
			表格標題
			<button class='fold-toggle'>展開/收起</button>
		</div>
		<table class="fold-table">
		</table>
	</div>
</div>
```


```git
git diff "check the name equal" "add the view when update"
```

`ruby` 可以使用 `onchange` 來進行上傳檔案時的操作
```ruby
<%= f.file_field :test_output_list, :class => 'form-control flat', multiple: true, onchange: 'updateOutputFile(event)' %>
```
然後折疊地方的實現基本上就是套用一個 `jquery` 的 [[toggle]], 之後有三個函數
- `updateInputFile(event)` => 接收`InputFile`的資料並且fliter過一遍
- `updateOutputFile(event)` => 接收`OutputFile`的資料並且fliter過一遍
- `refreshFileListTable()` => 更新`table`裡面的值



## 問題三(壓縮文字檔案再上傳)


### 未壓縮文件格式
```
#<ActionDispatch::Http::UploadedFile:0x00007f42872b4c08 @tempfile=#<Tempfile:/tmp/RackMultipart20230526-108725-gpxlh3.out>, @original_filename="a935_16.out", @content_type="application/octet-stream", @headers="Content-Disposition: form-data; name=\"testdatum[test_output_list][]\"; filename=\"a935_16.out\"\r\nContent-Type: application/octet-stream\r\n">
```


## 實行過程

### `testdata/_form.html.erb`

- 使用[[JSzip]] (前端)
- 使用[[rubyzip]]（後端）
- 透過[[ruby file handling]]講檔案開啟成`file_input_list`, `file_output_list`並且處理它

