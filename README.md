Big Data Project

 Input File
- Refered Dr.case repo ((https://github.com/denisecase/setup-spark) for input file.
- Downloaded spark into the local machine by follwing the instruction provided by Dr.case in the repo.(https://github.com/denisecase/setup-spark).
- Open Powershell as Administrator and start Spark with Scala:
``` spark-shell ```

- step 1:Creating a Resilient Distributed Datasets
``` scala> val testRDD = sc.textFile("D:/rmjldata.txt") ```

- step 2:Breaking each line into words using flatmap
``` scala> val testFlatWC = testRDD.flatMap(line => line.split(" ")) ```

- step 3: Mapping each word and performing aggregate function
``` scala> val resWC = testFlatWC.map(word => (word, 1)).reduceByKey((a, b) => a + b) ```

- step 4: Display content is collect()
``` scala> resWC.collect() ```

- step 5: performing sort by for top results
``` scala> val resOrderbysorting = resWC.sortBy(_._2,false).take(10) ```

- step 6 : copying results from shell to textfile
``` def exportResults(f: java.io.File)(op: java.io.PrintWriter => Unit) {
|   val p = new java.io.PrintWriter(f)
|   try { op(p) } finally { p.close() }
| }
exportResults(new File("D:/output.txt")) { p =>
|   data.foreach(p.println)
| }
```





