# 七、 `Python` 计算生态

1. 标准库：`turtle` 库（必选）、`random` 库（必选） 、`time` 库（可选）。
2. 基本的 `Python` 内置函数。
3. 第三方库的获取和安装。
4. 脚本程序转变为可执行程序的第三方库：`PyInstaller` 库（必选）。
5. 第三方库：`jieba` 库（必选）、`wordcloud` 库（可选）。
6. 更广泛的 `Python` 计算生态，只要求了解第三方库的名称，不限于以下领域：网络爬虫、数据分析、文本处理、数据可视化、用户图形界面、机器学习、Web 开发、游戏开发等。

## 库的使用

- `import <库名>`
- `import <库名> as <别名>`
- `from <库名> import <函数名>`

建议不直接引入函数，代码多了，容易造成误解

## 一些注意

词云的
- scipy 1.3.0 后不再支持 `scipy.misc.imread` 了
    - 使用 `imageio.imread` (`pip install imageio`)

## 生态

### 数据处理

- 数据分析
    - `NumPy` N维数组
    - `Pandas` 数据分析功能库
    - `SciPy` 数学、科学和工程计算功能库
- 数据可视化
    - `Matplotlib` 二维
    - `Seaborn` 统计类数据可视化
    - `Mayavi` 三维
- 特定格式处理
    - `PyPDF2` PDF
    - `NLTK` 自然语言文本处理：分类、标记、语法句法、语义分析
    - `Python-docx` Word文件
- 机器学习
    - `Scikit-learn` 机器学习方法工具集
    - `TensorFlow`
    - `MXNet` 基于神经网络的深度学习计算框架

### 网络
- 爬虫
    - `Requests` 最友好的网络爬虫功能库
    - `Scrapy` 优秀的网络爬虫框架
    - `pyspider` 强大的Web页面爬取系统
- 信息提取
    - `Beautiful Soup` HTML和XML的解析
    - `Re` 正则表达式解析和处理
    - `Python-Goose` 提取文章类型Web页面
- 网站开发
    - `Django` Web应用框架，大型网站：路由+模板+数据库
    - `Pyramid` 中规模
    - `Flask` 微框架
- 网络应用
    - `WeRoBot` 微信公众号开发框架
    - `aip` 百度AI开放平台接口

### 交互
- 图形界面
    - `PyQt5` Qt开发框架的Python接口
    - `wxPython` 跨平台GUI开发框架
    - `PyGObject` 使用GTK+开发GUI的功能库
- 游戏开发
    - `PyGame` 简单的游戏开发
    - `Panda3D` 3D游戏引擎
    - `cocos2d`
- VR
    - `VR Zero`: 树莓派VR
    - `Vizard`: 基于Python的通用VR开发引擎
    - `pyovr`: 针对Oculus VR设备的Python开发库
