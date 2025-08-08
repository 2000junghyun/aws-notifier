# aws-notifier

## Overview

- A Lambda function that sends **automated email notifications** based on key information from detected threat events
- Invoked by upstream classifier or responder systems, delivering alerts to pre-subscribed email recipients via AWS SNS
- Serves as a **notification module** that improves response speed by ensuring immediate awareness of security incidents

## Tech Stack

- AWS Lambda
- Python 3.9
- AWS SNS (Simple Notification Service)

## Directory Structure

```bash
.
├── lambda_function.py                # Sending threat alert notifications
└── README.md
```

## How It Works

- Extracts fields like `sourceIPAddress`, `userIdentity`, `eventName`, and `eventTime` from the incoming event
- Includes `classifierSource` to identify the origin of the detection
- Formats the extracted data into a readable email message and publishes it to the configured SNS topic
- Logs the result of the SNS operation and returns appropriate HTTP status codes based on success or failure

## Features / Main Logic

- **Automated Email Alert Delivery**
    
    Sends threat information automatically using SNS email subscriptions
    
- **Event Summary Formatting**
    
    Builds human-readable summaries from key event fields (IP, user, region, action, timestamp)
    
- **Classifier Source Tracking**
    
    Logs and includes the `classifierSource` to trace which classifier triggered the alert
    
- **Built-in Error Handling**
    
    Logs errors and returns a `500` status code if the SNS notification fails
    

## Motivation / Impact

- Enables **immediate awareness of threats**, improving the response time of security teams
- Acts as the **starting point of incident awareness** within a cloud security automation pipeline