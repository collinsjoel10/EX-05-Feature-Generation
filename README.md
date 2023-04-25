# EX-05-Feature-Generation


## AIM
To read the given data and perform Feature Generation process and save the data to a file. 

# Explanation
Feature Generation (also known as feature construction, feature extraction or feature engineering) is the process of transforming features into new features that better relate to the target.
 

# ALGORITHM
### STEP 1
Read the given Data
### STEP 2
Clean the Data Set using Data Cleaning Process
### STEP 3
Apply Feature Generation techniques to all the feature of the data set
### STEP 4
Save the data to the file


# CODE
Developed by: JOEL P

Register no : 212222230057

Data:
```
import pandas as pd
df=pd.read_csv("data.csv")
print(df)
import category_encoders as ce
be=ce.BinaryEncoder()
df1=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
df1
be=ce.BinaryEncoder()
df2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
df2
df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder,OneHotEncoder
import category_encoders as ce
be=ce.BinaryEncoder()
ohe=OneHotEncoder(sparse=False)
le=LabelEncoder()
oe=OrdinalEncoder()
df1["City"] = ohe.fit_transform(df1[["City"]])
temp=['Cold','Warm','Hot','Very Hot']
oe1=OrdinalEncoder(categories=[temp])
df1['Ord_1'] = oe1.fit_transform(df1[["Ord_1"]])
edu=['High School','Diploma','Bachelors','Masters','PhD']
oe2=OrdinalEncoder(categories=[edu])
df1['Ord_2']= oe2.fit_transform(df1[["Ord_2"]])
df1
## SCALING:
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df2=pd.DataFrame(sc.fit_transform(df1),columns=(['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target']))
df2
from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df3=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df3
from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df4=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df4
from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df5=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'City', 'Ord_1','Ord_2','Target'])
df5
```

Encoding data:

```
import pandas as pd
df=pd.read_csv("Encoding Data.csv")
df
## GENERATION
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df["bin_1"])
df["bin_1"] = be.fit_transform(df["bin_1"])
ndf
be=ce.BinaryEncoder()
ndf2=be.fit_transform(df["bin_2"])
df["bin_2"] = be.fit_transform(df["bin_2"])
ndf2
df1=df.copy()
from sklearn.preprocessing import LabelEncoder,OrdinalEncoder
le=LabelEncoder()
oe=OrdinalEncoder()
df1["nom_0"] = oe.fit_transform(df1[["nom_0"]])
temp=['Cold','Warm','Hot']
oe2=OrdinalEncoder(categories=[temp])
df1['ord_2'] = oe2.fit_transform(df1[['ord_2']])
df1
## SCALING:
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df0
from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df2
from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df3
from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['id', 'bin_1', 'bin_2', 'nom_0','ord_2'])
df4
```

Titanic Dataset:

```
import pandas as pd
df=pd.read_csv("titanic_dataset.csv")
df
df.drop("Name",axis=1,inplace=True)
df.drop("Ticket",axis=1,inplace=True)
df.drop("Cabin",axis=1,inplace=True)
df.isnull().sum()

df["Age"]=df["Age"].fillna(df["Age"].median())
df["Embarked"]=df["Embarked"].fillna(df["Embarked"].mode()[0])
df.isnull().sum()
df

## ENCODING
import category_encoders as ce
be=ce.BinaryEncoder()
ndf=be.fit_transform(df['Sex'])
ndf
df1=df.copy()
from sklearn.preprocessing import LabelEncoder, OrdinalEncoder
embark=['S','C','Q']
e1=OrdinalEncoder(categories=[embark])
df1['Embarked'] = e1.fit_transform(df[['Embarked']])
df1

## SCALING
from sklearn.preprocessing import MinMaxScaler
sc=MinMaxScaler()
df0=pd.DataFrame(sc.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df0
from sklearn.preprocessing import StandardScaler
sc1=StandardScaler()
df2=pd.DataFrame(sc1.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df2
from sklearn.preprocessing import MaxAbsScaler
sc2=MaxAbsScaler()
df3=pd.DataFrame(sc2.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df3
from sklearn.preprocessing import RobustScaler
sc3=RobustScaler()
df4=pd.DataFrame(sc3.fit_transform(df1),columns=['PassengerId', 'Survived', 'Pclass', 'Sex','Age','SibSp','Parch','Fare','Embarked'])
df4
```

# OUTPUT

(i) Data.csv

![image](https://user-images.githubusercontent.com/118626456/234177568-2f671093-e50c-430c-8c63-fc4b408af713.png)

![image](https://user-images.githubusercontent.com/118626456/234177629-ddd18c9e-d0a0-489f-bf43-9a37c65db332.png)

![image](https://user-images.githubusercontent.com/118626456/234177646-c0cdc21e-7dea-424b-8ba3-c71b192f30cf.png)

![image](https://user-images.githubusercontent.com/118626456/234177654-f9ca7182-5d63-482f-9c01-de13eeb29070.png)

Minmax scaling:

![image](https://user-images.githubusercontent.com/118626456/234177698-9e9d4541-d9e4-4045-99c9-c73ad551c9ab.png)

Standard scaling:

![image](https://user-images.githubusercontent.com/118626456/234177842-8d11080e-b54d-4bb6-bcc8-e7c9653becf8.png)

Maxabs scaling:

![image](https://user-images.githubusercontent.com/118626456/234177871-3489d322-9aca-4a41-aabc-342b0d267132.png)

Robust scaling:

![image](https://user-images.githubusercontent.com/118626456/234177905-ef503be5-cff3-4785-af73-d2d830d7e5fb.png)

(ii) Encoding data.csv

![image](https://user-images.githubusercontent.com/118626456/234177973-1722ae0d-3a47-4c3a-8f9a-c27d85b84337.png)

![image](https://user-images.githubusercontent.com/118626456/234178024-619f0365-4a53-4ed5-81e8-ab200ccb99fc.png)

![image](https://user-images.githubusercontent.com/118626456/234178097-6ed7964e-222d-4b52-af05-ec7c734da936.png)

Minmax scaler:

![image](https://user-images.githubusercontent.com/118626456/234178103-85e5bf56-dc88-42a5-8b28-6abf1c44bf70.png)

Standard scaler:

![image](https://user-images.githubusercontent.com/118626456/234178150-6ad2e965-fcd5-4cd0-9829-a3fc28fbff08.png)

Maxabs scaler:

![image](https://user-images.githubusercontent.com/118626456/234178204-b9841eca-f464-4b88-992d-78ac3886efe1.png)

Robust scaler:

![image](https://user-images.githubusercontent.com/118626456/234178230-5c8440d5-edfe-4dbf-91a0-f58c60f69047.png)

(iii) Titanic dataset.csv:

![image](https://user-images.githubusercontent.com/118626456/234178300-6fb8a241-b60f-4f3a-b6e3-38a70482d856.png)

Removing null values:

![image](https://user-images.githubusercontent.com/118626456/234178267-1b7edb6f-34db-4870-8835-35e923bcedac.png)

![image](https://user-images.githubusercontent.com/118626456/234178319-53fa02f8-d960-4d1a-ae73-2030b348edc7.png)

Encoding:

![image](https://user-images.githubusercontent.com/118626456/234178400-86b839b8-91e7-4f5e-a882-1af2e5af8598.png)

![image](https://user-images.githubusercontent.com/118626456/234178422-bcd09e3b-9489-4602-aa70-34e8e9ecd85f.png)

Minmax scaler:

![image](https://user-images.githubusercontent.com/118626456/234178469-940dc8b4-2f80-432e-8464-a9e8080d41b6.png)

Standard scaler:

![image](https://user-images.githubusercontent.com/118626456/234178553-1fa4ae88-cb71-423b-acca-452b09a22d2e.png)

Maxabs scaler:

![image](https://user-images.githubusercontent.com/118626456/234178618-1a2a11de-5419-46e6-8636-3607bca657d5.png)

Robust scaler:

![image](https://user-images.githubusercontent.com/118626456/234178680-225e91e9-ece4-4c24-98dd-fbac5450f0b1.png)


Result:

Thus the Feature Generation and Feature Scaling process is applied to the given data set.
