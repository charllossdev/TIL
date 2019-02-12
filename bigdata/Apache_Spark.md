# Apache Spark

Apache Spark is a fast and general-purpose cluster computing system


# Categories

0. [Apache Spark](#apache-spark)
0. [](#)
0. [](#)


---

## 빅데이터

 기존의 데이터베이스 관리도구의 능력을 넘어서는 대량의 정형 또는 비정형 데이터의 집합 데이터로부터 가치를 추출하고 결과를 분석하는 기술

 기술 : 컴퓨터 1대로 처리하지 못하므로, 여러대를 연결해서 데이터를 저장하고 처리해야 하는 기술

빅테이터 기술은 대부분 하둡이라고 생각할 수 있다.

데이터를 읽어와서 변환하고, 핵심을 추출하는 것도 마찬가지로 컴퓨터 1대로 할 수 있는것보다 속도가 빨라야 한다.

맵리듀스 = 분산 데이터 처리 -> 현재는 스파크가 가장 많이 사용되고 있다.

## 왜 데이터 분석을 하는가?

* 비싼 비용에도 불구하고 큰 양의 데이터를 분석하는 이유? : 사업에 큰 영향력
  * 광고 비즈니스, 커머스, 금융 분야에서는 데이터가 매출과 직결되기 때문에 비싼 비용에도 데이터 분석에 큰 공을 들인다.


## BIG Data

Big data is a term used to refer to data sets that are too large or complex for traditional data-processing application software to adequately deal with. Data with many cases (rows) offer greater statistical power, while data with higher complexity (more attributes or columns) may lead to a higher false discovery rate.[2] Big data challenges include capturing data, data storage, data analysis, search, sharing, transfer, visualization, querying, updating, information privacy and data source. Big data was originally associated with three key concepts: volume, variety, and velocity.[3] Other concepts later attributed with big data are veracity (i.e., how much noise is in the data) [4] and value.[5]

Current usage of the term "big data" tends to refer to the use of predictive analytics, user behavior analytics, or certain other advanced data analytics methods that extract value from data, and seldom to a particular size of data set. "There is little doubt that the quantities of data now available are indeed large, but that's not the most relevant characteristic of this new data ecosystem."[6] Analysis of data sets can find new correlations to "spot business trends, prevent diseases, combat crime and so on."[7] Scientists, business executives, practitioners of medicine, advertising and governments alike regularly meet difficulties with large data-sets in areas including Internet search, fintech, urban informatics, and business informatics. Scientists encounter limitations in e-Science work, including meteorology, genomics,[8] connectomics, complex physics simulations, biology and environmental research.[9]

Data sets grow rapidly- in part because they are increasingly gathered by cheap and numerous information- sensing Internet of things devices such as mobile devices, aerial (remote sensing), software logs, cameras, microphones, radio-frequency identification (RFID) readers and wireless sensor networks.[10][11] The world's technological per-capita capacity to store information has roughly doubled every 40 months since the 1980s;[12] as of 2012, every day 2.5 exabytes (2.5×1018) of data are generated.[13] Based on an IDC report prediction, the global data volume will grow exponentially from 4.4 zettabytes to 44 zettabytes between 2013 and 2020.[14] By 2025, IDC predicts there will be 163 zettabytes of data.[15] One question for large enterprises is determining who should own big-data initiatives that affect the entire organization.[16]

Relational database management systems, desktop statistics[clarification needed] and software packages used to visualize data often have difficulty handling big data. The work may require "massively parallel software running on tens, hundreds, or even thousands of servers".[17] What qualifies as being "big data" varies depending on the capabilities of the users and their tools, and expanding capabilities make big data a moving target. "For some organizations, facing hundreds of gigabytes of data for the first time may trigger a need to reconsider data management options. For others, it may take tens or hundreds of terabytes before data size becomes a significant consideration."[18]

## 빅데이터의 시초: GFS

* **Google File System**
* 막대한 양의 웹 문서를 저장, 조회해야하는 상황에서 컴퓨터 1대로는 당연히 처리가 불가능
* 저렴한 하드웨어를 사용하면서, 중복저장을 통한 파일 유실을 방지
* 파일을 새로 추가하는데 집중
* 삭제나 파일 덮어쓰기는 어려움
* 클러스터의 대수를 늘릴수록 저장용량과 throughput이 점점 올라간다.

## 빅데이터의 시초: MapReduce

* **Google MapReduce**
* 여러대의 분산 저장소에 존재하는 데이터를 변환하거나 계산하기 위한 프레임워크
* Functional Programming의 Map() 함수와 Reduce() 함수를 조합하여 효율적으로 분산 환경에서 다양한 계산을 할 수 있다.
* MapReduce는 슈퍼컴퓨터 없이도 저렴한 서버를 여러 대 연결하여 빅데이터 분석을 가능하게 해 준 혁신적인 기술이다.
* 10년이 지나니 여러 가지 단점들이 보이게 되며, 특히 과도하게 복잡한 코드를 짜야한다.

## 빅데이터의 시초2: Hadoop

* Google의 GFS, MapReduce 논문을 보고 야후 프로젝트 팀원들이 오픈소스로 만듬
* Hadoop Hive Project
    * Hive
      SQL의 분석 쿼리를 실행하면, 이를 MapReduce 코드로 컴파일 해주는 분석도구
      MapReduce를 작성하기 어렵기 때문에 쉽게 사용가능

---

## Apache Spark

* 2012년에 등장하여 선풍적인 인기를 얻고있는 분산처리 프레임워크
* 메모리 기반의 처리를 통한 고성능과 Functional Programming 언어를 지향하는 프레임워크
* 스칼라, 자바, 파이썬, R
* [Hadoop VS Apache Spark](http://engineering.vcnc.co.kr/2015/05/data-analysis-with-spark/)
* Hadoop은 매번 중간 결과를 디스크에 저장하지만, Spark은 이를 메모리에서 처리하므로 효율이 매우 좋다.
* PageRank or 머신러닝 알고리즘 같이 반복계산이 많은 경우 특히 성능이 좋다


### Apache Spark 핵심개념

* **RDD(Resilient Distributed Dataset)** 탄력적으로 분산된 데이터 셋
    * 오류 자동복구 기능이 포함된 가상 리스트
    * 다양한 계산을 수행 가능, 메모리를 활용하여 높은 성능을 가짐
* **Scala Interface**
    * 매우 간결한 표현이 가능한 모던 프로그래밍 언어
    * Functional Programming이 가능하여 데이터의 변환을 효과적으로 표현할 수 있음


### Apache Spark 확장 프로그램

* Spark을 엔진으로 하는 확장 프로그젝트들이 같이 제공된다.
    * Spark SQL : Hive와 비슷하게 SQL로 데이터를 분석
    * Spark Streamming 실시간 분석
    * MLlib : 머신러닝 라이브러리
    * GraphX : 페이지랭크 같은 그래프 분석


### 향후 방향성

* Apache Spark이 계속 힘을 얻을 것
    * 강력한 성능과 좋은 인터페이스, 확장성


## Scala

> Scala 란?
> 데이터 분석을 위한 Scala

### **Sca**lable **La**nguage -> Scala
***

* 간결한 표현과 강력한 기능을 통해 더 큰 프로그램을 나들기 위한 언어
* Scala가 가진 여러가지 특징들이 데이터 분석하기에 좋은 것들이 많다.
* 아주 간결한 문법(Like Python)
* OOP, Functional Programming
* JVM에서 실행 -> Java와 호환
* 좋은 성능(== Java)
* 정적 타입


### Java - Scala

```Java
public class Job {
 public void main(String[] args) {
 Person kevin = new Person();
 kevin.setName("Kevin");
 kevin.setWork("Between");
 }
}

public class Person {
 private String name;
 private String work;
 public void setName(String name) {
 this.name = name;
 }
 public String getName() {
 return name;
 }
 public void setWork(String work) {
 this.work = work;
 }
 public String getWork() {
 return work;
 }
}
```



```Scala
class Person(val name: String, val work: String)

val kevin = new Person("Kevin", "Between")
```

### JVM(자바가상머신)

* JVM에서 실행, JAVA와 호환
* Scala 코드를 컴파일하면, java와 마찬가지로, .class 파일이 나옴
* JVM에서 실행, Java와 거의 동일한 실행 성능을 가짐
* Java Class Import 하여 사용 가능
* Java file롸 Scala file을 혼용하여 컴파일도 가능
