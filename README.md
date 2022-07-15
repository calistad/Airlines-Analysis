# Airlines-Analysis

## Overview
This analysis is to predict whether a given flight will be delayed, given the information of the scheduled departure.

## Purpose
Which machine learning algorithm would achieve the best performance for prediction?

## Findings
This is a large dataset with 9 columns and 539,383 rows.

![Screen Shot 2022-07-14 at 8 38 29 PM](https://user-images.githubusercontent.com/88747464/179123844-6d430fa6-1459-45c8-bbbf-f90aeeca0c96.png)

### Analyze numeric attributes

![Screen Shot 2022-07-14 at 8 41 14 PM](https://user-images.githubusercontent.com/88747464/179124142-0fd60e3e-c515-4f89-aa9c-0569d1ee65ba.png)

Take a closer check on the day of the week and flight length attributes.

![Screen Shot 2022-07-14 at 8 41 23 PM](https://user-images.githubusercontent.com/88747464/179124183-a0f0fad1-06b7-4f4b-ae2e-c1b24d87097b.png)
![Screen Shot 2022-07-14 at 8 41 30 PM](https://user-images.githubusercontent.com/88747464/179124192-aec473ce-2298-44eb-827e-683953aa0b83.png)

Although there are outliers in the length attribute, they seem reasonable and might be related to the cause of the delay.

#### Distribution of each attribute of whether or not delay.

![Screen Shot 2022-07-14 at 8 45 53 PM](https://user-images.githubusercontent.com/88747464/179124641-bc37d799-2f6e-48da-bf3a-7490594e5264.png)
![Screen Shot 2022-07-14 at 8 46 00 PM](https://user-images.githubusercontent.com/88747464/179124648-29a1433d-017e-4a80-ad39-0a4aee652f77.png)

![Screen Shot 2022-07-14 at 8 49 02 PM](https://user-images.githubusercontent.com/88747464/179124818-cae92069-6e1a-48c2-bc2b-fd1be83b165e.png)
![Screen Shot 2022-07-14 at 8 46 07 PM](https://user-images.githubusercontent.com/88747464/179124657-3df4c126-9a88-4d6b-ada1-e0d6315a7961.png)

Flights with shorter times are more tend to be on time.

### Analyze categorical attributes

![Screen Shot 2022-07-14 at 8 51 22 PM](https://user-images.githubusercontent.com/88747464/179125026-1c1ecbc0-af50-4c80-8e22-263e968b4e9a.png)
![Screen Shot 2022-07-14 at 8 51 29 PM](https://user-images.githubusercontent.com/88747464/179125031-9802d7b2-a0de-406b-a75c-da082de0934f.png)

WN airline has the most count of flights and the most amount of delays. YV airline has the least amount of delays.

#### Prepared dataset for training after categorical encoding.

![Screen Shot 2022-07-14 at 8 54 27 PM](https://user-images.githubusercontent.com/88747464/179125294-428f7938-1110-47cc-ab0b-b0e3d252869f.png)

## Results

| Decision Tree Classification | Random Forest Classification | 
| --- | --- | 
| Accuracy: 62.5% | Accuracy: 61.3% |
| ![Screen Shot 2022-07-14 at 9 35 15 PM](https://user-images.githubusercontent.com/88747464/179129281-4b2e7df6-5d65-4236-b7bf-81cf98ec8be3.png) | ![Screen Shot 2022-07-14 at 9 39 20 PM](https://user-images.githubusercontent.com/88747464/179129599-e1f00148-12fd-4308-936d-cfb99f70f35e.png) |
| ![Screen Shot 2022-07-14 at 9 35 22 PM](https://user-images.githubusercontent.com/88747464/179129315-e5283c45-54c8-4f57-91c9-e20066235f78.png) | ![Screen Shot 2022-07-14 at 9 39 25 PM](https://user-images.githubusercontent.com/88747464/179129755-17dc713b-ac18-4204-9c10-827598c36f92.png) |
| ![Screen Shot 2022-07-14 at 9 37 52 PM](https://user-images.githubusercontent.com/88747464/179129470-d4fd7ecc-1044-41da-9ad1-682417fe88d5.png) | ![Screen Shot 2022-07-14 at 9 41 18 PM](https://user-images.githubusercontent.com/88747464/179129827-fb7b72bf-b385-4a12-ad98-089e546837c3.png) |
| ROC AUC: 65.4% | ROC AUC: 64.2% |
| ![Screen Shot 2022-07-14 at 9 38 40 PM](https://user-images.githubusercontent.com/88747464/179129516-4065dd36-d148-49c1-9c48-aaa630368090.png) | ![Screen Shot 2022-07-14 at 9 41 26 PM](https://user-images.githubusercontent.com/88747464/179129852-d31dd34e-aa08-49f4-9b70-01a2460408f2.png) |

Since both models do not achieve good performance, I retrieved the feature importance of the attributes.

![Screen Shot 2022-07-14 at 9 44 08 PM](https://user-images.githubusercontent.com/88747464/179130183-ff3de576-8132-4b60-9fb3-2b61449a0cb9.png)

I decide to keep 'Airlines', 'Time', 'Airport_To', and 'Flight' attributes, and drop the last 3 attributes.

![Screen Shot 2022-07-14 at 10 07 29 PM](https://user-images.githubusercontent.com/88747464/179132435-61a32d57-54ef-407c-829b-4981eea98e10.png)

| Voting Classifier | Decision Tree Randomized Cross-validation | Ada Boost |
| --- | --- |  --- |
| Accuracy: 66.3% | Accuracy: 63.1% | Accuracy: 64.8% |
| ![Screen Shot 2022-07-14 at 9 55 40 PM](https://user-images.githubusercontent.com/88747464/179131315-618b0966-261c-44ca-ab45-3dce97f0d786.png) | ![Screen Shot 2022-07-14 at 9 57 13 PM](https://user-images.githubusercontent.com/88747464/179131471-91d500fa-fe79-4053-90b9-0d13dd298f63.png) | ![Screen Shot 2022-07-14 at 10 01 32 PM](https://user-images.githubusercontent.com/88747464/179131895-49dd23b8-1148-4c33-be20-e5b9f32ce083.png) |
| ![Screen Shot 2022-07-14 at 9 55 46 PM](https://user-images.githubusercontent.com/88747464/179132124-10bc6486-c220-4807-9843-83fcfca35721.png) | ![Screen Shot 2022-07-14 at 9 57 18 PM](https://user-images.githubusercontent.com/88747464/179132150-afbf7e2c-c640-469f-beb4-a20f4d62043d.png) | ![Screen Shot 2022-07-14 at 10 01 37 PM](https://user-images.githubusercontent.com/88747464/179132159-57849670-43ed-49a6-8a6d-7e7968df0c40.png) |
| ![Screen Shot 2022-07-14 at 9 55 54 PM](https://user-images.githubusercontent.com/88747464/179131354-6f499712-149c-4716-8b5b-086bf1c1a7ba.png) | ![Screen Shot 2022-07-14 at 9 57 24 PM](https://user-images.githubusercontent.com/88747464/179131532-8536b86e-467d-4a77-b2b8-cb67b228384e.png) | ![Screen Shot 2022-07-14 at 10 01 45 PM](https://user-images.githubusercontent.com/88747464/179132024-b8f6e71e-c0aa-4fb9-b35c-67cda845a370.png) |
| ROC AUC: 71% | ROC AUC: 66% | ROC AUC: 69.4% |
| ![Screen Shot 2022-07-14 at 9 56 03 PM](https://user-images.githubusercontent.com/88747464/179131374-dbe4c373-3db8-4294-b46e-efe3e2deef47.png) | ![Screen Shot 2022-07-14 at 9 57 32 PM](https://user-images.githubusercontent.com/88747464/179131554-3c51f10f-dab9-4987-814c-ccb18e41180e.png) | ![Screen Shot 2022-07-14 at 10 01 54 PM](https://user-images.githubusercontent.com/88747464/179132035-46448ae0-f408-40e2-9354-9ad528f20521.png) |

## Summary
Overall, the predictions of various models do not achieve highly accurate results. The model with the best performance is the voting classifier, which contains the highest accuracy, highest roc-auc score, and shorter run time. 

If the company wants to predict flight delays, the voting classifier is recommended. However, the accuracy is only around 70%, which they should take into consideration.
