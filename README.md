# Mini-Project: Stock Data Streaming with Apache Kafka

## Introduction

In this mini-project, I applied my basic understanding of Apache Kafka to create a robust data pipeline for handling the live stream of stock data. Leveraging the power of Apache Kafka and complementary technologies, I successfully implemented a solution to manage real-time stock information.

## Architecture

![image](https://github.com/shyamal31/Stock-Data-pipeline-using-Apache-Kafka/assets/57554284/00f7290c-642f-40a8-89b0-1126bce4de8c)


The architecture of the project is designed to ensure efficiency and scalability. Key components include:

1. **Apache Kafka:** A distributed streaming platform forming the backbone of the data pipeline.
2. **Python:** Utilized for scripting and logic implementation.
3. **AWS Services:**
   - **EC2:** Providing scalable compute capacity.
   - **S3:** Serving as a reliable and scalable object storage solution.
   - **Athena:** Enabling easy querying of data stored in S3.
   - **Glue Crawler:** Facilitating automatic schema discovery.

First, we will write a Python logic to mimic the live stream data behavior using static data resource(CSV file), then the generated live data stream will one by one go throught the Kakfa architecture (Producer, Topic, Zookeeper, and Consumer). Finally, with the help of the consumer, we will store the data in S3 buckets. After that with the help of aws crawler and glue catalog, we will move our data to aws Athena to analyze it further. 


## Technology Used

- **Apache Kafka**
- **Python**
- **AWS:**
  - EC2
  - S3
  - Athena
  - Glue Crawler

## Dataset

Instead of relying on any live data streaming API, I opted for a practical approach by using [Microsoft stock data](https://finance.yahoo.com/quote/MSFT/history/?guccounter=1&guce_referrer=aHR0cHM6Ly93d3cuZ29vZ2xlLmNvbS8&guce_referrer_sig=AQAAADYx0aQsq-ieA8meNPH02KZOjS57qMczvgwrW46ZbEsOyT_pgp4nNLj_y__Ed0tHZ5ZtGRqUsQiJVGMRbfsj_dfMWTuRdIdlXuuFueHxuXSdb_J0TnzMjKRbBLr40TpEu2l2dmpxCRChLXEwAJd6KjupiveQrSt3AHsFxcC1-yex). To mimic the streaming behavior of the data, I wrote a Python logic, ensuring a realistic representation of the live stream of stock data within the project.
