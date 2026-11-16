🇧🇷 [Português](README.md) | 🇺🇸 English

# Urban Scooter — Manual web and API testing

Final project of the **TripleTen QA Engineer program**: planning and executing manual tests for the scooter rental ordering flow of the **Urban Scooter** web app, plus testing its REST API.

## 📊 Results summary

| Test type | Test cases | Passed | Failed | Bugs logged in Jira |
|---|---|---|---|---|
| Web ("Place order" flow) | 62 | 50 | 12 | SF-1 to SF-12 |
| REST API (couriers) | 8 | 7 | 1 | SF-13 |
| **Total** | **70** | **57** | **13** | **13 bugs** |

## 🧪 What was tested

**Web tests** — order form tested on **Chrome and Opera (1280x720)**:
- First name, last name, address and phone fields
- Station selection with autocomplete
- Delivery date calendar
- Rental period dropdown
- Color selection and comment field
- Required field rules

**API tests** — courier endpoints (`/api/v1/courier`) in **Postman**:
- Creating a courier (success, duplicate login, missing required fields)
- Deleting a courier (success, repeated deletion, non-existent ID, empty ID)
- Validating status codes (200, 201, 400, 404, 409), response body and the effect on the database

## 🛠️ Techniques and tools

- **Test design techniques:** equivalence partitioning and boundary value analysis
- **Tools:** Postman, Jira, Google Sheets, Chrome, Opera
- **Documentation:** test cases with precondition, steps, test data, expected result and actual result

## 🐞 Main bugs found

| Bug | Description |
|---|---|
| SF-1 | Last name field accepts 16 characters (above the 15-character limit) |
| SF-2 | Address field does not accept 50 characters (maximum valid limit) |
| SF-3 | Order proceeds with an empty address field |
| SF-4 | "7th Street/Metro Center" station appears twice in the list |
| SF-5 | Phone field does not accept 10 characters (minimum valid limit) |
| SF-6 | Phone field accepts 13 characters (above the 12-character limit) |
| SF-7 | Calendar allows selecting today's date |
| SF-8 | Calendar allows navigating to past months |
| SF-9 | Date field accepts a past date typed manually |
| SF-10 | Empty rental period blocks the order without showing an error |
| SF-11 | No message when no color is selected |
| SF-12 | Comment field accepts more than 24 characters |
| SF-13 | API: deleting without an ID does not return 400 Bad Request |

All full reports, with steps and concrete test data, are in [BUGS.md](BUGS.md) (in Portuguese).

## 📁 Files

- [casos-de-teste-web.md](casos-de-teste-web.md) — the 62 web flow test cases (in Portuguese)
- [casos-de-teste-api.md](casos-de-teste-api.md) — the 8 API test cases (in Portuguese)
- [BUGS.md](BUGS.md) — the 13 bug reports copied from Jira (the project's Jira is private)
- [casos-de-teste-urban-scooter.xlsx](casos-de-teste-urban-scooter.xlsx) — the original spreadsheet with all test cases and results

## 👩‍💻 Author

Scheila Schwede Wink — [LinkedIn](https://www.linkedin.com/in/scheila-schwede-wink/)
