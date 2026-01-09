# Serverless To-Do REST API on AWS

## Project Overview

This project is a fully serverless RESTful To-Do API built using **AWS API Gateway (HTTP API)**, **AWS Lambda**, and **Amazon DynamoDB**. It provides complete CRUD (Create, Read, Update, Delete) functionality and is designed to be **Free Tier safe**, **secure**, and **browser-ready**.

The entire project was built using the **AWS Management Console only**, without Terraform, CDK, or AWS CLI.

---

## Architecture

```
Client / Browser / Postman
        ↓
API Gateway (HTTP API, CORS enabled)
        ↓
AWS Lambda (TodoHandler)
        ↓
Amazon DynamoDB (Todos table)
```

---

## Technologies Used

* AWS Lambda (Python runtime)
* Amazon DynamoDB (On-Demand billing)
* Amazon API Gateway (HTTP API)
* IAM (Least-Privilege Permissions)
* CORS for browser access

---

## DynamoDB Table

* Table Name: `Todos`
* Partition Key: `id` (String)
* Billing Mode: On-Demand (PAY_PER_REQUEST)

Each item is stored in the format:

```json
{
  "id": "uuid",
  "task": "Task description"
}
```

---

## Security

* Lambda uses least-privilege IAM permissions
* Access limited to required DynamoDB actions:

  * `GetItem`
  * `PutItem`
  * `UpdateItem`
  * `DeleteItem`
  * `Scan`
* Resource access restricted to the `Todos` table only

---

## API Details

Base URL:

```
https://r9309x2rdl.execute-api.us-east-1.amazonaws.com
```

### Available Endpoints

| Method | Endpoint      | Description       |
| ------ | ------------- | ----------------- |
| POST   | `/todos`      | Create a new todo |
| GET    | `/todos`      | List all todos    |
| GET    | `/todos/{id}` | Get a single todo |
| PUT    | `/todos/{id}` | Update a todo     |
| DELETE | `/todos/{id}` | Delete a todo     |

---

## Testing the API

### Create a Todo

```bash
curl -X POST https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos \
  -H "Content-Type: application/json" \
  -d '{"task": "Finish AWS project"}'
```

### List Todos

```bash
curl https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos
```

### Get a Single Todo

```bash
curl https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos/{id}
```

### Update a Todo

```bash
curl -X PUT https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos/{id} \
  -H "Content-Type: application/json" \
  -d '{"task": "Updated task"}'
```

### Delete a Todo

```bash
curl -X DELETE https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos/{id}
```

---

## Browser Usage Example

```html
<script>
async function listTodos() {
  const res = await fetch('https://r9309x2rdl.execute-api.us-east-1.amazonaws.com/todos');
  const data = await res.json();
  console.log(data);
}
listTodos();
</script>
```

---

## Features

* Full CRUD functionality
* Serverless architecture (no servers to manage)
* Secure IAM configuration
* CORS-enabled for frontend use
* Free Tier safe
* Production-ready structure

---

## Project Status

Completed and fully operational

This project demonstrates practical knowledge of AWS serverless services, REST API design, and cloud security best practices.

---

## License

This project is for educational and portfolio purposes.
