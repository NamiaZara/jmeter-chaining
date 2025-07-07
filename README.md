# 💼 Performance Testing with JMeter – Dmoney API 

This project demonstrates end-to-end performance testing of the Dmoney API using Apache JMeter. It includes API chaining, CSV-driven dynamic data, token-based authorization, and transaction-level assertions. The test simulates realistic transaction flows by agents, customers, and merchants as per the provided scenario.

---

✅ **What I Have Done**

- Created a JMeter script (`dmoney.jmx`) to test the Dmoney API with three different transaction types.
- Performed deposit, send money, and merchant payment simulations using agents, customers, and merchants.
- Implemented API chaining and parameterized data from CSV files.
- Used Random Variable Controller to make transaction amounts dynamic.
- Collected and analyzed test results using JMeter's HTML report.
- Added assertions to validate transaction success.
- Took screenshots of key statistics and test summaries.

---

🛠 **Prerequisites**

- JMeter installed (version 5.4 or above recommended)
- Java installed and configured in system path
- Git installed (for uploading to GitHub)

---
## 🎯 Scenario Description

The test scenario simulates the following real-world activities:

1. ✅ **5 agents** perform **deposits** for **10 customers**
2. ✅ **5 customers** send money to **10 different customers**
3. ✅ **5 customers** make payments to **2 merchants**

---

## ⚙️ Technical Implementation

### 🛡️ Token Management
- **Admin Login** is performed **once** at the beginning of the test.
- An **authorization token** is extracted and passed across all thread groups using a **JMeter variable**.

### 🔄 Test Plan Design

The JMeter test plan (`dmoney.jmx`) includes **three separate thread groups**:

| Thread Group     | CSV File         | Threads | Ramp-Up Time | Notes                            |
|------------------|------------------|---------|---------------|----------------------------------|
| Agent Deposits   | `deposit.csv`    | 5       | 120 sec       | Agents deposit to 10 customers   |
| Send Money       | `sendMoney.csv`  | 5       | 120 sec       | 5 customers send to 10 others    |
| Merchant Payment | `payment.csv`    | 5       | 120 sec       | Payments made to 2 merchants     |

- Each transaction amount is dynamically generated using **Random Variable Controller** (range: 10–100).
- **Assertions** are added to validate successful responses from all APIs.

---

### 🚀 **How to Run the Test**

1. Open **JMeter**.
2. Load the `dmoney.jmx` file.
3. Make sure the following CSV files are in the same folder:
   - `deposit.csv` (agent data)
   - `sendMoney.csv` (customer data)
   - `payment.csv` (merchant data)
4. Click the green **Start** button to run the test.

### ➕ To Generate the HTML Report:

1. Right-click the **Test Plan** → Add → Listener → **Summary Report**
2. Save results to `dmoney.jtl`
3. Run the following command in terminal:

```bash
jmeter -g dmoney.jtl -o HTMLReport
```
## 📸 Screenshots
### 📈 Load Test Report
![image](https://github.com/user-attachments/assets/ea70eae4-b771-4d46-bb97-afe79acef1f2)






