# ApacheSpark-With-Scala

Here’s a clean, professional README.md you can use for documenting your setup. I’ve written it so it works both for learning and for sharing with others (or your students).

# Apache Zeppelin + Spark (Scala) Setup Guide

This project documents the setup of Apache Zeppelin notebooks configured to run Apache Spark using Scala.

---

## 🚀 Overview

This setup allows you to:
- Run Apache Spark using Scala interactively
- Write and execute distributed data processing code
- Use notebooks for learning, teaching, and experimentation

---

## 🧰 Tech Stack

- Apache Zeppelin (Notebook Interface)
- Apache Spark (Execution Engine)
- Scala (Programming Language)
- Java (JDK 8 or 11)

## Versions - Below are standard versions

- Spark 3.5.3
- Java 11
- Scala 2.12


## 📦 Prerequisites

Make sure the following are installed:

- Java JDK (8 or 11) - openjdk
- Apache Spark (pre-built package)

## Install Java 11
- Mac - https://medium.com/@kirebyte/using-homebrew-to-install-java-jdk11-on-macos-2021-4a90aa276f1c
- Windows - https://www.codejava.net/java-se/download-and-install-java-11-openjdk-and-oracle-jdk

## Install Spark 3.5.3 on mac
- Mac - To Install latest version - https://medium.com/beeranddiapers/installing-apache-spark-on-mac-os-ce416007d79f
- MAC - To install specific verison - Download it from Apache Spark site and extract

# Steps to install in mac
## ⚙️ Method 2: Manual Installation (Standalone)

### 1. Download Spark
- Download **Spark 3.5.8 pre-built for Hadoop** from the official Apache Spark downloads page.

---

### 2. Extract the Package
bash
tar -xvf spark-3.5.8-bin-hadoop3.tgz
3. Move to /opt Directory
sudo mv spark-3.5.8-bin-hadoop3 /opt/spark
4. Set Environment Variables
Add the following to your ~/.zshrc or ~/.bash_profile:

export SPARK_HOME=/opt/spark
export PATH=$SPARK_HOME/bin:$PATH
5. Apply Changes
source ~/.zshrc
🐍 Method 3: PySpark (Python Only)
If you only need Spark for Python, install it directly using pip:

pip install pyspark==3.5.8
⚠️ Note
Ensure Java is installed before running Spark:

java -version


# Apache Spark 3.5.8 Installation Guide (Windows)

Installing **Apache Spark 3.5.8 on Windows** requires installing Java, Python, downloading Spark, setting up Hadoop binaries (`winutils.exe`), and configuring environment variables.

## 📋 Prerequisites

### 1. Java
- Install **JDK 8, 11, or 17** (JDK 17 recommended)
- Verify installation:
  ```bash
  java -version
2. Python
Install Python (required for PySpark)

3. Winutils (Hadoop binaries)
Download:

winutils.exe
hadoop.dll

Recommended source: cdarlint/winutils GitHub repository

⚙️ Step-by-Step Installation
1. Download Spark 3.5.8
Download pre-built package:

spark-3.5.8-bin-hadoop3.tgz
From the official Apache Spark website

2. Extract Files
Extract the .tgz file

Place in a directory without spaces:

C:\spark-3.5.8
3. Setup Hadoop Binaries (Winutils)
Create directory:
C:\hadoop\bin

Move files:
winutils.exe
hadoop.dll
into: C:\hadoop\bin

4. Set Environment Variables
Open:

Edit the system environment variables
Add the following:

JAVA_HOME

C:\Program Files\Java\jdk-17
SPARK_HOME

C:\spark-3.5.8
HADOOP_HOME

C:\hadoop
Update Path variable:

%JAVA_HOME%\bin
%SPARK_HOME%\bin
%HADOOP_HOME%\bin
5. Verify Installation
Open Command Prompt or PowerShell:

pyspark
If Spark shell starts successfully → ✅ Installation complete

🚀 Alternative: Install via PyPI
If you only need Spark for Python development:

pip install pyspark

Verify installation:

#bash
java -version


⚙️ Environment Variables
Set the following environment variables:
Mac / Linux
export JAVA_HOME=/path/to/java
export SPARK_HOME=/path/to/spark
export PATH=$SPARK_HOME/bin:$PATH

Windows
setx JAVA_HOME "C:\path\to\java"
setx SPARK_HOME "C:\path\to\spark"
setx PATH "%SPARK_HOME%\bin;%PATH%"


📥 Install Apache Zeppelin
Download Apache Zeppelin from the official site (Spark pre-built version recommended).
Extract the archive:
tar -xvzf zeppelin-*.tgz
cd zeppelin-*


▶️ Start Zeppelin
Mac / Linux
bin/zeppelin-daemon.sh start

Windows
bin\zeppelin.cmd


🌐 Access Zeppelin UI
Open your browser:
http://localhost:8080


📝 Create a Notebook


Click on Create New Note


Select default interpreter (Spark)


Use %spark for Scala execution



🔍 Verify Spark is Working
Run the following in a notebook cell:
println("Spark Version: " + spark.version)

Example output:
Spark Version: 3.5.0


🧪 Sample Spark Scala Code
val data = Seq(1, 2, 3, 4, 5)
val rdd = sc.parallelize(data)

val result = rdd.map(_ * 2).collect()
result.foreach(println)


🔧 Interpreter Configuration
To configure Spark:


Go to Interpreter


Locate spark


Update properties like:


spark.master (e.g., local[*])


SPARK_HOME



📁 Project Structure (Optional)
zeppelin-spark-setup/
│
├── README.md
├── notebooks/
└── configs/


🛠️ Useful Commands
Check Spark version via terminal:
$SPARK_HOME/bin/spark-submit --version

## zeppelin installation

Great—you’ve already got Java 11 + Apache Spark 3.5.8 in place. Now let’s install Apache Zeppelin and (optionally) point it to your Spark.

🍏 Mac Installation (Zeppelin)
1) Download
Go to: https://zeppelin.apache.org/download.html
Pick:
“Binary package with Spark included” (simplest)
or “without Spark” (if you want to use your Spark 3.5.8)
2) Extract
cd ~/Downloads
tar -xvf zeppelin-*.tar.gz
mv zeppelin-* ~/zeppelin
cd ~/zeppelin

3) Set JAVA_HOME
export JAVA_HOME=$(/usr/libexec/java_home -v 11)

4) (Optional but recommended) Use your Spark 3.5.8

If you downloaded Zeppelin without Spark OR want to use your own Spark:

cp conf/zeppelin-env.sh.template conf/zeppelin-env.sh
nano conf/zeppelin-env.sh


Add:

export SPARK_HOME=/path/to/your/spark-3.5.8
export JAVA_HOME=$(/usr/libexec/java_home -v 11)


Save & exit.

5) Start Zeppelin
./bin/zeppelin-daemon.sh start


Open:

http://localhost:8080

🪟 Windows Installation
1) Download

Same as Mac:

Download Zeppelin (with or without Spark)
2) Extract

Extract to:

C:\zeppelin

3) Set Environment Variables
JAVA_HOME
C:\Program Files\Java\jdk-11

(Optional) SPARK_HOME

If using your Spark:

C:\spark-3.5.8


Add both to Path:

%JAVA_HOME%\bin
%SPARK_HOME%\bin

4) Configure Zeppelin (if using your Spark)

Go to:

C:\zeppelin\conf


Rename:

zeppelin-env.cmd.template → zeppelin-env.cmd


Edit and add:

set SPARK_HOME=C:\spark-3.5.8
set JAVA_HOME=C:\Program Files\Java\jdk-11

5) Start Zeppelin

Open Command Prompt:

cd C:\zeppelin\bin
zeppelin.cmd


Open:

http://localhost:8080

⚡ First Test (Scala + Spark)

Create a new note and run:

val df = spark.range(1, 10)
df.show()


If it runs → 🎉 you’re done.

⚠️ Important Decision (don’t skip)
Option A (Simple)

👉 Use Zeppelin with bundled Spark
✔ Works instantly
✔ Best for quick learning

Option B (Your current setup)

👉 Use your Spark 3.5.8
✔ Better for consistency with projects
✔ Good for teaching real-world setup

🧠 My recommendation for you

Since you:

want to practice + teach Spark with Scala

👉 Use:

Zeppelin + your Spark 3.5.8

This keeps:

Notebook learning
Real-world compatibility
