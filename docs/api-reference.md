# Patient Data API Reference

**Version:** 2.1.0 | **Base URL:** `https://api.medcore.io/v2` | **Protocol:** REST

---

## Overview

The MedCore Patient Data API provides secure, HIPAA-compliant access to 
de-identified patient records for authorized healthcare applications. 
All endpoints require Bearer token authentication.

---

## Authentication

Include your API key as a Bearer token in every request header:

````http
Authorization: Bearer YOUR_API_KEY
Content-Type: application/json
````

---

## Endpoints

### GET /patients/{id}

Retrieves a single patient record by ID.

**Parameters**

| Parameter | Type   | Required | Description                          |
|-----------|--------|----------|--------------------------------------|
| `id`      | string | Yes      | Unique patient identifier (UUID)     |
| `fields`  | string | No       | Comma-separated fields to return     |

**Example Request**

````bash
curl -X GET "https://api.medcore.io/v2/patients/a3f9c821" \
  -H "Authorization: Bearer YOUR_API_KEY"
````

**Example Response**

````json
{
  "id": "a3f9c821",
  "age_group": "45-54",
  "diagnosis_codes": ["E11.9", "I10"],
  "last_visit": "2024-11-03",
  "facility_id": "CHI-042"
}
````

**Response Codes**

| Code | Meaning                             |
|------|-------------------------------------|
| 200  | Success                             |
| 401  | Unauthorized — check your API key   |
| 404  | Patient ID not found                |
| 429  | Rate limit exceeded (100 req/min)   |

---

### POST /patients/search

Returns a list of patient records matching the specified filters.

**Request Body**

````json
{
  "diagnosis_code": "E11.9",
  "age_group": "45-54",
  "date_range": {
    "start": "2024-01-01",
    "end": "2024-12-31"
  },
  "limit": 50
}
````

---

## Rate Limits

| Plan       | Requests/minute | Requests/day |
|------------|-----------------|--------------|
| Basic      | 60              | 10,000       |
| Standard   | 100             | 50,000       |
| Enterprise | 500             | Unlimited    |

---

## Error Reference

All errors follow this format:

````json
{
  "error": {
    "code": "INVALID_PATIENT_ID",
    "message": "The patient ID format is invalid. Expected UUID v4.",
    "docs_url": "https://docs.medcore.io/errors#INVALID_PATIENT_ID"
  }
}
````

---

*This is a writing sample created for portfolio purposes. MedCore is a fictional product.*
