## Section 1 — Functional Requirements

| ID | Requirement — The system SHALL | Scope Boundary — SHALL NOT (where relevant) |
|---|---|---|
| FR1 | Allow users to configure their house type, number of floors, rooms, and household structure. | SHALL NOT require live smart-home devices to configure a household. |
| FR2 | Allow users to enter appliance names, quantities, wattage, and daily usage hours. | SHALL NOT assume that missing or unknown appliance information is accurate. |
| FR3 | Calculate estimated daily and monthly electricity consumption using appliance wattage, quantity, and usage duration. | SHALL NOT use AI-generated values as a replacement for the calculation formula. |
| FR4 | Display estimated electricity consumption statistics by appliance, room, floor, and household. | SHALL NOT display statistics that cannot be calculated from the available input data. |
| FR5 | Estimate household electricity costs using the selected tariff type and documented tariff assumptions. | SHALL NOT claim that the estimated amount is the exact TNB bill. |
| FR6 | Generate AI-based energy-saving recommendations and answer household energy questions using available household data and relevant energy-saving information. | SHALL NOT present unsupported assumptions as confirmed household facts. |
| FR7 | Allow users to change appliance usage assumptions and compare estimated electricity consumption and costs before and after the changes. | SHALL NOT claim that simulated savings are guaranteed real-world savings. |

---

## Section 2 — Non-Functional Requirements

| ID | Quality Attribute | Requirement | Measurement Method | Metric | Threshold |
|---|---|---|---|---|---|
| NFR1 | Correctness | The system shall calculate electricity consumption accurately using the defined formula. | Compare results against manually calculated test cases covering different wattages, quantities, and usage hours. | Absolute calculation error in kWh | ≤ 0.01 kWh for predefined test cases |
| NFR2 | Performance | The system shall return local calculations and dashboard updates within an acceptable time. | Measure response time across a defined set of local calculation and dashboard operations. | 90th-percentile response time (p90) | ≤ 3 seconds for local operations |
| NFR3 | Reliability | The system shall complete valid calculation requests without calculation errors. | Run at least 50 valid calculation test cases and record successful completions. | Successful calculation rate | 100% of valid test cases |
| NFR4 | Usability | Users shall be able to complete basic household setup and electricity calculation tasks without assistance. | Conduct a usability test with five intended users. | Number of users completing the defined tasks without assistance | At least 4 out of 5 users |


---

## Section 3 — Responsible AI Requirements

| ID | Responsible AI Risk | Requirement | Measurement Method | Metric | Threshold |
|---|---|---|---|---|---|
| RAI1 | Recommendation Quality | The system shall provide relevant and practical energy-saving recommendations based on available household data. | Evaluate 20 recommendations using a predefined rubric for relevance, practicality, and consistency with the supplied data. | Recommendations meeting the rubric | At least 18 out of 20 |
| RAI2 | Transparency and Missing Data | The system shall acknowledge missing or insufficient information and identify when an estimate depends on assumptions. | Test cases with missing wattage, usage hours, household details, or tariff information. | Test cases that correctly acknowledge missing information | 100% of defined missing-data test cases |
| RAI3 | Privacy | The system shall avoid sending unnecessary personal identifiers to an external AI service. | Inspect outgoing AI requests using test household profiles. | Requests containing unnecessary direct personal identifiers | 0 in the defined test cases |
| RAI4 | Numerical Grounding | AI-generated responses shall use verified calculation-engine results for electricity consumption and cost figures, or clearly identify when a value is an unavailable estimate. | Compare AI responses against calculation-engine outputs using a predefined test set. | Numerical claims matching verified results or correctly labelled as unavailable estimates | 100% of tested numerical claims |
