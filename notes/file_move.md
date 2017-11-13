## 管理文件与快速移动

#### 管理缓冲区

`vim *.txt`

- `:ls` 列出所有缓冲区文件
- `:bnext :bprev :bfirst :blast`
- `:b{number}`
- `<C-^>` 文件切换
- `:args`
- `:edit xxx.md`

#### 切分窗口

- `<C-w>s` 水平切分
- `<C-w>v` 垂直切分
- `sp(lit) {file}`
- `vsp(lit) {file}`
- `close` `<C-w>c` 关闭活动窗口
- `only` `<C-w>o` 关闭其他窗口

#### 标签页

- `tabedit {file}` 新标签页打开
- `<C-w>T` 把当前窗口移动到新标签页
- `tabclose` 
- `tabonly`
- `gt` `gT` 切换

#### netrw管理文件系统

- `:Explore`
- `Sexplore`
- `Vexplore`
- `Texplore`

### 移动

- `gj gk g0 g^ g$` 屏幕行移动
- `w b e ge` 单词移动
- `W B E GE` 单词移动

#### 查找

- `f{char} F{char}` 查找移动到字符
- `t{char} T{char}` 查找移动到字符的前一个
- `;` 自动下一个
- `,` 返回上一个
- `dt.` 删除到.的前一个

#### 文本对象选择

- `it at` xml标签
- `cit cat yit yat dit dat` 操作
- `is as ip ap` 句子 段落

#### 标记

- `m{a-zA-Z}` 标记
- `{a-zA-Z} 跳转标记
- mm `m
- `` 当前文件中上次跳转之前的位置
- `. 上次修改的位置
- `^ 上次插入的地方
- `[ 上次修改或复制的起始位置
- `] 上次修改或复制的结束位置
- `< 上次高亮选区的起始位置
- `> 上次高亮选区的结束位置
- `%` 匹配括号之间跳转

#### surround.vim

- `viwS"` 单词上加引号
- `ds"` 删除引号
- `cs"'` 修改引号
- `ysw"` 当前位置到单词末尾加引号
- `ysiw"` 单词加引号
- `dst` 删除标签
