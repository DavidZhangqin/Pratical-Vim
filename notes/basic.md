## 模式命令

### 普通模式：normal mode

- `daw` 删除单词
- `10<C-a>` 下一个数字加10
- `9<C-x>` 下一个数字减9

**操作符 + 动作命令 = 操作**

**操作**

- `c d y`
- `g~ gu gU` 大小写转换
- `> < = !`

**行快捷操作**

- `>> gUgU/gUU dd yy`

### 插入模式: insert mode

- `<C-h>` 删除前一个字符
- `<C-w>` 删除前一个单词
- `<C-u>` 删除到行首
- `<C-o>zz` 将当前编辑行放在屏幕中间
- `<C-r>0` 粘贴y复制内容
- `<C-r>=2*3<CR>` 计算后输入

### 可视模式：visual mode

- `gv` 重选上次的高亮选区
- `o` 切换高亮选区的活动端
- `vit` 选择标签里的内容(abckhh) `<a href=“#">abc</a>`
- `gUit` 大写 `<a href=“#">ABC</a>`

**在行尾添加字符**

1. `$<C-v>jjjj` `A;<Esc>`
2. `<C-v>$jjjj` `A;<Esc>`
3. `A;` `:'<,'>normal .<CR>`
4. `%normal A;<CR>`

### 命令行模式：command mode

**Ex命令**

- `:[range]print` `p` 显示
- `:[range]delete` ``
- `:[range]join` ``
- `:[range]copy {address}` `t` 复制行到指定位置
- `:[range]move {address}` `m` 移动行到指定位置
- `:[range]yank` 
- `:[range]normal {commands}` 对每一行执行命令
- `:[range]substitute/{pattern}/{string}/[flags]` 替换pattern为string
- `:[range]global/{pattern}/[cmd]` 对匹配pattern的行，对其执行cmd
- `<C-r><C-w>` 复制当前光标下单词到命令行
- `<C-r><C-a>` 复制当前光标下字串到命令行
- `[range]!{cmd}`
- `[range]!{filter}` 使用外部程序{filter}过滤指定区域数据

**address**

- `.,$` 当前行到最后一行
- `%` 文件所有行 `1,$`
- `/<\/html>/+1` 匹配行+1
- `0` 第一行前一行

**例子**

- `g/{pattern}/m$` 移动指定行到文件末尾
- `6t.` 把第六行复制到当前行下面
- `t6` 把当前行复制到第六行下方
- `%normal i//` 所有行前加注释
- `%normal A;` 所有行尾加分号
- `%s//<C-r><C-w>/g` 替换
- `:w | !php %` 用php执行当前脚本
- `%!sort -t',' -k2` 逗号分隔，按第二列排序

