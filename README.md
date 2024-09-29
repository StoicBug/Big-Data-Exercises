# Word Count MapReduce Project

This project implements a simple Word Count algorithm using Hadoop MapReduce. It counts the occurrences of each word in the input text file.

## Prerequisites

- Docker and Docker Compose installed on your system
- Basic understanding of Hadoop and MapReduce concepts

## Project Structure

```
project_root/
│
├── src/
│   └── main/
│       └── java/
│           └── ma/
│               └── enset/
│                   ├── Main.java
│                   ├── WordCountMapper.java
│                   └── WordCountReducer.java
│
├── apps/
│   └── (place your compiled JAR file here)
│
├── docker-compose.yml
└── README.md (this file)
```

## Setup and Running

1. Clone this repository to your local machine.

2. Compile the Java code and create a JAR file. Name it `TP.jar` and place it in the `apps/` directory.

3. In the project root directory, run the Docker Compose file:

   ```
   docker-compose up -d
   ```

   This will set up the Hadoop cluster using Docker containers.

4. Once the containers are up and running, execute into the namenode container:

   ```
   docker exec -it namenode bash
   ```

5. Inside the namenode container, navigate to the apps directory:

   ```
   cd /opt/hadoop/apps
   ```

6. Create a sample input file in HDFS:

   ```
   hdfs dfs -touchz /file1.txt
   hdfs dfs -appendToFile - /file1.txt
   deer car deer beer
   car car car deer
   beer humaine
   ```

   Press Ctrl+D after entering the text to save the file.

7. Run the MapReduce job:

   ```
   hadoop jar TP.jar /file1.txt /output1
   ```

8. Once the job is complete, you can view the output directory:

   ```
   hdfs dfs -ls /output1
   ```

9. To see the results of the word count:

   ```
   hdfs dfs -cat /output1/part-r-00000
   ```

   This will display each word along with its count.

## Troubleshooting

- If you encounter permission issues, make sure your JAR file has the correct permissions.
- Check the Hadoop logs for any error messages if the job fails to run.

## Cleaning Up

To stop and remove the Docker containers, run:

```
docker-compose down
```

## Contributing

Feel free to fork this project and submit pull requests with improvements or bug fixes.
