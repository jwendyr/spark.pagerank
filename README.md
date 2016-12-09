Spark Page Rank
==============

Resource:
http://ampcamp.berkeley.edu/5/exercises/graph-analytics-with-graphx.html#constructing-an-end-to-end-graph-analytics-pipeline-on-real-data
http://inst.eecs.berkeley.edu/~cs61c/fa15/projs/05_1/
https://github.com/drewnoff/simple-spark-page-rank/blob/master/src/main/scala/PageRank.scala
http://www.programcreek.com/java-api-examples/index.php?class=org.apache.spark.api.java.JavaRDD&method=mapToPair
http://www.programcreek.com/java-api-examples/index.php?source_dir=cdap-master/cdap-archetypes/cdap-spark-java-archetype/src/main/resources/archetype-resources/src/main/java/SparkPageRankProgram.java
http://ampcamp.berkeley.edu/big-data-mini-course/graph-analytics-with-graphx.html
http://kukuruku.co/hub/algorithms/social-network-analysis-spark-graphx
http://spark.apache.org/docs/latest/graphx-programming-guide.html
https://github.com/ajak6/Page-Rank-and-TFIDF-using-Apache-Spark/blob/master/PageRank.java

To make a jar:

    rm -rf spark.pagerank/
    git clone https://github.com/jwendyr/spark.pagerank.git
    cd spark.pagerank/
    mvn clean package
    unzip scowiki-20090929-one-page-per-line.zip
    hadoop fs -mkdir input
    hadoop fs -mkdir input/SparkPageRank
    hadoop fs -copyFromLocal scowiki-20090929-one-page-per-line input/SparkPageRank/1
    hadoop fs -rm -r output/SparkPageRank
    cd target/
    spark-submit --class com.spark.cis833.extra.SparkPageRank --master yarn cis833.extra-0.0.1-SNAPSHOT.jar input/SparkPageRank/1 output/SparkPageRank
    hadoop fs -copyToLocal output/SparkPageRank/part-00000 1
    head -n 100 1

