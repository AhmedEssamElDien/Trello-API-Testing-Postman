# Trello API Testing – Postman Collection

A complete API testing suite for [Trello's REST API](https://developer.atlassian.com/cloud/trello/rest/), covering the full CRUD lifecycle for Boards, Lists, Cards, and Checklists.

## 📌 Overview

This project demonstrates end-to-end API testing skills using Postman: writing automated test scripts, chaining requests with dynamic variables, validating both success and error responses, and structuring a collection for maintainability.

## 🧪 What's Covered

| Resource | Operations Tested |
|---|---|
| **Boards** | Create, Get, Update, Delete |
| **Lists** | Create, Get, Update, Archive, Unarchive |
| **Cards** | Create, Get, Update, Delete |
| **Checklists** | Create, Get, Update, Delete |

**25 requests** in total, chained together so the output of one (e.g. a newly created Board ID) automatically feeds into the next request.

## ⚙️ Key Features

- **Automated test scripts** on every request — validating status codes, response schema (`id`, `name` fields), and data types using `pm.test()` and Chai assertions.
- **Dynamic variable chaining** — IDs returned from `Create_*` requests (BoardID, ListID, CardID, ChecklistID) are captured with `pm.collectionVariables.set()` and reused automatically in later requests, so the whole flow runs without manual copy-pasting.
- **Negative testing** — after deleting a resource, a follow-up `GET` confirms it correctly returns a `404`, verifying the delete actually worked.
- **Global response-time check** — a collection-level test ensures every request responds in under 1000ms.
- **Environment-based configuration** — Base URL and Trello API credentials (`key`, `token`) are kept as variables, never hardcoded into requests.

## 🚀 How to Run It

1. Import `Trello_APIs.postman_collection.json` into Postman.
2. Create a Postman environment (or use collection variables) with:
   - `Base_URL` → `https://api.trello.com`
   - `key` → your Trello API key
   - `token` → your Trello API token
   
   Get these from [Trello's Developer Portal](https://trello.com/power-ups/admin).
3. Run the full collection with the **Collection Runner**, or execute requests individually in order (Create → Get → Update → Delete) since later requests depend on IDs generated earlier.

## 🛠️ Tools Used

- **Postman** — request building, scripting, and test automation
- **Trello REST API** — the API under test
- **JavaScript (Chai/pm assertions)** — for writing test scripts

## 📎 Notes

- No API keys or tokens are included in this repository — you must supply your own via environment variables.
- This project was built as a hands-on practice exercise in API testing fundamentals: CRUD coverage, response validation, variable chaining, and error-case verification.

---

**Author:** Ahmed Essam
