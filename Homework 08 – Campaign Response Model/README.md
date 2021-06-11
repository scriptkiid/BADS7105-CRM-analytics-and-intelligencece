## Campaign Response Model
[![](https://img.shields.io/badge/-Improvement-blue)](#) [![](https://img.shields.io/badge/-Classification-blue)](#) [![](https://img.shields.io/badge/-Logistic-Regression-blue)](#) [![](https://img.shields.io/badge/-XGBoost-blue)](#) [![](https://img.shields.io/badge/-Resampling-blue)](#) [![](https://img.shields.io/badge/-Cross-Varidation-blue)](#)

## Dataset
Retail Data 2 ไฟล์
1. Retail_Data_Transactions.csv เป็นไฟล์ข้อมูล Transections มีข้อมูลทั้งหมด 125,001 ข้อมูล
2. Retail_Data_Response.csv เป็นไฟล์ข้อมูลที่บอกการตอบกลับของลูกค้า มีข้อมูลทั้งหมด 6,885 ข้อมูล

## Objective
เพิ่มประสิทธิ์ภาพการทำงานของ model จากตัวอย่างไฟล์ Campaign Response Model.ipynb

## Implementations
- Feature Engineering โดยการเพิ่มตัวแปร AOU, ticket_size, ticket_size_std, ticket_size_med, ticket_size_min, ticket_size_max
- Resampling data โดยใช้วิธีการ Undersampling, Oversampling, SMOTE, SMOTE-Tomek Links
- Cross varidation โดยใช้วิธีการ StratifiedKFold 5 Folds
- Tuning hyperparameter

## Models
- Logistic Regression
- XGBoots

## Result
- Logistic Regression

| model | resampler | train-mean | train-min | train-max | test-mean | test-min | test-max |
| --- | --- | --- | --- | --- | --- | --- | --- |
| logistic | n/a	        | 0.729881 | 0.702982 | 0.750309 | 0.734630 | 0.637293 | 0.897677 |
| logistic | undersampler	| 0.732716 | 0.706441 | 0.755415 | 0.729527 | 0.634330 | 0.887469 |
| logistic | oversampler	| 0.730112 | 0.701658 | 0.750258 | 0.727977 | 0.631895 | 0.877567 |
| logistic | smote	        | 0.746499 | 0.729031 | 0.757130 | 0.695957 | 0.635696 | 0.783240 |
| logistic | smote-tomek	| 0.749581 | 0.713968 | 0.769619 | 0.700381 | 0.634323 | 0.797576 |

- XGBoots

| model | resampler | train-mean | train-min | train-max | test-mean | test-min | test-max |
| --- | --- | --- | --- | --- | --- | --- | --- |
| xgboost | n/a	            | 0.944305 | 0.940354 | 0.946454 | 0.709524 | 0.613217 | 0.899374 |
| xgboost | undersampler	| 0.982189 | 0.978072 | 0.984936 | 0.702638 | 0.617733 | 0.863163 |
| xgboost | oversampler	    | 0.974203 | 0.972987 | 0.975349 | 0.708742 | 0.619714 | 0.896726 |
| xgboost | smote	        | 0.970229 | 0.966980 | 0.977068 | 0.689306 | 0.602769 | 0.886052 |

## Conclutions
จากการทดลองพบว่า
- เมื่อสร้างตัวแปรจากข้อมูลที่มีอยู่เพิ่มทำให้เมื่อไปรัน model จะได้ประสิทธิ์ภาพที่ดีขึ้น
- การทำ Resampling data โดยวิธีการต่าง ๆ ทำให้ประสิทธิ์ภาพที่ดีขึ้น แต่ขึ้นอยู่กับ model ที่ใช้ด้วย
- การทำ Cross varidation ส่งผลอย่างมากในการเพิ่มประสิทธิ์ภาพ
- การทำ Tuning hyperparameter ไม่ช่วยเท่าไหร่ และใช้ระยะเวลานานในการหาค่า hyperparameter