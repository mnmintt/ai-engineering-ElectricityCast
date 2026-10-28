# Evaluation Criteria

## Evaluation Criteria Table

| Objective / Requirement ID | Evaluation Criterion | Capability Bucket | Measurement Method | Metric | Threshold | User / Business Outcome |
|---|---|---|---|---|---|---|
| O1 / FR5 | Estimated Bill Calculation Correctness | Domain-specific capability | Compare estimated bills against manually calculated test cases using different tariff selections and billing inputs. | Absolute difference between system result and expected result | Matches the expected result within the defined rounding tolerance for all predefined test cases | Users can estimate electricity bills without setting up their household or appliances. |
| O1 / FR5 / RAI2 | Estimated Bill Transparency | Instruction-following capability | Test different tariff selections and cases with missing or incomplete tariff information. Check whether the system identifies assumptions and limitations. | Correct tariff selection and appropriate estimate or missing-information notice rate | 100% of defined test cases | Users understand the assumptions and limitations behind their estimated bills. |
| O2 / FR3 / NFR1 | Home Energy Calculation Correctness | Domain-specific capability | Compare daily and monthly kWh results against manually calculated test cases using different appliance inputs. | Absolute calculation error in kWh | ≤ 0.01 kWh for predefined test cases | Users receive reliable estimates of household electricity consumption. |
| O2 / FR4 | Dashboard Consistency | Domain-specific capability | Compare dashboard totals by appliance, room, floor, and household against the underlying calculation results. | Percentage of tested dashboard totals that match calculated values | 100% of defined test cases | Users can identify which rooms and appliances contribute most to their estimated electricity usage. |
| O3 / FR6 / RAI1 | Recommendation Quality | Generation capability | Evaluate 20 generated recommendations using a rubric covering relevance, practicality, and consistency with household data. | Number of recommendations meeting the rubric | At least 18 out of 20 | Users receive practical energy-saving suggestions based on their household information. |
| O3 / FR6 / RAI4 | Chatbot Numerical Grounding | Instruction-following capability | Ask the chatbot questions about household kWh and calculated energy costs. Compare its numerical claims with verified calculation-engine outputs. | Percentage of tested numerical claims matching verified outputs or correctly labelled as unavailable estimates | 100% | Users receive answers that are consistent with the system's calculated data. |
| O3 / FR7 | What-if Simulator Correctness | Domain-specific capability | Change appliance usage hours or quantities and compare the displayed baseline and adjusted consumption values against manual calculations. | Percentage of tested scenarios with correct consumption differences | 100% of defined test cases | Users can compare possible changes in appliance usage before deciding how to save energy. |
| O1, O2 / NFR2 | Response Latency | Cost and latency | Measure response time for local bill calculations, energy calculations, and dashboard operations. Measure external AI responses separately. | p90 latency | ≤ 3 seconds for local operations | Users can use both calculators without unnecessary delays. |
| O1, O2 / NFR3 | Calculation Reliability | Domain-specific capability | Run at least 50 valid calculation test cases covering both calculators and record successful completions. | Successful calculation rate | 100% of valid test cases | Users can rely on both calculators to complete valid requests. |
| O1, O2 / NFR4 | Interface Usability | Usability capability | Ask five intended users to complete a bill estimation task and a home energy analysis task independently. | Number of users completing the defined tasks without assistance | At least 4 out of 5 users | Users can understand and use each feature independently. |
| O3 / RAI3 | Privacy Protection | Instruction-following capability | Inspect outgoing AI requests for unnecessary direct personal identifiers using test household profiles. | Number of requests containing unnecessary direct personal identifiers | 0 in the defined test cases | Unnecessary personal information is not sent to the external AI service. |

## Evaluation Notes

- O1: Develop the Estimated Bill Calculator.
- O2: Develop the Home Energy Calculator.
- O3: Provide AI-based recommendations and household energy assistance within the Home Energy Calculator.
- The two calculators have separate inputs, calculation processes, and outputs.
- Users can access either calculator without completing the other.
- Evaluation thresholds are proposed targets. Actual performance will be measured during testing.
- The Estimated Bill Calculator must use documented tariff rates and clearly state its assumptions. Its result is an estimate, not a guaranteed exact TNB bill.
