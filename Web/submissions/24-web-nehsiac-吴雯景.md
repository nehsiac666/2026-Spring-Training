1. 浏览器开发者工具（F12）

![image-20260418175032989](C:\Users\wz371\AppData\Roaming\Typora\typora-user-images\image-20260418175032989.png)

2. Hackbar插件

![屏幕截图 2026-04-18 183007](C:\Users\wz371\Desktop\Captures\屏幕截图 2026-04-18 183007.png)

3.burpsuite community 安装

![image-20260419172459236](C:\Users\wz371\AppData\Roaming\Typora\typora-user-images\image-20260419172459236.png)

4.Yakit 安装

![image-20260419125413302](C:\Users\wz371\AppData\Roaming\Typora\typora-user-images\image-20260419125413302.png)

5.AI工具

![image-20260419125755615](C:\Users\wz371\AppData\Roaming\Typora\typora-user-images\image-20260419125755615.png)

6.dirsearch安装

![image-20260419201622209](C:\Users\wz371\AppData\Roaming\Typora\typora-user-images\image-20260419201622209.png)

**第一题gift_F12（前端源码泄露）**

**考点**

前端代码 / JS 脚本中的 flag 泄露，核心是利用浏览器开发者工具查看网页源码。

**解题思路**

题目标题直接提示了用F12（浏览器开发者工具），flag 被直接写在网页的 JavaScript 脚本中，无法在页面直接看到，只能通过查看源码获取。

**分步操作**

1. 访问题目靶机环境：打开题目给的靶机链接，页面一般显示倒计时界面。
1. 脱离平台嵌套：复制靶机链接，在浏览器新标签页中独立打开（避免平台 iframe 嵌套导致看不到完整源码）。
1. 查看完整源码：在靶机页面按快捷键 Ctrl + U，直接打开网页的全部原始代码。
1. 定位 flag：按 Ctrl + F 搜索 flag，找到 JS 代码中的 flag 变量值：We1c0me_t0_WLLMCTF_Th1s_1s_th3_G1ft。
1. 按格式提交：套上题目要求的NSSCTF{}格式，提交NSSCTF{We1c0me_t0_WLLMCTF_Th1s_1s_th3_G1ft}。

![屏幕截图 2026-04-19 194345](F:\CTF\屏幕截图 2026-04-19 194345.png)

![屏幕截图 2026-04-19 194303](F:\CTF\屏幕截图 2026-04-19 194303.png)

**第二题（路径泄露）**

**考点**

利用网站robots.txt文件泄露禁止爬虫访问的隐藏路径，flag 通常藏在这些路径中。

**解题思路**

robots.txt是网站给搜索引擎的爬虫协议文件，里面会写Disallow:字段，禁止爬虫访问某些路径，而 CTF 题中这些路径就是 flag 的藏身之处。

**分步操作**

1. 访问题目靶机环境：打开题目给的靶机链接，记录完整地址（含端口号，如http://xxx:端口/）

2. 访问robots.txt：在靶机地址后拼接/robots.txt，访问完整地址：http://xxx:端口/robots.txt。

3. 读取隐藏路径：文件中会显示Disallow: /xxx.php，记录禁止访问的路径。

4. 访问隐藏路径：在靶机地址后拼接路径，如http://xxx:端口/xxx.php，打开页面直接获取 flag。

5. 提交答案：将获取到的flag 输入提交框提交即可。

   ![屏幕截图 2026-04-19 195617](F:\CTF\屏幕截图 2026-04-19 195617.png)

![屏幕截图 2026-04-19 195703](F:\CTF\屏幕截图 2026-04-19 195703.png)

![屏幕截图 2026-04-19 195824](F:\CTF\屏幕截图 2026-04-19 195824.png)

**第三题（GET 请求传参）**

**考点**

HTTP GET 请求的 URL 参数传参，PHP 后端通过$_GET[]接收参数，判断参数值后返回 flag。

**解题思路**

题目 PHP 代码逻辑为：接收 URL 中的moe参数，当参数值为flag时输出 flag，否则仅显示源码。因此需要构造带正确参数的 GET 请求触发条件。

分步操作

1. 访问题目靶机环境：打开题目给的靶机链接，页面会显示 PHP 源码。

2.  分析源码逻辑：源码中包含$moe = $_GET['moe']; if ($moe == "flag") {echo $flag;}，明确需要传递moe=flag的 GET 参数。

3. 构造 GET 请求：在靶机地址后拼接参数，格式为http://靶机地址/?moe=flag。

4. 访问获取 flag：访问构造好的地址，页面会直接显示 flag：NSSCTF{W3lc0m3_t0_M03CTF_2021_G3T_St4rt3r!}。

5. 提交答案：将 flag 输入提交框完成验证。

   ![屏幕截图 2026-04-19 200945](F:\CTF\屏幕截图 2026-04-19 200945.png)

![屏幕截图 2026-04-19 201035](F:\CTF\屏幕截图 2026-04-19 201035.png)

**关于Linux的使用**

下载VMware

![image-20260419203821229](C:\Users\wz371\AppData\Roaming\Typora\typora-user-images\image-20260419203821229.png)

创建虚拟机并在其中下载Ubuntu

![image-20260419204340637](C:\Users\wz371\AppData\Roaming\Typora\typora-user-images\image-20260419204340637.png)

![image-20260419203936930](C:\Users\wz371\AppData\Roaming\Typora\typora-user-images\image-20260419203936930.png)

**Linux基础命令学习**

以下为Linux常用基础指令，包含命令、核心作用及实操实例，表格清晰易懂，适合入门学习：

| 命令 | 核心作用 | 实操实例 |
| :--- | :--- | :--- |
| **ls** | 查看目录文件 | `ls`、`ls -l`、`ls -a` |
| **cd** | 切换目录 | `cd /home`、`cd ..`、`cd ~` |
| **pwd** | 查看当前路径 | `pwd` |
| **mkdir** | 创建目录 | `mkdir test`、`mkdir -p a/b/c` |
| **rm** | 删除文件/目录 | `rm 1.txt`、`rm -rf test` |
| **touch** | 创建空文件 | `touch demo.txt` |
| **cp** | 复制文件/目录 | `cp 1.txt /tmp`、`cp -r dir1 dir2` |
| **mv** | 移动/重命名 | `mv 1.txt ./test`、`mv old.txt new.txt` |
| **cat** | 查看文件内容 | `cat 1.txt` |
| **more** | 分页查看大文件 | `more log.txt` |
| **less** | 高级分页查看 | `less log.txt` |
| **head** | 查看文件开头 | `head -n 5 1.txt` |
| **tail** | 查看文件末尾 | `tail -n 3 1.txt`、`tail -f log.txt` |
| **clear** | 清空终端 | `clear` |
| **whoami** | 查看当前用户 | `whoami` |
| **hostname** | 查看主机名 | `hostname` |
| **find** | 查找文件/目录 | `find ./ -name "*.txt"` |
| **grep** | 文本搜索 | `grep "error" log.txt` |
| **chmod** | 修改权限 | `chmod 755 test.sh` |
| **sudo** | 管理员权限执行 | `sudo apt update` |
| **exit** | 退出终端 | `exit` |
| **ping** | 测试网络连通 | `ping www.baidu.com` |

**学习总结**

一、三道题核心考点

1.gift_F12：前端源码泄露
flag 藏在网页 JS 代码里，按Ctrl+U看完整源码就能找到。

2.robots.txt：路径泄露
访问/robots.txt，看Disallow后面的隐藏路径，直接访问拿 flag。

3.GET：GET 请求传参
看 PHP 源码，用?参数名=值的格式构造 URL，触发条件输出 flag。

二、通用解题步骤

1.把靶机链接复制到新标签页打开，脱离平台嵌套。

2.按Ctrl+U看源码，搜flag关键字。

3.尝试访问/robots.txt、/flag.php等常见路径。

4.分析源码里的$_GET[]，构造带参数的 URL 访问。
三、避坑要点
1.不要在 CTF 平台 iframe 里直接按 F12，看不到靶机源码。
2.访问路径 / 文件时，必须带上端口号。
3.GET 传参要注意参数名、值和?的格式，不能写错。
