# AI_Capstone_HW1

The raw data is named `data.csv`, which is the original data collected from Xiaomi Smart Band 7, containing 230-days data of myself. To perform different tasks, I preprocessed them into different files:
### Task 1: Clustering Pre-Sleep Physiological States and Analyzing Their Relationship with Deep Sleep Proportion (Unsupervised learning)
`data1.csv` contains the information in three hours before bedtime and when I went to bed and woke up. This file contains 229 rows of data. Please referred to `Task1_data_construction.py` in Appendix for more details.

| Feature Name               | Data Type  | Description | Example |
|----------------------------|-----------|-------------|-----|
| `total_sleep_hour`             | Float     | How long the sleep take (converted to hour format) | 9.87 |
| `bedtime_hour`             | Float     | Sleep start time (converted to hour format).$^{[1]}$ | 23.93 |
| `wakeup_hour`             | Float     | Sleep end time (converted to hour format) | 9.8 |
| `steps`            | Integer   | Step count within 3 hours before bedtime | 316 |
| `avg_heart_rate`   | Float     | Average heart rate within 3 hours before bedtime | 72.0 |
| `max_heart_rate`   | Integer     | Maximum heart rate within 3 hours before bedtime | 91 |

$[1]$: If it's later than 24:00, it would be added by 24 hours to keep similarity. For instance, 00:12 would be converted into 24.2 rather than 0.2, to indicate that 00:12 is close to maybe 23:30 (23.5).

| Label Name               | Data Type  | Description | Example |
|----------------------------|-----------|-------------|---|
| 🏷️`sleep_quality`         |Boolean (0/1)     | Whether the deep-sleep ratio is higher than 15%. | 1 |

### **Task 2: Classifying Exercise and Non-Exercise States Using Random Forest (Supervised Learning)**  
`data2.csv` contains the information in ten minutes, inclulding the heart rate and steps. This file contains 34293 rows of data. Please referred to `Task2_data_construction.py` in Appendix for more details.

| Feature Name          | Data Type  | Description | Example |
|----------------------|-----------|-------------|---------|
| `start_heart_rate`   | Integer   | Heart rate at the beginning of the 10-minute window | 81 |
| `end_heart_rate`     | Integer   | Heart rate at the end of the 10-minute window | 107 |
| `steps`             | Integer   | Total steps taken within the 10-minute window | 256 |

| Label Name    | Data Type  | Description | Example |
|--------------|-----------|-------------|---------|
| 🏷️ `exercise` | Boolean (0/1) | **0** = Non-exercise state, **1** = Exercise state | 1 |

### **Task 3: Predicting Heart Rate After Physical Activity Using Regression**  
The dataset is named `data3.csv`, which contains 300 records of physical activity and heart rate data. Please refer to `Task3_data_construction.py` in the Appendix for details on data preprocessing.

| Feature Name           | Data Type | Description | Example |
|------------------------|-----------|-------------|---------|
| `previous_heart_rate`  | Integer   | Initial heart rate before movement | 75 |
| `steps`               | Integer   | Total steps taken | 150 |
| `distance`            | Integer     | Distance covered (meters) | 120 |
| `calories`            | Integer     | Calories burned during the movement | 5 |

| Label Name   | Data Type | Description | Example |
|-------------|-----------|-------------|---------|
| 🏷️ `heart_rate`  | Integer   | Heart rate after walking | 82 |