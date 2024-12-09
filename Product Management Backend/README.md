Overview
This project implements a backend system for managing products, designed with scalability, asynchronous processing, caching, and robust error handling. The system features image compression and cloud storage integration to enhance performance and usability.

Features

Product Management:
Add, retrieve, and update product details, including images.
Support for filtering and querying products by price range and name.

Asynchronous Image Processing:
Product image URLs are added to a message queue (RabbitMQ).
An image processing service downloads, compresses, and uploads images to AWS S3.
The database is updated with the URLs of compressed images.

Caching:
Uses Redis to cache product details for faster retrieval and reduced database load.
Implements cache invalidation to ensure consistency with database updates.

Data Storage:
PostgreSQL for relational data storage with separate tables for users and products.
Includes a compressed_product_images field in the products table.

Logging and Monitoring:
Structured logging using logrus or zap.
Detailed logs for API requests, image processing events, and error handling.

Error Handling:
Retry mechanisms for failed queue processing.
Dead-letter queues for persistent failure scenarios.

Testing:
Unit and integration tests for core functionalities.
Benchmarks for API performance with and without caching.