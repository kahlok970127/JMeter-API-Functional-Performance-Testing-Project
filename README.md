# Restful Booker API Testing with JMeter

## 📌 Overview

This project demonstrates API functional testing and performance testing using **Apache JMeter** with the Restful Booker API.

The project covers the complete booking lifecycle, including authentication, creating a booking, retrieving booking details, updating booking information, deleting a booking, and verifying the deletion.

## 🛠️ Tools & Technologies

* Apache JMeter 5.6.3
* REST API
* JSON
* HTTP / HTTPS
* JMeter JSON Extractor
* JMeter Response Assertion
* JMeter Summary Report
* JMeter Aggregate Report

## 🧪 Functional Testing

The functional test covers the following API workflow:

```text
Create Token
     ↓
Create Booking
     ↓
Get Booking
     ↓
Update Booking
     ↓
Verify Updated Booking
     ↓
Delete Booking
     ↓
Verify Booking is Deleted
```

### Test Scenarios

* Generate authentication token
* Create a new booking
* Extract `bookingid` from the Create Booking response
* Use the extracted `bookingid` in subsequent requests
* Retrieve booking details
* Update booking information
* Verify the updated firstname and lastname
* Delete the booking
* Verify that the deleted booking returns `404 Not Found`

## 🔄 Dynamic Data Handling

The project uses JMeter variables to pass dynamic data between requests.

### Booking ID

The `bookingid` is extracted from the Create Booking response using a JSON Extractor.

```text
${bookingid}
```

The extracted booking ID is then used in subsequent requests:

```text
GET /booking/${bookingid}
PUT /booking/${bookingid}
DELETE /booking/${bookingid}
```

### Authentication Token

The authentication token is extracted from the authentication response and reused for authenticated requests:

```text
${token}
```

## ⚡ Performance Testing

A separate Thread Group is used for API performance testing.

Example configuration:

```text
Number of Threads: 10
Ramp-Up Period: 10 seconds
Loop Count: 5
```

The performance test measures:

* Response Time
* Throughput
* Error Rate
* Minimum Response Time
* Maximum Response Time
* Average Response Time
* Percentile Response Time

## 📊 Performance Test Results

The test generated **400 samples** across the booking workflow.

| Request                  | Samples | Error % | Average Response Time |
| ------------------------ | ------: | ------: | --------------------: |
| Token                    |      50 |      0% |              ~1048 ms |
| Create Booking           |      50 |      0% |               ~3.4 ms |
| Get Booking              |      50 |      0% |               ~3.4 ms |
| Update Booking           |      50 |      0% |               ~3.4 ms |
| Get Updated Booking      |      50 |      0% |               ~3.3 ms |
| Delete Booking           |      50 |      0% |               ~3.5 ms |
| Get Booking after Delete |      50 |      1% |               ~3.7 ms |

> **Note:** `Get Booking after Delete` is expected to return `404 Not Found`. This response is used to verify that the booking has been successfully deleted.

## 📁 Project Structure

```text
restful-booker-jmeter/
│
├── Test Plan.jmx
└── README.md
```

## 🎯 What I Learned

Through this project, I practiced:

* API testing with JMeter
* HTTP request configuration
* JSON request and response handling
* JSON Extractor
* Passing dynamic variables between requests
* API authentication
* Response Assertions
* Functional API testing
* API performance testing
* Analyzing response time and throughput
* Using JMeter Summary Report and Aggregate Report

## 🚀 Future Improvements

* Add more test data
* Add parameterization using CSV Data Set Config
* Increase concurrent users for load testing
* Perform stress testing
* Add HTML performance reports
* Integrate JMeter tests into CI/CD

## 👨‍💻 Project Purpose

This project was created as a hands-on learning project to develop practical skills in **API testing, automation, and performance testing using Apache JMeter**.
