pylot
=====

Python test tool. Forked from http://pylot.org


教程：http://www.cnblogs.com/numbbbbb/archive/2013/04/19/3029959.html

首先需要配置一下testcases.xml这个文件。这个文件包含了需要测试的目标url以及具体的测试内容。

　　大家打开testcases.xml之后可以看到两个<case>......</case>，因为我们只是要一个简单的实例，所以我们把第二个<case>....</case>删掉，然后把第一个<case>....</case>里面的<url></url>改成你需要测试的url。我的就是<url>http://www.langman1dian.com</url>。改好之后整个文章内容是这样的

复制代码
<testcases>
    <!-- SAMPLE TEST CASE -->
    <case>
        <url>http://www.langman1dian.com</url>
    </case>
    -->
</testcases>
复制代码
 

　　好了，保存关闭。

　　然后我们就可以开始测试了。

　　什么？你说太快了？没错，就是这么快！

　　在命令行输入

python pylot -a 50
　　然后回车，你就可以看到测试开始了。

　　这里的 -a 参数就是设置用户数，也就是你想要模拟同时访问的人数。

4、参数详细说明
　　Pylot有很多参数，我详细介绍一下：

　　

-a, --agents=NUM_AGENTS
设置同时访问用户数量
-d, --duration=DURATION
设置总测试时间（秒）
-r, --rampup=RAMPUP
设置提升量（秒），我也没太搞懂这个是什么意思
-i, --interval=INTERVAL 
设置访问间隔（毫秒）
-x, --xmlfile=TEST_CASE_XML
设置要使用的xml文件，默认testcase.xml
-o, --output_dir=PATH
设置输出文件路径
-n, --name=TESTNAME
设置测试名称
-l, --log_msgs
设置是否需要日志信息
-b, --blocking  
设置是否开启锁定模式，如果开启会锁定输出直到测试结束
-g, --gui  
设置是否使用图形界面
-p, --port=PORT
设置xml-rpc监听的端口
　　常用的就是 -a -d -i -g，其他的不太常用，有几个我也搞不太清楚是什么意思。。。大家如果有知道的可以告诉我一下。

　　大家也看到了，使用-g选项的话就可以开启图形界面，图形界面我就不详细介绍了，虽然有几个英文单词吧，但是大家应该一眼就能看明白怎么用了，还是挺方便的。

　　如果你不想每次都手动设置参数，可以修改core文件夹里的config.py文件，这个文件是Pylot默认加载的配置。

　　好了，基本的介绍就到这里吧，对我来说知道这些已经足够用了，大家如果想看更深入的，比如设置cookie以及远程启动测试脚本等等进阶部分的话可以查看：Pylot官方教程。

5、查看测试结果
　　Pylot可以将测试结果转化成表格以及图的方式展示出来，测试完成后会在results文件夹中生成以当前日期命名的文件夹，打开之后可以看到一个html文件，这个就是测试结果了。

　　我们来看一个Pylot官方提供的例子吧：测试结果

　　pylot测试结果

　　这是第一部分。

　　最上面分别是结果的生成时间、测试的开始时间和测试的结束时间。

　　Workingload Model里分别是测试总时间、用户数以及提升（不太懂什么意思）和间隔时间。

　　Results Summary里是测试结果统计，可以看到总请求数（requests）、总错误数（errors）和总接受数据量（data received）。

　　最下面是访问时间统计以及流量统计。

　　avg是平均访问时间，stdev是标准差，min是最小值，max是最大值。50th %表示 排在50%位置（也就是中间位置）的访问时间，其他以此类推。

　　第二部分

　　这是第二部分。

　　第一张图表示的是测试时间与响应时间的关系，可以看到随着测试时间增大，响应时间也在增大。

　　第二张图表示的是测试时间和每秒请求数量的关系，可以看到随着测试时间增大，每秒请求数也在增大。

　　第三部分我就不截图了，就是具体的每个用户的信息。