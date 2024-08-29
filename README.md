# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output:
##  Data cleaning process:

```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS.csv")
df
```
![Screenshot 2024-08-20 152308](https://github.com/user-attachments/assets/4527d27f-ce48-44cb-b8ce-34bbd266e130)

```
df.head()
```
![image](https://github.com/user-attachments/assets/75445d50-f356-4172-a260-7744a4b8a5d0)

```
df.tail(5)
```
![image](https://github.com/user-attachments/assets/0aad2483-f1d4-4161-8819-6dd578b6c0b7)

```
df.isnull()
```
![Screenshot 2024-08-20 153018](https://github.com/user-attachments/assets/e3ad59dc-d554-42fa-ab22-1a0b8dccd19a)

```
df.notnull()
```
![Screenshot 2024-08-20 153131](https://github.com/user-attachments/assets/cab8a38c-0423-4657-8487-85a5b7cc4d9d)

```
df.dropna(axis=0)
```
![Screenshot 2024-08-20 153319](https://github.com/user-attachments/assets/6848d1b2-2b91-4d7b-aae2-89f3d5ebbd83)

```
df.dropna(axis=1)
```

![Screenshot 2024-08-20 153407](https://github.com/user-attachments/assets/551c2074-915a-4d95-8596-fbc85c7d3a34)

```
df.fillna(0)
```

![Screenshot 2024-08-20 153523](https://github.com/user-attachments/assets/d79561f9-7a81-4137-bd4e-1f44c82ca40c)

```
print(df.shape)
```

![Screenshot 2024-08-20 153810](https://github.com/user-attachments/assets/b1907a5f-ab9b-4ce5-a72c-7767076de54b)

##  IQR:
```
import pandas as pd
import seaborn as sns
ir=pd.read_csv('/content/iris.csv')
ir
```

![Screenshot 2024-08-20 153956](https://github.com/user-attachments/assets/5f92ae1d-167b-4412-8e99-312c878199d7)

```
ir.describe()
```

![Screenshot 2024-08-20 154042](https://github.com/user-attachments/assets/cc69d12e-9f65-4b57-a506-b8f9194f2749)

```
sns.boxplot(x='sepal_width',data=ir)
```

![Screenshot 2024-08-20 154153](https://github.com/user-attachments/assets/7c8b93dc-1649-4b07-bf99-39ce4448edeb)

```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```

![Screenshot 2024-08-20 154252](https://github.com/user-attachments/assets/c3276452-72db-4363-a9e0-3b0a7e0a8563)


```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```

![Screenshot 2024-08-20 154353](https://github.com/user-attachments/assets/4d29e256-9386-4ea4-82a6-02e0f5175f3c)

```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```

![Screenshot 2024-08-20 154438](https://github.com/user-attachments/assets/b5da97d6-af4b-4690-b448-c1ff0697ea18)

```
sns.boxplot(x='sepal_width',data=delid)
```

![Screenshot 2024-08-20 154526](https://github.com/user-attachments/assets/1fb5cdcf-87ba-4631-b643-d2aeb0b2f8a2)

## Z SQUARE

```
import matplotlib.pyplot as plt
import pandas as pd
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```

![Screenshot 2024-08-20 154842](https://github.com/user-attachments/assets/2f2868d2-4002-4f47-82c4-8c0ad8a19392)

```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
iqr = q3-q1
iqr
```

![Screenshot 2024-08-20 154942](https://github.com/user-attachments/assets/2dae9f2a-a47a-4249-90a6-159aea236d8d)

```
low = q1 - 1.5*iqr
low
```

![Screenshot 2024-08-20 155106](https://github.com/user-attachments/assets/68c83441-a0b3-4821-96c4-8113ec2d0abb)

```
high = q3 + 1.5*iqr
high
```

![Screenshot 2024-08-20 155213](https://github.com/user-attachments/assets/734158d2-fc68-4f4b-b315-b58ff808ae2c)

```
df1 = df[((df['height'] >=low)& (df['height'] <=high))]
df1
```

![Screenshot 2024-08-20 155255](https://github.com/user-attachments/assets/c6f95d8a-8a60-48bf-9fc0-3bb251eeabec)

```
z = np.abs(stats.zscore(df['height']))
z
```

![Screenshot 2024-08-20 155353](https://github.com/user-attachments/assets/0f13eb15-f41a-4de2-b43a-47c5062c495b)

```
 df1 = df[z<3]
 df1
```

![Screenshot 2024-08-20 155457](https://github.com/user-attachments/assets/2c5a2fc4-cbec-4311-bf01-d85c236ecef3)

# Result
 Thus the Data Cleaning Process and Detecting and Removal of Outliers is executed successfully.
