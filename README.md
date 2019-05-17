# freedom
This is a free Repository.
#!/bin/sh
export LC_ALL=en_US.UTF-8
rm -Rf /data/sourcecode/test/*

svn co svn://132.232.41.245/test/trunk/test --username=ycj --password=ycj123 /data/sourcecode/test

cd /data/sourcecode/test
# mvn -s 指定 settings.xml文件
# -DskipTests，不执行测试用例，但编译测试用例类生成相应的class文件至target/test-classes下。
# -Dmaven.test.skip 不执行测试用例，也不编译测试用例类 （maven默认编译执行测试用例）
# clean package 依次执行了clean、resources、compile、testResources、testCompile、test、jar(打包)等７个阶段。
# clean install依次执行了clean、resources、compile、testResources、testCompile、test、jar(打包)、install等8个阶段。
# clean deploy依次执行了clean、resources、compile、testResources、testCompile、test、jar(打包)、install、deploy等９个阶段。
# package命令完成了项目编译、单元测试、打包功能，但没有把打好的可执行jar包（war包或其它形式的包）布署到本地maven仓库和远程maven私服仓库
# install命令完成了项目编译、单元测试、打包功能，同时把打好的可执行jar包（war包或其它形式的包）布署到本地maven仓库，但没有布署到远程maven私服仓库
# deploy命令完成了项目编译、单元测试、打包功能，同时把打好的可执行jar包（war包或其它形式的包）布署到本地maven仓库和远程maven私服仓库　　

mvn -s /app/apache-maven-3.6.0/conf/settings.xml -Dmaven.test.skip clean package
sleep  2
rm -Rf /app/test/test-0.0.1.jar
mv /data/sourcecode/test/target/app.jar /app/test/
