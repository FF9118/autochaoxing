# autochaoxing

超星学习通无界面刷课脚本，通过selenium+bs4+正则处理，实现看视频+章节测试全自动，无需打开浏览器即可刷课（还有docker版本哦:smile:）
<hr/>

## 使用

**Windows**：

- 安装chrome浏览器以及相对应的chromedriver，并**将chromedriver放在项目目录下**
  
    - [chrome浏览器下载地址](https://www.google.cn/chrome/)，[chromedriver下载地址](http://npm.taobao.org/mirrors/chromedriver/)或者[这里](http://chromedriver.storage.googleapis.com/index.html)，注意版本对应
    
- 安装python3和pip，[python官网](https://www.python.org)

- 安装依赖：命令行执行<br/>
`pip install -r requirements.txt`
- 考虑到国内直接pip下载的速度，这边建议运行一下这个命令<br/>
`pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple`
  
- 在**logindata_phone.txt**或**logindata.txt**中按提示填写登录信息，并把提示信息删除

- 查看帮助信息 ，选择合适的参数开始刷课<br/>
  `python autocx.py -h`     
  
- 示例：以16倍速(-r)全自动模式(-m)运行脚本，并指定自动提交限制(-n)为2<br/>
`python autocx.py -m fullauto -r 16 -n 2`


**Linux**：可以配环境运行py，也可以使用**docker**:point_down:

**如果有帮到你的话请赏颗:star:吧**

<br/>

## 关于autocx(Docker)

autocx是autochaoxing的**Docker**版本，主要由[KimJungWha](https://github.com/KimJungWha)制作了这个开箱即用的镜像<br/>
详细信息和说明请[移步项目地址](https://hub.docker.com/r/kimjungwha/autocx)<br/><br/>
[Rainy season boy](https://github.com/chenaidairong)与[KimJungWha](https://github.com/KimJungWha)分别制作了**Linux下自动安装docker与运行docker镜像的sh脚本**，详见[issues#8](https://github.com/Luoofan/autochaoxing/issues/8)，欢迎测试与反馈

<br/>

## 功能支持

- [x] **无浏览器界面**，只有控制台执行界面
- [x] 充分的**交互**
- [x] **多账号多开**
- [x] 支持所有机构用户登录运行
- [x] 自动刷视频(包括页面内**多视频**)，静音播放
- [x] 解决视频内弹出的试题（单选、多选）
- [x] 支持ppt、音频任务点
- [x] 自动答章节测试题（**单选、多选、判断**）
- [x] **多种模式：全自动，单课程自动，控制模式**
- [x] **视频倍速**
- [x] 自定义查题API优先级
- [x] 自定义章节测试自动提交限制
- [x] 只看视频不答题

<br/>

## 暂不支持&ToDo

 - [ ] 【非视频、章节测试、ppt、音频】的任务点
 - [ ] 【非选择判断类题目】的自动答题
 - [ ] 自动考试
 - [ ] ~~自动填写登录验证码~~（手机登录不需要填写）

<br/>

## 如果想亲手写刷课脚本 或者遇到问题 可以先来[FAQ](https://github.com/Luoofan/autochaoxing/blob/master/doc/FAQ.md)看看哦:blush:

<br/>

## 关于题库与考试

 - 考试因为考虑到直接无界面完成不放心，所以暂未提供支持，考试时可使用**查题程序**辅助

 - 原先的题库服务器来源于GreasyFork上**wyn大佬**，现在的题库接口源于多方，十分感谢！


<br/>

## 更新（**如果有帮到你的话请赏颗:star:吧**）

- 详细更新信息请见-->[FAQ](https://github.com/Luoofan/autochaoxing/blob/master/doc/FAQ.md)
- 2020-5-4：
    - 发布查题程序（`exe`）  [通道](https://github.com/Luoofan/autochaoxing/releases)
- 2020-4-29：
    - 支持ppt、音频任务点
- 2020-4-24：
    - 新增**全局答题设置**选项`-n(--num)`  
        - 默认值：5                                  可选值：0，1，2 ......
        - 自动答题时,如果 未找到答案的题目数量 达到num值,则暂时保存答案,不进行自动提交
    - 支持**自定义查题API优先级** 
- 2020-4-6：

  - 发布了Docker2.0版本（有docker的小伙伴可以直接在docker里多开sk啦）
- **2020-4-2**：:star:

  - **发布了2.0版本**
  - 新增**模式选择**：`-m(--mode)`
    - `single`:      单课程自动模式——选择课程,自动完成该课程(默认启动参数，可不填写)
    - `fullauto`:  全自动模式——自动遍历全部课程,无需输入
    - `control`:    单课程控制模式——选择课程并选择控制章节,自动完成选定章节前的任务点
  - 新增**视频倍速**：`-r(--rate)`  默认1倍速
    - [0.625,16]   全局倍速设置——在选定模式的全局范围内开启该倍速
  - 代码简单**重构**，执行**优化**：将原有功能封装，想*亲自写脚本*的童鞋可以关注这点哦 :point_left:
  - 提高**容错率**(遇到未完成的任务点会暂时跳过,登录异常采用备用登录方案)
  - 更改原播放视频部分的模拟操作为js操作，提高程序运行稳定性
  - 可以通过 `-h(--help)`选项查看帮助信息，`-v(--version)`选项查看版本信息
  - 运行异常提交服务器—以便尽快debug
  
----

- 2020-3-16:
  
  - 由[KimJungWha](https://github.com/KimJungWha)制作了**Docker版本**，并发布到了[DockerHub](https://hub.docker.com/r/kimjungwha/autocx)
  
- 2020-3-15：

  - 新增了在**无图形界面的linux终端**下运行的脚本，需要工作目录下有`viu`，[viu:终端显示图片](https://github.com/atanunq/viu)

- 2020-3-5：

  - 发布1.0版本

<br/>

## 免责声明

autochaoxing为本人python学习交流的开源非营利项目，仅作为程序员之间相互学习交流之用，使用需严格遵守开源许可协议，严禁用于商业用途。个人或者组织，机构如果使用本项目产生的各类纠纷，法律问题，均由其本人承担。对一切非法使用所产生的后果，本人概不负责。
