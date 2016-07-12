# Hive

q1:  select count(e.emp_no) from employees e join dept_emp d on(e.emp_no=d.emp_no) where e.gender="M";

q2:     select count(e.emp_no) from employees e join titles t on(e.emp_no=t.emp_no) where e.gender="F" AND t.title="Staff";


q3:   select d.dept_no, sum(s.salary) from salaries s join dept_emp e on(e.emp_no=s.emp_no) join departments d on(e.dept_no=d.dept_no)  group by d.dept_no;

q4:   :     select e.gender, sum(s.salaries) from employees e join salaries s on(e.emp_no=s.emp_no)  group by e.gender;

q5:   select e.emp_no from employees e join salaries s on(e.emp_no=s.emp_no)  where e.gender= 'M' AND s.salary>70000 AND (e.birth_date>'1960-00-00');


q6:

ToUppercase.java:

package hiveudf;
import org.apache.hadoop.hive.ql.exec.UDF;
import org.apache.hadoop.io.Text;
public class ToUppercase extends UDF {
	private Text result = new Text();

	public Text evaluate(Text str) {
	String word = str.toString();
	if (word!=null) {
	result.set(str.toString().toUpperCase());
	} 
	return result;
	}
	
		
	}


pom.xml:


<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.nexr</groupId>
	<artifactId>nexr-hive-udf</artifactId>
	<version>0.2-SNAPSHOT</version>
	<name>nexr-hive-udf</name>
	<description>nexr-hive-udf</description>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<hadoop.version>0.20.2</hadoop.version>
		<hive.version>0.9.0</hive.version>
	</properties>

	<dependencies>
		<!-- Hadoop -->
		<dependency>
			<groupId>org.apache.hadoop</groupId>
			<artifactId>hadoop-core</artifactId>
			<version>${hadoop.version}</version>
		</dependency>
		<!-- Hive -->
		<dependency>
			<groupId>org.apache.hive</groupId>
			<artifactId>hive-exec</artifactId>
			<version>${hive.version}</version>
		</dependency>
		<dependency>
			<groupId>org.apache.hive</groupId>
			<artifactId>hive-metastore</artifactId>
			<version>${hive.version}</version>
		</dependency>
		<dependency>
			<groupId>org.apache.hive</groupId>
			<artifactId>hive-pdk</artifactId>
			<version>${hive.version}</version>
		</dependency>
		<dependency>
			<groupId>javax.jdo</groupId>
			<artifactId>jdo2-api</artifactId>
			<version>2.3-eb</version>
		</dependency>
		<dependency>
			<groupId>commons-logging</groupId>
			<artifactId>commons-logging</artifactId>
			<version>1.1.1</version>
		</dependency>
		<dependency>
			<groupId>junit</groupId>
			<artifactId>junit</artifactId>
			<version>4.7</version>
			<scope>test</scope>
		</dependency>
	</dependencies>

</project>

hive queries.txtOpen
Displaying hive queries.txt.
