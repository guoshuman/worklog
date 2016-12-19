#2016-11-19更新：  
##一、启动solr服务
**1、linux/unix/OSX下下载.tgz的solr，windows下下载.zip的solr；**  
**2、压缩文件下载好之后，输入以下命令**  
	    $~/  
	    $tar zxf solr-x.y.z.tgz  
**安装solr文件；**  
**3、运行solr文件：**  
**linux下：**	    $bin/solr start  
**windows下：**	    bin\solr.cmd start  
  
**4、一般情况下，solr都是在背后运行，特别是unix/linux下，如果我们想让它在前端运行，只需要：**  
**linux/unix下：**	    $bin/solr start -f  
**windows下：**	    $bin/solr.cmd start -f  
**5、solr的默认端口是8983，如果想换个不同的端口：**  
	    $bin/solr start -p 8984  
**6、我们利用-f将solr运行在前端，我们可以利用ctrl-c来停止它，但是，当solr在后台运行时，我们需要输入停止命令：**  
	    $bin/solr stop -p 8983  
**7、开始运行solr的一些捆绑的例子；solr提供了很多例子来帮助理解它的关键特点。我们可以利用-e flag来运行这里例子，以“techproducts”为例，我们用：**  
	    $bin/solr -e techproducts  
**来启动这个例子。很明显，我们可以运行的可获多的例子有：[techproducts dih schemaless cloud](https://cwiki.apache.org/confluence/display/solr/Solr+Start+Script+Reference#SolrStartScriptReference-RunningwithExampleConfigurations).从的 [Ru
nning with Example Configurations](https://cwiki.apache.org/confluence/display/solr/Solr+Start+Script+Reference#SolrStartScriptReference-RunningwithExampleConfigurations)来看每个例子的细节。**  
**对于SolrCloud模块，运行cloud例子，在[Getting Started with SolrCloud](https://cwiki.apache.org/confluence/display/solr/Solr+Start+Script+Reference#SolrStartScriptReference-RunningwithExampleConfigurations)这部分。**  
**8、检查solr是否运行，用：**  
	    $bin/solr status  
  
##二、建立索引  
**1、执行**  
	    #bin/post -c gettingstarted docs/  
	    #bin/post -c gettingstarted docs/  
	    java -classpath /solr-5.0.0/dist/solr-core-5.0.0.jar -Dauto=yes -Dc=gettingstarted -Ddata=files -Drecursive=yes org.apache.solr.util.SimplePostTool docs/  
	    SimplePostTool version 5.0.0  
	    Posting files to [base] url http://localhost:8983/solr/gettingstarted/update...  
	    Entering auto mode. File endings considered are xml,json,csv,pdf,doc,docx,ppt,pptx,xls,xlsx,odt,odp,ods,ott,otp,ots,rtf,htm,html,txt,log  
	    Entering recursive mode, max depth=999, delay=0s  
	    Indexing directory docs (3 files, depth=0)  
	    POSTing file index.html (text/html) to [base]/extract  
	    POSTing file quickstart.html (text/html) to [base]/extract  
	    POSTing file SYSTEM_REQUIREMENTS.html (text/html) to [base]/extract  
	    Indexing directory docs/changes (1 files, depth=1)  
	    POSTing file Changes.html (text/html) to [base]/extract  
	    ...  
	    3254 files indexed.  
	    COMMITting Solr index changes to http://localhost:8983/solr/gettingstarted/update...  
	    Time spent: 0:02:27.712  
**2、为xml文件建立索引**  
  
	    #bin/post -c gettingstarted example/exampledocs/*.xml  
**3、为JSON文件建立索引**  
  
	    #bin/post -c gettingstarted example/exampledocs/*.json  
**4、为CSV文件建立索引**  
  
	    #bin/post -c gettingstarted example/exampledocs/books.csv  

color=#DC143C 今天出现的问题：  
color=#DC143C建立索引时运行：	    #bin/post -c gettingstarted example/exampledocs/*.xml，无法得出正常结果。  

