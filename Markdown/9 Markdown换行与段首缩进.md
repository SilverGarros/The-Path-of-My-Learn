# Markdown 换行与段首缩进

## 换行

Markdown中，段落之间的换行是通过在段落之间留空行的方式来实现的。

```markdown
段落1

段落2
```

段落1

段落2

如果我们有其他的换行需求我们可以：

+ 键入HTML语言换行标签：`<br>`(通用)
+ 段落内换行使用换行符`<br>`，或者<kbd>两个空格</kbd>+<kbd>shift-Enter</kbd>(不推荐使用<kbd> \ </kbd><kbd>shift-Enter</kbd>).
+ Typora中，空格中使用四个空格（一个Tab）可以快速增大段落之间的间距

演示举例如下：

```markdown
春望<br>唐代:杜甫
		
国破山河在，城春草木深。
感时花溅泪，恨别鸟惊心。
烽火连三月，家书抵万金。
白头搔更短，浑欲不胜簪。
```

春望<br>唐代:杜甫

国破山河在，城春草木深。
感时花溅泪，恨别鸟惊心。
烽火连三月，家书抵万金。
白头搔更短，浑欲不胜簪。

+ 注意：Typora中使用<kbd>ENTER</kbd>会自动添加空格进行分段（本复刻MD笔记使用Typora编写但我在1-9的部分均未注意到这一点所以之前的笔记全部进行了自动换段，直到此刻我才注意到，苦笑，Typora可以使用<KBD>SHIFT</KBD>+<kbd>ENTER</kbd>进行段内换行，也可以使用上面介绍的通用方法）。

## 段首缩进

使用Markdown写文章不需要进行段首缩进。但如果你需要的话，可以在段落前面使用：

####  1 . 两个全角空格    

因为一个全角空格(space)的宽度是整整一个汉字，输入两个全角空格正好是两个汉字的宽度。 
~~全角空格的输入方法为：一般的中文输入法都是按 shift + space，可以切换到全角模式下，输完后再次按 shift + space 切换回正常输入状态。~~(`存疑待验证`)

#### 2. 使用特殊占位符

使用特殊占位符 

 ``` markdown
 &ensp; or &#8194;  表示一个半角的空格
 &emsp; or &#8195;  表示一个全角的空格
 &emsp;&emsp;       两个全角的空格（用的比较多）
 &nbsp; or &#160;   不断行的空白格
 ```

&ensp; or &#8194;  表示一个半角的空格
&emsp; or &#8195;  表示一个全角的空格
&emsp;&emsp;       两个全角的空格（用的比较多）
&nbsp; or &#160;   不断行的空白格

## See also

+ [CSDN-markdown 首行缩进的快捷实现：全角空格配合](https://blog.csdn.net/thither_shore/article/details/52205748)

