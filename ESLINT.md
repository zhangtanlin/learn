# ESLINT
ESLINT

## 文档
- [Eslint规则说明](https://segmentfault.com/a/1190000014230857)

## vscode配置
```
{
	//"files.autoSave": "onFocusChange", // 控制已更新文件的自动保存。接受的值:“off”、“afterDelay”、“onFocusChange”。如果设置为“afterDelay”，则可在 "files.autoSaveDelay" 中配置延迟。

	"editor.minimap.enabled": false, // 关闭右侧迷你代码预览
    	"editor.fontSize": 11, // 编辑器字体大小
    	"editor.formatOnSave": true, // 保存自动格式化
        //"editor.formatOnType": true, // 控制编辑器是否应在键入后自动设置行的格式
    	"editor.codeActionsOnSave": {
    		"source.fixAll.eslint": true, // 按 eslint 规则
  	}, // 保存时自动修复
  	"eslint.codeAction.showDocumentation": {
    		"enable": true
  	},
  	"eslint.options": {
    		"extensions": [
      			".js",
      			".jsx",
      			".vue",
      			".ts",
      			".tsx"
    		]
  	}, // 指定vscode的eslint所处理的文件的后缀
}
```