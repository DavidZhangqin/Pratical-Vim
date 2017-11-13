## 寄存器与宏
========

### 寄存器

- `"{register}` 指定寄存器
- `"ayiw` 复制到寄存器a `"ap`
- `"bdd` 整行复制到寄存器b `"bp`
- `""` 无名寄存器 `""p = p`
- `y{motion}` 复制专用寄存器 `"0`

**正常的dxy操作都会存入无名寄存器，若想使用复制内容不被覆盖则粘贴专用寄存器内容**

- `yiw` -> `diw` -> `"0p`替代`p`
- `:reg "0` 查看寄存器中内容

**寄存器分类**

- "" 无名寄存器，dxy
- "0 复制专用寄存器，y
- "a-"z 有名寄存器，需指定使用
- "- 黑洞寄存器
- "+ 系统剪贴板 `"+p` `<C+r>+`
- "\* 主剪贴板，鼠标中键
- "= 表达寄存器

### 宏

- `q` 录制或停止，`q{register}` 录制到指定寄存器
- `:reg {register}` 查看宏内容
- `@{register}` 执行宏，`@@` 重复执行最近调用的宏

#### 例子

1. x = "("+a+","+b+","+c+","+d+")" 在加号两边加空格

```
f+ -> s_+_<Esc> -> qq;.q -> 22@q // 执行22次，表示后面的全都执行
```

**串行执行失败会终止，并行则不会**

2. 比较串行和并行，将序号后的点替换成括号，并将首字母大写

```
1. one
2. two
// break
3. three
```

```
串行: qq -> 0f. -> r)w~ -> j -> q -> 3@q
并行: qq -> 0f. -> r)w~ -> q -> jVG -> :'<,'>normal @q
```

#### 给宏追加命令

```
qa -> 0f.rw~ -> q 少了j
:reg a -> qA -> j -> q -> :reg a
```

#### 对一组文件执行宏

```
vim .../source-code/macros/ruby_module/*.rb
:ls :bn :first :last :bp
:args *.rb
qa ->gg/class<CR> -> Omodule Rank<Esc> -> j>G(缩进) -> Goend<Esc> -> q

并行: :edit!(放弃对第一个缓冲区文件的修改) -> :argdo normal @a
串行: qA -> :next -> q -> 22@a

保存: wall
```

#### 给列表编号

```
:let i=1
qa -> I<C-r>=i<CR>)<Esc> -> :let i+= 1 ->q
jVG -> :'<,'>normal @a
```
#### 修改宏

```
:reg a
:put a -> 修改 -> 0"ay$ -> dd
:reg a
```

