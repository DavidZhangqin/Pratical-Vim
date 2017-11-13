## 模式匹配与查找

### 模式匹配

1. `\v` 正则表达式模式开关

```
vim source-code/patterns/color.css
/\v#([0-9a-fA-F]{6}|[0-9a-fA-F]{3}`
```

2. `\V` 按原义查找

```
vim source-code/patterns/excerpt-also-known-as.txt
/\Va.k.a.
```

3. 捕获子匹配

```
vim source-code/patterns/???
/\v<(\w+)\_s+\1>
```

4. 界定单词边界

```
<> <the> 界定单词边界
%(And|D) 使用括号但不捕获内容
```
5. 界定匹配边界 `zs` `ze`

```
xxx "quoted words" xxx
/\v"[^"]+"<CR> "quoted words"
/\v"\zs[^"]+\ze"<CR> quoted words

xxx Pratical Vim xxx Vim
/Pratical Vim<CR>
/Pratical \zsVim<CR>
```

### 查找

- `<C-r><C-w>` 根据预览域结果对查找域补全
- `:%s///gn` 统计匹配个数，n表示不替换
- `/lang/e<CR>` 光标移到查找项结尾

#### 例子

1. XhtmlDocument XmlTag => XHTMLDocument XMLTag

```
/\vX(ht)?ml\C<CR> -> gU//e<CR> -> //<CR>. -> //<CR>.
```

2. 先查找再替换

```
vim source-code/search/quoted-strings.txt
/\v'(([^']|'\w)+)'
%s//"\1"/g
```
