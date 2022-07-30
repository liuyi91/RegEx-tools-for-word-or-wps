## <font color=red>Word正则工具</font>
● 主要功能：本工具的用途是通过 *正则表达式* 进行更高效、灵活的查找、替换。**Word通配符**虽然强大，但是不及正则表达式灵活。**本工具目的不是替代它，而是弥补它的不足。。**

● 特别说明：仅供测试使用；**不足：** 如果文档内容较多、或表达式较为复杂时，查找和替换速度可能会有所下降。建议可以将 **Word通配符** 和本工具配合使用， 哪个解决问题更方便，就用哪个！

● 热键：运行软件后，在word或wps文档中按下**F12**，即可调出程序窗口

正则表达式引擎为:Pcre8.1，与大多软件的正则表达式兼容，如vba、emEditor
> 注1:    替换中的引用为 $1,$2,$3....$9等
>
> 注2:    支持环视，例如(?<=\\,)\y+(?=\\,) 可以查找标点符号之间的中文
>
> 注3:    支持\K模式，例如\\,\K\y+可以查找以标点符号开始的中文
>
> 注4:    支持POSIX字符集，例如[[:alpha:]]可以查找[a-zA-Z]字符，[[:punct:]]可以查找标点符号
>
> 注5:    替换中$L0转为小写，$U0转为大写
>
> 注6:    匹配表格中单元格数值：(?:^|\a)\K-?[\d.]++(?=\a)

### 下载地址
●  下载地址:[蓝奏云:https://sixtyone.lanzoux.com/b015cpfji](https://sixtyone.lanzoux.com/b015cpfji)
    
●  视频介绍: [bilibili视频](https://space.bilibili.com/250915492/video)

●  ReadMe: [ReadMe](http://note.youdao.com/noteshare?id=987641bbdbfbe3d9a7b321ddfd5f4004&sub=55634728E5FB4B55AD5D6675769F4C6A)        
    
●  交流反馈及更多小工具请关注QQ群：595797774（1群已满） <font color=red>**2群：233862980**</font>

### 一般设置
| 特殊        | 描述      |
| ------------- | ------------- |
| i)  | 忽略大小写 |
| m)  | 多行模式 |
|<font color=red>\\,<br>匹配常见标点</font>|<font color=red>!"#$%&'()*+,\-.\/:;<=>?@[\]^_`{\|}~！\\“”￥‘’（），、。：；《》？【】……·◎○※×±Φφδ≠≥≤↑→↓ ∥∧∨①②③④⑤⑥⑦⑧⑨⑩ⅠⅡⅢⅣⅤⅥⅦⅧⅨⅩⅪⅫ★☆℃√</font>|
|<font color=red>\\y<br>匹配常规中文</font>|<font color=red>即等于：[\x{4e00}-\x{9fa5}]<br>约等于：[一-龟]</font>|


### 替换中的m=>模式
| 格式        | 描述      |
| ------------- | ------------- |
| **m=>** | <font color=red>**必须前缀格式**</font> |
| i.0  | 一般用作序号<br>如1：++i.0<br>如2："<" ++i*2-1 ">" |
| m[0]、m[1]  | 替换引用由$1,$2,$3变成m[1],m[2]... |
| StrLower(m[0])<br>StrUpper(m[0])  | 转小写<br>转大写 |
| StrLen(m[0])  | 长度 |
| SubStr(m[0],start,length)  | 截取字符 |
| (m[0] >10 ) ? "Z" : "L"  | 三元运算 |
| StrSplit(A_clipboard,"`n")[++i.0]  | 替换为剪切板的第n行数据 |
| **y2z(m[0])**  | 英文字符转中文字符：<br>**!"'(),.:;<>?[]** 转为 **！“ ’（），。：；《》？【】**  |
|**z2y(m[0])**   | 中文字符转英文字符：<br>**！“ ’（），。：；《》？【】** 转为 **!"'(),.:;<>?[]**  |
| **h2f(m[0])<br>f2h(m[0])**  | 半角转全角<br>全角转半角 |


### 通用语法
| 常用元素        | 描述      |
| ------------- | ------------- |
| .  | 默认情况下, 句点匹配换行符(\r\n) 中除\r外的任何单个字符|
| *  |星号匹配零个或多个前面的字符, 例如, a* 可以匹配 ab 和 aaab. 它还可以匹配完全不包含 "a" 的任意字符串的开始处|
| ?  |问号匹配零或一个前面的字符,可以理解为"前面的那项是可选的". 例如, colou?r 可以匹配 color 和 colour, 因为 "u" 是可选的|
| (?:xxx)  |不捕获分组|
| +  |加号匹配一个或多个前面的字符,例如 a+ 可以匹配 ab 和 aaab. 但与 a* 和 a? 不同的是, 模式 a+ 不会匹配开始处没有 "a" 的字符串|
| {min,max} |匹配出现次数介于 min 和 max 的前面的字符, 例如, a{1,2} 可以匹配 ab 但只匹配 aaab 中的前两个a<br>此外, {3} 表示准确匹配 3 次, 而 {3,} 则表示匹配 3 次或更多. 注: 指定的数字必须小于 65536, 且第一个必须小于等于第二个|
| [...]  |字符类: 方括号把一列字符或一个范围括在了一起(或两者). 例如, [abc] 表示 "a, b 或 c 的中任何一个字符". 使用破折号来创建范围; 例如, [a-z] 表示 "在小写字母 a 和 z(包含的) 之间的任何一个字符". 列表和范围可以组合在一起; 例如 [a-zA-Z0-9_] 表示 "字母, 数字或下划线中的任何一个字符"<br>字符类后面可以使用 *, ?, + 或 {min,max} 进行限定. 例如, [0-9]+ 匹配一个或多个任意数字; 因此它可以匹配 xyz123 但不会匹配 abcxyz<br>通过 [[:xxx:]] 还支持下列 POSIX 命名集, 其中 xxx 是下列单词的其中一个: alnum, alpha, ascii(0-127), blank(space 或 tab), cntrl(控制字符), digit(0-9), xdigit(十六进制数), print, graph(排除了空格的打印字符), punct, lower, upper, space(空白), word(等同于 \w)<br>在字符类中, 只有在类中具有特殊含义的字符才需要进行转义; 例如 [\^a], [a\-b], [a\]] 和 [\\a]|
| [^...] |匹配 不 在类中的任何一个字符. 例如, [^/]* 匹配零个或多个 不是 正斜杠的任意字符, 例如 http://. 同样地, [^0-9xyz] 匹配既不是数字也不是 x, y 或 z 的任何一个字符|
| \d  |匹配任意一个数字(相当于类 [0-9]). 相反的, 大写的 \D 表示 "任意的 非 数字字符". 这个和下面的两个都可以用在字符类中; 例如, [\d.-] 表示 "任何数字, 句点或负号"|
| \s  |匹配任意单个空白字符 , 主要是空格, tab 和换行符(`r 和 `n)<br>大写的 \S 表示 "任何 非空白字符"|
| \w  |匹配任何单个 "单词" 字符, 即字母, 数字或下划线. 这等同于 [a-zA-Z0-9_]<br>大写的 \W 表示 "任何 非单词字符"|
| ^<br>$  |抑扬符(^) 和美元符($) 被称为 锚, 因为它们不消耗任何字符; 相反地, 它们把模式限定在被搜索字符串的开始或末尾进行匹配<br>在模式的开始处使用 ^ 表示需要在行的开始处进行匹配. 例如, ^abc 可以匹配 abc123 但不匹配 123abc<br>在模式的末尾处使用 $ 表示需要在行的末端进行匹配. 例如, abc$ 可以匹配 123abc 但不能匹配 abc123<br>这两个锚还可以组合使用. 例如, ^abc$ 仅匹配 abc(即在它的前面或后面不能有另外的字符)<br>如果被搜索的文本包含多行, 则可以使用 "m" 选项让锚应用于每行而不是把所有文本作为整体. 例如, `am)^abc$ 可以匹配 123`r`nabc`r`n789. 如果没有 "m" 选项则不会匹配成功|
| \b  |"单词边界", 它类似锚, 因为它不消耗任何字符. 它要求当前字符的状态为单词字符(\w), 与前一个字符的状态相反. 它通常用来避免意外地匹配到在其他单词内的某个单词. 例如, \bcat\b 不会匹配 catfish, 但它可以匹配不论周围是否有标点或空白的 cat<br>大写的 \B 则相反: 它要求当前字符 不是 单词的边界|
| \|  |竖线将两个或多个可选项目分隔开来. 如果可选项目中 任何一个 满足条件, 则会形成匹配. 例如, gray\|grey 既可以匹配 gray 也可以匹配 grey. 同样地, 模式 gr(a\|e)y 中通过下面描述的括号的帮助可以实现同样的作用|
<details><summary><font color=blue>查看更多></font></summary>

>贪婪: 默认情况下, *, ?, + 和 {min,max} 是贪婪的, 因为它们消耗到 最后一个 能满足整个模式的可能的所有字符. 要让它们停在 首个 可能的字符, 请在它们后面加上问号. 例如, 模式 <.+>(其中没有问号) 表示: "搜索一个 <, 接着一个或多个任意字符, 然后是一个 >". 
>
>要在匹配 整个 字符串 \<em>text\</em\> 时停止, 请在加号后加上问号: <.+?>. 这样会让匹配在第一个 '>' 处停止, 因此它只匹配第一个标签 \<em\>.

> 预测和回顾断言: 这组 (?=...), (?!...), (?<=...) 和 (?<!...) 被称为断言, 因为它们要求符合某个条件但不消耗任何字符  
> 例如: abc(?=.*xyz) 中含有预测断言, 它要求在字符串 abc 右边的某个位置存在字符串 xyz(如果不存在, 则匹配失败)  
> (?=...) 被称为 正 预测断言, 因为它要求指定的模式存在.   
> (?!...) 被称为 负 预测断言, 因为它要求指定的模式 不 存在.   
> 同样地, (?<=...) 和 (?<!...) 分别是正的和负的 回顾 断言, 因为它们检查当前位置的 左边 而不是右边.   
>
> 回顾比预测受到更多的限制, 因为它们不支持可变大小的限定符, 例如 *, ? 和 +. 转义序列 \K 类似于回顾断言, 因为它会让前一个匹配的字符在最后的匹配字符串中省略. 例如, foo\Kbar 可以匹配 "foobar" 但报告匹配的结果为 "bar".  
>
> 对于中文字符的匹配, [一-龥] 匹配单个汉字(包含了几乎所有常见汉字)(等同于 [\x{4e00}-\x{9fa5}]), 容易记忆的版本为 [一-龟](等同于 [\x{4e00}-\x{9f9f}]). 而 [^\x00-\x7f] 能匹配 ASCII 码表以外的所有字符. ë 这个字符编码为 0x0065 0x0308, 字符串 "123ë56" 使用 .{1,6} 匹配到的是 "123ë5", 而使用 \X{1,6} 匹配到的是 "123ë56".  

> 最后说明: 尽管这个页面涉及了大多数常用的正则表达式功能, 但是还有相当一部分您可能希望了解的其他功能没有提及, 例如条件子模式、递归等. 完整的 PCRE 手册请访问 www.pcre.org/pcre.txt

> 正则替换模式时：替换内容用$0引用整个匹配的内容，$1引用第一组内容..$2..$3..  
> 正则代码中用\1引用第一个分组内容：如 (ab)ka\1  可以匹配abkaab
</details>


### 更新历史
- v1.1.3[2022.07.30]  
 ○ 更新替换中：m=>xxxx 的高级替换模式   
 ○ 例1:替换为序号: m=>++i.0   
 ○ 例2:替换为序号、: m=>++i.0 "、"   
 ○ 增加函数：半角转全角h2f,全角转半角f2h,英文符号转中文y2z，中文字符转英文z2y   

- v1.1.2[2022.07.27]     

- v1.1.1[2022.07.20]     
 ○ 修复ctrl+c在某些界面报错

- v1.1[2022.07.15]     
 ○ 增加页码   

- v1.0.9[2022.07.14]     
 ○ 增加支持更多格式   
 ○ 修复一些问题    
 ○ 增加托盘菜单:更新入口    

- v1.0.8[2022.07.06]     
 ○ 增加替换全部按钮    
 ○ 增加默认多行模式,**^\r** [在之前的版本中需要使用**m)^\r**] 可以匹配空行    
 ○ 增加点击列表标题全选列表

- v1.0.7[2022.07.05]     
 ○ 增加正则表达式 **\\,** 匹配常见标点符号    
 ○ 增加正则表达式 **\\y** 匹配常规中文  

- v1.0.6[2022.07.05]     
 ○ 增加ctrl+c复制列表框中的匹配项    
 ○ 增加可手动修改替换内容    

- v1.0.5[2022.07.02]     
 ○ 修复完善一些问题    
     
- v1.0.3      
 ○ 增加查找结果列表         
 ○ 增加增加替换功能      
