## 前置知识

必备：python基础、HTML/CSS基础

可选：网络协议基础（有最好，没有也行），ajax基础

> 通用处理中文乱码的解决方案：
>
> ```python
> 标识符.encode('iso-8859-1').decode('gbk')
> ```

## 概念部分

### 什么是爬虫

通过编写程序，模拟浏览器上网，然后让其去互联网上抓取数据的过程

爬虫只是个工具，在法律中是不被禁止的，但是如果用爬虫爬取隐私信息，则属于违法行为

### 爬虫的分类

- 通用爬虫
  - 抓取系统重要组成部分。抓取的是一整张页面数据
- 聚焦爬虫
  - 建立在通用爬虫的基础之上，抓取页面中特定的局部内容
- 增量式爬虫
  - 检测网站中数据更新的情况，只会抓取网站中最新更新出来的数据

### 反爬机制

​	门户网站可以通过制定相关的策略或者技术手段防止爬虫程序进行网站数据的爬取

### 反反爬策略

​		爬虫程序可以通过制定相关的策略或者技术手段破解门户网站汇总具备的反爬机制，从而可以获取网站数据

- 反爬机制之robots.txt协议


该协议规定了网站中哪些数据可以被爬虫爬取，哪些数据不能被爬取。该协议是君子协议，并不强制遵守，但是如果执意爬取，可能会承担相应的责任。可以通过域名/robots.txt的方式查看该网站的协议

> 当爬取的数据不做商业用途时，一般可以无视这个协议，否则基本没有多少数据可以爬取

### http协议

http协议指超文本传输协议

概念：服务器和客户端进行数据交互的一种形式

http常用请求头信息

- User-Agent：请求载体的身份标识（请求载体指发起请求的人）
- Connection：请求完毕后是断开连接（close）还是保持连接（keep live）

http常用响应头信息

- Content-Type：服务器响应回客户端的数据类型

### https协议

https协议即加密后的http协议

- 加密方式
  - 对称密钥加密
    - 用同一种密钥进行加密解密，即客户端将密钥和密文分别发送给服务器，然后服务器利用密钥进行解密
  - 非对称密钥加密
    - 利用公钥和私钥分别进行加密和解密，其中公钥只能用于加密，无法解密
  - 证书密钥加密（HTTPS所采用的的方式）
    - 服务器将公钥发送给证书认证机构进行签名，然后将签名后的公钥和证书一起发送给客户端

## requests模块

requests模块是python中原生的一款基于网络请求的模块，功能非常强大，简单便捷效率高

作用：模拟浏览器发请求

如何使用：

- 指定url
- 发起请求
- 获取响应数据
- 存储数据

### UA伪装和UA检测

- UA伪装

指User-Agent伪装，即让爬虫对应的请求载体身份标识伪装成某一款浏览器

- UA检测

指门户网站的服务器会检测对应请求的载体身份标识，如果检测到请求的载体身份标识为某一款浏览器则说明该请求是正常的。如果检测到请求的载体身份标识不是基于某一款浏览器的则表示该请求为不正常请求（爬虫）

- 示范样例（爬取搜狗搜索返回的页面数据）

```python
import requests
# 指定py文件执行入口
if __name__ == "__main__":
    # UA伪装：将某款浏览器对应的User-Agent封装到一个字典中
    headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.74 Safari/537.36 Edg/99.0.1150.55'
    }
	# 指定url
    url = "https://www.sogou.com/web"
    # 处理url携带的参数：封装到字典中
    kw = input('enter a word:')
    param = {
        'query': kw
    }
    # 使用get方式发起请求，该方法会返回一个响应对象
    response = requests.get(url=url,params = param,headers=headers)
    # 获取响应数据，text返回的是字符串形式的响应数据，此处的为HTML结构
    page_text = response.text
    # 存储数据
    with open('./'+param['query']+'.html','w',encoding='utf-8') as fp:
        fp.write(page_text)
    print('爬取数据结束')
```

### 捕获ajax请求（可以获取局部数据）

打开浏览器开发者工具，打开网络选项卡，选择XHR（XHR为ajax数据包），然后观察数据包查看ajax请求格式

> 注意：如果ajax请求中有参数为空的变量，也要写入，否则可能无法返回数据

- 示范样例1（直接获取百度翻译的结果，下方只能获取单个单词翻译）

```python
import requests
import json
# 指定py文件执行入口
if __name__ == "__main__":
    # UA伪装：将某款浏览器对应的User-Agent封装到一个字典中
    headers = {
        'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.74 Safari/537.36 Edg/99.0.1150.55'
    }
	# 指定url
    url = "https://fanyi.baidu.com/sug"
    # 处理url携带的参数：封装到字典中
	trans = input('输入你要翻译的句子')
    data = {
        'kw': trans
    }
    # 使用post方式发起请求，该方法会返回一个响应对象
    response = requests.post(url=url,data = data,headers=headers)
    # 获取响应数据，因为服务器返回的是json格式的数据，因此需要用json方法进行解析，注意，必须在确定响应的是json类型才能使用该方法，否则会报错
    page_json = response.json()
    # 存储数据，json.dump方法是存储json格式的方法，因为存储内容有中文，所以要关闭ascii码存储
    fp = open('./trans.json','w',encoding='utf-8')
    json.dump(page_json,fp=fp,ensure_ascii=False)
    print('爬取数据结束')
```

- 示范样例2（爬取豆瓣电影）

```python
import requests
import json
# 指定py文件执行入口
if __name__ == "__main__":
    # UA伪装：将某款浏览器对应的User-Agent封装到一个字典中
    headers = {
        'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.74 Safari/537.36 Edg/99.0.1150.55'
    }
	# 指定url
    url = "https://movie.douban.com/j/chart/top_list"
    # 处理url携带的参数：封装到字典中
    param = {
        'type': 24,
		'interval_id': '100:90',
		'start': 0,
		'limit': 20
    }
    # 使用post方式发起请求，该方法会返回一个响应对象
    response = requests.get(url=url,params=param,headers=headers)
    # 获取响应数据，因为服务器返回的是json格式的数据，因此需要用json方法进行解析，注意，必须在确定响应的是json类型才能使用该方法，否则会报错
    page_json = response.json()
    # 存储数据，json.dump方法是存储json格式的方法，因为存储内容有中文，所以要关闭ascii码存储
    fp = open('./film.json','w',encoding='utf-8')
    json.dump(page_json,fp=fp,ensure_ascii=False)
    print('爬取数据结束')
```

## 数据解析（三种方法选择其中一个掌握就行）

### 基础部分

- 数据解析原理


我们需要的数据都会在html标签或者标签对应的属性中进行存储，所以我们要从中将数据解析出来

- 步骤


1. 进行指定标签的定位
2. 标签或者标签对应的属性中存储的数据值进行提取

- 补充点：图片数据解析

可以通过 `requests.content` 获取二进制形式的图片数据，之后可以直接将数据写入图片文件中，从而获得图片

> 注意：图片的URL必须以图片文件名进行结尾，不能是加密文件

```python
import requests
if __name__ == "__main__"
headers = {
	'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.74 Safari/537.36 Edg/99.0.1150.55'
}
img_src = '图片的src地址'
img_path = '图片存储路径'
img_name = img_src.split('/')[-1]
img_data = requests.get(url=img_src, headers=headers).content

# 注意写入方式是wb，即以二进制形式进行写入
with open(img_path, 'wb') as fp:
	fp.write(img_data)
	print(img_name,'下载成功!!!')
```

### 正则（较难，通用性较强，灵活性较高，新手不建议学）

> 正则表达式语法相关可以参考链接 https://deerchao.cn/tutorials/regex/regex.htm  

python中的正则表达式用法：

```python
import re
# ex为正则表达式,.*?表示匹配尽可能少的内容,()表示提取其中的内容
ex = '<div class="thumb">.*?<img src="(.*?)" alt.*?</div>'		
re.findall(ex,"要匹配的内容",re.S)
```

> python中正则表达式相关参数
>
> | 修饰符 | 描述                                                         | 备注                                                         |
> | ------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
> | re.I   | 使匹配对大小写不敏感                                         | 使正则不区分大小写                                           |
> | re.L   | 做本地化识别匹配                                             |                                                              |
> | re.M   | 多行匹配                                                     |                                                              |
> | re.S   | 使.匹配换行符在内的所有字符                                  | 该修饰符的作用可以理解为将.的作用拓展到整个字符串。如果不使用该参数，正则只会在每一行进行匹配，如果一行没有，就换下一行重新开始匹配，不会跨行匹配 |
> | re.U   | 根据Unicode字符集解析字符。这个标志影响 \w, \W, \b, \B       |                                                              |
> | re.X   | 该标志通过给予你更灵活的格式以便你将正则表达式写得更易于理解。 |                                                              |

### bs4（只能用于python中，上手快）

- 原理

1. 实例化一个BeautifulSoup对象，并且将页面源码数据加载到该对象中
2. 通过调用BeautifulSoup对象中相关的属性或者方法进行标签定位和数据提取

- 环境安装

```python
pip install bs4
pip install lxml	# 数据解析器，是bs4需要的一个第三方库
```

- 对象实例化

将html格式的数据加载到该对象中

```python
# 实例化对象
fp = open('./test.html','r',encoding = 'utf-8')
# 或者 fp = requests(...).text	# 获取网页源码并返回
soup = BeautifulSoup(fp,'lxml')	# 第一个参数为html文本数据
```

- BeautifulSoup对象的相关方法和属性

| 方法                                                         | 说明                                                         | 示例                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `soup.tagName`                                               | 返回第一次出现的标签，标签名称例如a、div、span等。           | `soup.a`，表示返回第一次出现的a标签的内容                    |
| `soup.find(tagName[,属性名1_='属性名称',属性名2_='属性名称',...])` | 返回第一个带有指定属性名和属性值的标签，tagName为标签名字符串，注意一定要用_=而不是=，因为_=表示这是一个属性而不是参数 | `soup.find(div,class_='container')`，表示返回第一个class='container'的div标签的内容 |
| `soup.find_all(tagName[,属性名1_='属性名称',属性名2_='属性名称',...])` | 与find()方法类似，但该方法返回的是符合要求的所有标签的列表   | 略                                                           |
| `soup.select('css选择器')`                                   | 返回的是符合选择器的列表，选择器为CSS的内容                  | 实例略。备注：该方法不仅可以使用ID选择器、类选择器、标签选择器等，还可以使用兄弟选择器，子代选择器等，需要了解的CSS知识较多，入门不建议使用 |
| `定位方法.text/定位方法.get_text()`                          | 获取某一个标签中所有的文本内容（包括子代文本）。定位方法即上方的方法 | `soup.a.text`，获取第一个a标签中的文本内容（包括子代文本）   |
| `定位方法.string`                                            | 获取该标签下直系的文本内容（不包含子代文本）                 | 略                                                           |
| `定位方法['属性名称']`                                       | 获取指定属性名称的内容                                       | `soup.a['href']`，获取第一个a标签中的href属性的内容          |

> 上方的soup即对象实例化后的soup



- 综合示例

```python
import requests
from bs4 import BeautifulSoup as bs	# 为BeautifulSoup设置别名
import lxml

headers = {
	'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.74 Safari/537.36 Edg/99.0.1150.55'
}
target_url = '所要获取的网页的url'
param = {
    ...		# 是否有参数需要视情况分析
}
# 实例化对象
fp = requests.get(url = target_url, headers = headers[, params = param]).text	# 获取网页源码并返回
soup = bs(fp,'lxml')	# 第一个参数为html文本数据
img_data = soup.find_all(img)
saved = ""	# 用于保存标签内容
# 获取数据
for item in img_data:
	saved += (item['src'] + '\n')
# 保存数据
with open('./img_data.csv','w') as fp:
    fp.write(saved)
    print("保存成功")
```

> 纯手写，仅供参考，如果报错根据报错信息修改

### xpath（推荐使用，最常用，通用性最强）

xpath是一门在XML文档中查找信息的语言，python中内置了这门语言

xpath利用了html文档树结构进行查找

> 小提示：使用浏览器打开所要爬取的标签后，点击F12打开开发者工具，使用左上角的标签定位工具定位到所要的标签后，点击右键，会发现复制选项有一个展开选项，里面可以直接复制完整的xpath路径

> 在利用上述工具的情况下，xpath上手最快…

- 原理

1. 实例化一个etree对象，并将需要被解析的页面源码数据加载到该对象中
2. 调用etree对象中的xpath方法结合xpath表达式实现标签的定位和内容的捕获

- 环境安装

```python
pip install lxml	# 只需要这一个包，该包中有etree类
```

- 对象实例化

将html数据加载到etree对象

```python
from lxml import etree

# 加载本地html文档
fp = open('./test.html','r',encoding = 'utf-8')
tree = etree.parse(fp)	# 解析文档字符串

# 加载网页源码
page_text = requests(...).text	# 获取网页源码并返回
tree = etree.HTML(page_text)

# 以上两种对象实例化方法二选一即可

# 调用etree对象的xpath方法
tree.xpath('xpath表达式')
```

- xpath表达式

```python
# 标签定位，下方标签定位方式可结合使用
/	# 一个斜杠表示单个层级，可以用 /html 指定根节点
//	# 两个斜杠表示多个层级，如tree.xpath('//div')表示查找文档中任意位置的div标签
标签名[@属性名="属性值"]		# 属性定位，定位到具有指定属性的标签
标签名[num]	# 索引定位，例如p[1]表示定位到第一个符合查找条件的p标签，注意索引是从1开始的

# 获取文本内容
标签名/text()	# 获取标签的直系文本内容，不包含子代的文本内容
标签名//text()	# 获取标签的所有文本内容，包含子代的文本内容

# 获取属性内容
标签名/@属性名	# 获取标签的指定属性的属性值
```

> 如果没有指定根节点，则将从文档中任意节点开始查找，返回所有符合的结果

```python
tree.xpath('/html/body/div')	# 左边为html文档树写法，返回的是元素对象列表
```

## 反爬机制之验证码识别

验证码是一种反爬机制，因此我们需要识别验证码图片的数据用于模拟登陆操作

识别验证码的操作：利用第三方自动识别

### 自动识别验证码

云打码平台和超级鹰平台提供了较为全面的验证码识别，但是是个付费平台

- 注册流程

在平台注册普通和开发者两种身份的用户

普通用户用于查询用户是否还有剩余题分

开发者用户：

1. 创建一个软件：我的软件->添加新软件->录入软件名称->提交，会产生软件id和密钥
2. 点击开发文档下载示例代码

- 使用流程

1. 将验证码图片进行本地下载
2. 调用平台提供的实例代码进行识别

### 模拟登陆

- 流程

1. 直接向服务器发送登录请求（注意其中的参数）
2. 获取服务器返回的页面
3. 存储数据

> 可以利用响应状态码`requests.post().statuscode`判断是否模拟登陆成功

- cookie

cookie：cookie是在登录成功后服务端发送给客户端用于识别身份的信息，用于记录客户端的登录状态，因此我们可以在发送请求时携带cookie数据，从而使得服务器返回我们想要的结果

> cookie不是唯一一种用于验证登录的信息，还有例如JWT机制等其他方法可以用来识别客户端信息，当前所讲述方法只适用于采用了cookie验证登录的网站

> cookie一般被存放于session对象中，因此可以使用session对象进行模拟登陆post请求的发送（cookie）就会被服务器自动保存于session对象中，之后就可以利用该session对象对服务器发起请求

- 简单示例（下方示例采用了bs4写法且没有添加验证码识别部分）

```python
from lxml import etree
import requests
from bs4 import BeautifulSoup

# step1，预备数据处理
session = requests.Session()	# 创建session对象
headers = {
	'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/99.0.4844.74 Safari/537.36 Edg/99.0.1150.55'
}
page_url = '需要登录的网页URL'
login_url = '需要发送登录请求的ajax地址'
img_src = ''	# 用于保存获取到的图片地址
detail_url = '登录后想要爬取的请求信息'

# step2，获取网站验证码图片并保存
page_text = requests.get(url = page_url, headers = headers).text # 获取网站源码
soup = BeautifulSoup(page_text)		# 将获取到的网页源码转化为BS对象
# 保存验证码的地址，注意：验证码一般唯一，且采用了特定标签属性进行记录，如采用alt、id等
img_src = soup.find(img,alt_="alt值")	
# 保存请求的图片二进制数据
img_content = requests.get(url = img_src, headers = headers).content()
# 将保存的图片二进制数据写入图片文件中
with open('./check.jpg','wb') as fp:
	fp.writr(img_content)
    
# step3，解析图片中的验证码，此处getCodeText为封装好的云打码平台验证码验证函数
result = getCodeText('./check.jpg',验证码类型代码)	

#step4，向网站发送登录请求
# 需要用于post请求的参数
data = {
    'icode': result,	# 验证码识别后的值
    ...		# 其余参数需要具体参考对应的ajax请求格式
}
# 使用session对象发送post请求，使得服务器传递的cookie能够被保存
response = session.post(url=login_url, headers=headers, data=data)
print(response.status_code)	# 打印返回的状态码以查看登录是否成功，如果是200则表示请求成功

# step5，爬取需要获取的登录后信息
# 发送请求，下方的post也可以是get，解析数据的方式也可以是json()或者content()，具体视情况而定
detail_page_text = session.post(url=detail_url, headers=headers).text
with open('保存的路径/文件名.文件后缀','w',encoding='utf-t') as fp:
    fp.write(detail_page_text)
```

## 反反爬策略之代理IP

某些服务器可能会通过识别IP的访问频次来判断是否是爬虫，如果是则会直接封IP。而代理IP则是针对反反爬策略的一种有效的反反爬策略

- 什么是代理

代理指代理服务器。代理服务器相当于客户端和服务端的一个中间站，使得服务器识别的IP为代理服务器的IP

- 代理的作用

1. 突破自身IP访问的限制（简称：翻墙…）
2. 隐藏自身真实IP（包括自身的地理位置）

- 代理相关的网站

部分网站有提供免费代理，但是那速度……

> 所以别看了，代理都是要钱的，不过学生可以白嫖GlaDOS的代理

1. 快代理
2. 西祠代理
3. www.goubanjia.com

- 代理ip的类型
  - http：应用到http协议对应的url中
  - https：应用到https协议对应的url中

> 科普一下：之所以有这种类型区别，是因为有浏览器等有安全策略这种安全措施，即处安全性的考虑，不同协议的请求是不能相互处理的，在服务器中甚至需要利用到跨域技术才能成功响应数据给服务器

- 代理ip的匿名度

1. 透明：服务器知道该次请求使用了代理，也知道请求对应的真实IP
2. 匿名：服务器知道该次请求使用了代理，但不知道真实IP
3. 高匿：服务器既不知道该次请求使用了代理，也不知道真实IP

- 代理服务器的使用

```
requests.get(url=url, headers=headers, proxies={"代理服务器类型":"代理服务器ip地址"})	# 代理服务器类型指http、https等
```

## 高性能的异步爬虫

- 什么是异步

异步可以简单理解为不同步，表现为发送请求后可以不用等待服务器返回结果，而是先进行下一步的处理，等到服务器返回结果后会自动调用回调函数进行处理

> python是一种解释型语言，特性为单线程，即如果不指定异步操作的话则只有处理完当前操作后才会继续进行后续操作

- 异步爬虫的目的

在爬虫中使用异步实现高性能的数据爬取操作，避免了因为服务器响应速度慢而带来的时间损失

- 异步爬虫的方法

1. 多线程、多进程（不建议使用，此处不提及）
   1. 好处：可以为相关阻塞操作单独开启线程或者进程，从而使阻塞操作异步执行
   2. 坏处：因为CPU的线程处理是有限的，因此无法无限制的开启多线程或者多进程
2. 进程池、线程池（适当使用）
   1. 好处：我们可以降低系统对进程或者线程创建和销毁的频率，从而很好的降低系统的开销
   2. 坏处：池中线程和进程数量是有上限的，如果达到了上限，执行效率很会很慢
3. 单线程+异步协程（python3.6后才支持，推荐使用）

### 进程池、线程池

- 使用方式示例

```python
from multiprocessing.dummy import Pool	# 导入线程池模块对应的类

# 实例化线程池对象
# 4表示线程池中线程数量，可以根据需要增加或者减少，线程数量不是越多越好，而是需要根据需要处理的程序进行分析
pool = Pool(4)	

# 第一个参数：函数参数，传入可能会发送阻塞的函数
# 第二个参数：列表参数，表示需要传递进第一个参数函数中依次进行处理的数据列表
pool.map(func, list)	# 此时同一个函数可以由4个线程进行处理

pool.close()	# 关闭线程池
pool.join()		# 让主线程等待线程池结束后才结束整个进程
```

> 线程池使用原则：只处理阻塞且较为耗时的操作，普通的get或者post请求可以不用线程池，但如果是下载的请求则一般需要采用线程池

### 异步协程

- 名词解释

| 名词       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| event_loop | 事件循环，相当于一个无限循环，我们可以 把一些函数注册到这个事件循环上，当满足某些条件的时候，函数就会被循环执行 |
| coroutine  | 协程对象，我们可以将协程对象注册到事件循环中，他会被事件循环调用。我们可以使用async关键字来定义一个方法，这个方法在调用时不会立即被执行而是返回一个协程对象 |
| task       | 任务对象，它是对协程对象的进一步封装，包含了任务的各个状态，主要是用于查看协程对象的运行状态和绑定回调函数 |
| future     | 表示将来执行或还没有执行的任务，实际上和task没有本质区别     |
| async      | 函数修饰符，用于定义一个协程                                 |
| await      | 用来挂起阻塞方法的执行                                       |

- 协程的实现步骤

1. 引入asyncio模块
2. 定义协程（即使用async修饰符修饰一个函数）
3. 创建回调函数（可选）
4. 实例化协程对象
5. 创建事件循环对象
6. 基于loop创建task对象或创建future对象
7. 为任务对象绑定回调函数
8. 将task对象注册到loop中，然后启动loop

- 协程实现示例一

> 协程一次只创建一个，因此可以在循环中重复定义协程对象

```python
# step1，引入asyncio模块
import asyncio

# step2，定义协程
async def request(url) :
    print('正在请求的url是', url)
    print('请求成功', url)
    return url
# step3，创建回调函数，task为任务对象
def callback_func(task):
    print(task.result())	# task.result()中保存了协程的返回值，此处的返回值即为url

# step4，实例化协程对象
# async修饰的函数，调用之后返回的是一个协程对象
c = request('www.baidu.com')

# step5，创建一个事件循环对象
loop = asyncio.get_event_loop

# step6，基于loop创建task对象，并将协程对象传递进去，也可以创建future对象
task = loop.create_task(c) # 或 task = asyncio.ensure_future(c)

# step7，绑定回调函数
# 注意绑定回调函数时不用传参，默认就是将task任务对象作为参数传递进去
task.add_done_callback(callback_func)

# step8，将task对象注册到loop中，然后启动loop，此时协程对象内部的方法才正式被执行
loop.run_until_complete(task)
```

> task对象被创建后，可以通过print(task)的方式查看内部协程的状态
>
> 如果不想使用task对象查看状态的话，可以跳过step5，直接在step6中将协程对象c传递进去，这样也可以执行，但是就无法绑定回调函数

- 协程实现示例二

> 该示例利用循环定义多个任务对象并运行

```python
import asyncio
import time

async def request(url):
    print('正在下载', url)
    # 休眠2s，注意此处不能使用time.sleep(2)，否则会阻塞进程，使异步协程无法实现
    # 当在asyncio中遇到阻塞操作必须进行手动挂起
    await asyncio.sleep(2)	
    print('下载完成', url)
    
urls = [
    'www.baidu.com',
 	'www.sougou.com',
    'www.goubanjia.com'
]

# 任务列表：用于存放多个任务对象
stasks = []
for url in urls:
    c = request(url)
    task = asyncio.ensure_future(c)
    stasks.append(task)
loop = asyncio.get_event_loop()
# 注意：下方为固定写法，不能直接将stasks传递进去，而是利用asyncio.wait(stasks)间接传递进去
loop.run_until_complete(asyncio.wait(stasks))
```

> 注意：在异步协程中如果出现了同步模块相关的代码，那么就无法实现异步，即async后只能跟异步程序或者有`__await__`属性的对象。
>
> await必须在异步程序中使用，且await后面修饰的也必须为异步程序，其本质上是将原异步程序挂起，然后去执行await后的异步程序或者其他操作，当挂起条件消失后，则马上回到原异步程序中执行之前未执行的后续操作

> 注意：`requests.get()`或`requests.post()`也是同步请求，因此不能在异步程序中使用，否则会阻塞程序，使异步程序变成同步程序。
>
> 解决方法：可以使用aiohttp模块代替requests模块

### `aiohttp`模块

```python
import aiohttp
import asyncio

async def get_page(url):
    # 利用session对象发起请求
    async with aiohttp.ClientSession() as session:
        headers = {...}
        param = {...}
        # 下方的代理地址中不是使用字典，而是直接使用字符串
        async with await session.get(url=url,headers=headers,params=param,proxies='代理地址字符串') as response:
            # 注意：获取相应数据操作之前一定要使用await进行手动挂起
            page_text = await response.text()
            print(page_text)
task = []
for url in urls:
    c = get_page(url)
    task = asyncio.ensure_future(c)
    tasks.append(task)
loop = asyncio.get_envent_loop()
loop.run_until_complete(asyncio.wait(tasks))
```

## selenium模块

### 什么是selenium模块

selenium模块是基于浏览器自动化的一个模块，可以理解为有一个机器人在帮你操作

### 环境安装

```python
pip install selenium
下载某一个浏览器的驱动程序（例如chromedriver）
```

### 使用示例

```
from selenium import webdriver
bro = webdriver.Chrome(executable_path='')	# 浏览器驱动程序目录
bro.get('url地址')	# 发送get请求并将返回的源码直接保存到bro对象中，模拟用户在浏览器地址栏中输入url地址的行为
...	# 执行相关行为
```

### selenium常用方法

| 方法名                                          | 描述                                                         |
| ----------------------------------------------- | ------------------------------------------------------------ |
| 标签定位系列.find_...，见下                     |                                                              |
| `bro.find_element_by_id('ID属性值')`            | 通过标签id查找标签，返回所查找的标签                         |
| `bro.find_element_by_css_selector('CSS选择器')` | 通过CSS选择器查找标签，返回所查找的标签                      |
| ...                                             | 其他常用的标签定位方法与js中类似，因此不一一解释             |
| 标签交互系列见下                                |                                                              |
| `定位标签.send_keys('要输入的值')`              | 模拟浏览器输入功能，在所定位的标签中进行输入                 |
| `定位标签.click()`                              | 模拟浏览器点击功能，点击所选择的标签                         |
| `定位标签.location`                             | 这是一个属性，以对象形式返回标签的左上角坐标，可以利用location['x']获取x坐标 |
| `定位标签.size`                                 | 这是一个属性，以对象形式返回标签的大小，可以利用size['width']获取宽度 |
|                                                 |                                                              |
| js代码执行                                      |                                                              |
| `bro.execute_script('js代码')`                  | 在浏览器当前页面执行js代码                                   |
| 前进回退                                        |                                                              |
| `bro.back()`                                    | 浏览器页面回退                                               |
| `bro.forward()`                                 | 浏览器页面前进                                               |
| 截图                                            |                                                              |
| `bro.save_screenshot('图片名')`                 | 截图，传入的字符串参数为截图的保存位置和图片名               |
| 关闭浏览器                                      |                                                              |
| `bro.quit()`                                    | 关闭浏览器，一般要配合sleep()使用，否则可能会出现数据未抓取完毕浏览器就已经关闭的情况 |

> 更多的方法见文档

### selenium与iframe

如果定位的标签是存在于iframe标签中，则必须通过如下操作进行标签定位

```python
bro.switvh_to.iframe('iframeResult')	# 切换浏览器标签定位的作用域
...	# 之后按照之前的方法进行操作即可
```

> 原理：原本的作用域是在外部的iframe中，而该操作是切换作用域操作

### selenium与动作链

- 步骤

1. 导入包
2. 实例化动作链对象
3. 进行动作链操作

- 实例

```python
from selenium import webdriver
from selenium.webdriver import ActionChains

bro = webdriver,Chrome(executable_path='')
bro.get()

# 实例化动作链对象
action = ActionChains(bro)

# 点击并长按指定的标签
action.click_and_hold(标签定位语句)

# 移动对应的偏移量
action.move_by_offset(x坐标偏移量, y坐标偏移量)

# 执行动作链操作
action.perform()

# 释放动作链，此处表现为松开标签
action.release()
```

### 无头浏览器和规避检测

无头浏览器是一个属于，即无可视化界面的浏览器，在此处具体操作为关闭selenium操作过程时候的可视化界面

除了使用谷歌外，还可以使用phantomJs，但是phantomJs已经停止维护了，不是很建议使用

> 由于无头+selenium是一种很常见的爬虫手段，所以很多门户网站都针对此设定了反爬机制，因此我们需要设立反反爬策略进行规避

无头和规避检测代码示例如下，使用时直接将下方代码粘贴于爬虫代码前方即可

```python
from selenium import webdriver
# 实现无可视化界面
from selenium.webdriver.chrome.options import Options
# 实现规避检测
from selenium.webdriver import ChromeOptions

# 实现无头
chrome_option = Options()
chrome_option.add_argument('--headless')
chrome_option.add_argument('--disable-gpu')

# 实现规避检测
option = ChromeOptions()
option.add_experimental_option('excludeSwitches',['enable-automation'])

bro = webdriver.Chrome(executable_path='浏览器驱动安装地址', chrome_options=chrome_option, options=option)

bro.get('网页URL地址')
```

> 利用selenium模块模拟登陆时，需要对selenium打开的页面的验证码进行截图，否则如果直接对图片的src进行请求会出现当前登录请求与验证码不匹配

### 补充知识-图片裁剪

- 所需库

```python
from PIL import Image
```

- 使用方法

```python
from PIL import Image

rangle = (int('要裁剪的图片的左上角x坐标'),int('要裁剪的图片的左上角y坐标'),int('要裁剪的图片的右下角x坐标'),int('要裁剪的图片的右下角y坐标'))
i = Image.open('图片文件路径')
code_img_name = './code.png'	# 图片保存地址
frame = i.crop(rangle)
frame.save(code_img_name)
```

## scrapy框架

### 什么是框架

框架就是集成了很多功能并且具有很强通用性的一个项目模板

初学者只需要学习框架封装的各种功能的详细用法即可，进阶才需要了解框架的底层实现



### 环境安装

- mac或linux下

```python
pip install scrapy
```

- windows下

```
pip install wheel
#下载twisted	下载地址：https://www.lfd.uci.edu/~gohlke/pythonlibs/#twisted
#安装twisted
#文件下载完成后，在文件的保存位置打开终端，运行如下指令
pip install  Twisted‑20.3.0‑cp39‑cp39‑win_amd64.whl # 后面那一大串文字就是下载的文件名，其中39代表了是3.9版本的python
pip install pywin32
pip install scrapy
# 测试：在终端中输入scrapy指令，没有报错即表示安装成功
```

> 注意：在整个过程中终端中不能有任何报错信息出现，即终端中不能有红色信息出现，否则就是安装失败

### scrapy准备工作

注意：以下操作均需要在终端中进行

#### 创建工程

```
scrapy startproject 工程名
```

> 工程名最好是全英文的，不然容易出错
>
> 创建完后会发现当前文件夹下多了一个文件夹，其中有spiders文件夹，该文件夹下settings.py文件是工程的配置文件

#### 配置settings.py文件（待补充）



#### 在spiders子目录中创建爬虫文件

1. 在终端中用cd命令跳转到spiders目录中
   1. `cd 工程名/工程名/spiders`
2. 在跳转后的终端中输入如下命令创建新的爬虫文件
   1. `scrapy genspider 新建爬虫文件的名字 要爬取的网址`
   2. 例如：`scrapy genspider firstspider www.baidu.com`

进行完上述步骤后在spiders文件夹中会出现一个新的py文件，该文件中的代码如下（下面是我写了备注的版本）

```python
import scrapy

class FirstspiderSpider(scrapy.Spider):
	# 爬虫文件的名称，即爬虫源文件的一个唯一标识
    name = 'firstspider'
    # 允许的域名：用来限定start_urls列表中哪些url可以进行请求发送，通常不会使用这个属性
    # allowed_domains = ['www.baidu.com']
    # 起始的url：该列表中存放的url会被scrapy自动进行请求的发送
    start_urls = ['http://www.baidu.com/']

    def parse(self, response):
        pass
```

#### 工程文件之间的互相导入

例如在爬虫文件中导入items.py文件的某个类

```
from 工程名.items import 类名
```

#### 执行工程

在spiders文件夹下的终端中输入如下命令可以执行工程

```python
scrapy crawl spiderName
```

### scrapy操作

#### 标签定位

```
response.xpath('xpath语言')
```

> 注意：该方法返回的是列表，但列表元素是selector类型的对象，可以使用extract()方法提取selector对象中data参数存储的字符串提取出来

> extract()方法可以对单个selector对象使用，也可以对selector对象组成的列表使用，如果对列表使用，则返回每个selector对象中data参数的字符串列表，之后可以利用join方法将列表转化成字符串
>

> 如果保证列表中只有一个列表元素，则可以使用extract_first()，用于提取列表中第0个列表元素的data参数，如果有多个元素则不能使用

#### 持久化存储

持久化存储有两种方案：基于终端指令和基于管道

##### 基于终端指令

- 操作步骤

1. 将所有的数据保存到一个变量中，然后将其作为函数的返回值返回

2. 在终端中输入`scrapy crawl 当前爬虫文件名称 -o ./需要保存的文件名.文件后缀`


- 注意

终端中只能将文件保存为json、jsonlines、jl、csv、xml、marshal、pickle这几种文件的格式

- 好处

简洁高效便捷

- 缺点

局限性强，只能存储到指定后缀的文件中

##### 基于管道

> 在使用该方法前，需要先在配置文件中开启管道

- 操作步骤

1. 数据解析，将解析的数据封装存储到item类型的对象
2. 在items.py文件中的item类中定义要接受的相关属性
3. 将解析的数据封装到存储到item类型的对象（使用`yield item` 语法进行提交）
4. 将item类型的对象提交给管道进行持久化存储操作
5. 在管道类（该类定义位于pipelines中）的process_item方法中将接收到的item对象中存储的数据进行持久化存储操作

- 操作示例

爬虫文件：

```python
import scrapy
# 我的工程名就叫做project...所以导入方式如下
from project.items import ProjectItem

class FirstspiderSpider(scrapy.Spider):
    # 爬虫文件的名称
    name = 'firstspider'
    # 允许的域名
    # allowed_domains = ['www.baidu.com']
    # 起始的url
    start_urls = ['http://www.baidu.com/']
    
    def parse(self, response):
        result = response.xpath('xpath路径')
        item = ProjectItem()
        # test属性必须在items.py文件中先声明
        item['test'] = ''.join(result.extract())
        yield item
```

pipelines.py文件：

```python
class ProjectPipeline:
    fp = None
    # 重写父类的两个方法，使该方法只在开始爬虫的时候被调用一次
    def open_spider(self, spider):
        print('开始爬取...')
        self.fp = open('./test.txt', 'w', encoding='utf-8')
    
    def close_spider(self,spider):
        print('结束爬虫')
        
    # process_item是专门用来处理item类型对象的
    # 该方法可以接受爬虫文件提交过来的item对象
    # 该方法每接收到一个item就会被调用一次
    def process_item(self, item, spider):
        test = item['test']
        # 将test中的数据写入已经打开的文件
        self.fp.write(test)
        return item
```

items.py文件：

```python
import scrapy

class ProjectItem(scrapy.Item):
    # 定义test属性
    test = scrapy.Field()
```

### scrapy五大核心组件(了解)

调度器、管道、引擎、下载器、Spider

引擎（Scrapy）

​	用来处理整个系统的数据流处理，触发事务

调度器（Scheduler）

​	用来接受引擎发过来的请求，压入队列中，并在引擎再次请求的时候返回

下载器（Downloader）

​	用于下载网页内容，并且将网页内容返回给蜘蛛（Scrapy下载器是建立在twisted这个高效的异步模型上的）

爬虫（Spider）

​	爬虫主要是干活的，用于从特定的网页中

### 请求传参

请求传参即传入参数给下一个请求，主要思路为调用一次请求，然后将响应数据传递给回调函数

应用场景：请求传参主要用于处理爬取数据不在同一页的情况

请求传参的用法

```python
yield scrapy.Request(传入URL参数,callback=self.自定义方法)	# 该方法用于发起一个请求，请求结束后会调用回调函数，并将响应传递给回调函数中的response参数
```

> 注意：自定义的方法中的参数必须为(self, response)
>

### 图片爬取

scrapy提供了ImagePipeline类用于对img的src属性进行解析

我们只需要提交图片的src属性到ImagesPipeline管道类，管道就会自动对图片的src进行请求发送来获取图片的二进制数据，并且会帮我们进行持久化存储


