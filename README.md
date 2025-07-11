IEEE-CIS-Fraud-Detection - Machine learning Assignment 2 - gtoro22

კონკურსის მიზანი იყო დაგვედგინა და ამოგვეცნო თაღლითური საბანკო ტრანზაქციები. მოცემულლი გვქონდა 2 ფართომასშტაბიანი მონაცემთა სეტი Vesta Corporation-ის მიერ.
მონაცემთა ნაკრები შეიცავს ტრანზაქციების და იდენტიფიკაციის მონაცემებს. ესწავლისას გამოჩნდა , რომ data იყო დაუბლანსებელი, მის მხოლოდ 3.5 % ს შეადგენდა Fraud-ს და გვქონდა დიდი რაოდენობით null მნიშვნელობები. 
საბოლოოდ ჩემი მთავარი მიზანი იყო მონაცემების სწორად დამუშავება , დაბალანსება და რაიმე ნიმუშის დაჭერა რათა სწორად გამომეცნო სამიზნე

ჩემი მიდგომა

პრობლემის გადასაჭრელად გამოვიყენე სხვადასხვა მოდელი, რომელიც კარგად მუშაობს კლასიფიკაციის ამოცანებში და 
შეუძლია ავტომატურად აირჩიოს მნიშვნელოვანი ფიჩერები. მთავარი ფოკუსი იყო მონაცემთა წინასწარი დამუშავება და ფიჩერების სელექცია.

რეპოზიტორიის სტრუქტურა

model_experiment_{მოდელის არქიტექტურა}.ipynb

თითოეულ კლასში გამოყენებულია Cleaning, Feature Engineering, Feature Selection და Trainin ნაბიჯები

model_inference.ipynb
ამ ფაილში კი მაქვს საბოლოოდ შერჩეული მოდელის (RandomForest) დალოუდება, რომელმაც ყველაზე კარგი შედეგი აჩვენა 

მონაცემთა დამუშავება

Feature Engineering

ტრანზაქციების და იდენტიფიკაციის მონაცემთა გაერთიანება
დროის მახასიათებლების (TransactionDT) გარდაქმნა
კატეგორიული ცვლადების დამუშავება

Label Encoding გამოყენებულია კატეგორიული ცვლადებისთვის
NaN მნიშვნელობების შევსება მოდალური მნიშვნელობებით ან სპეციალური მნიშვნელობით
Cleaning მიდგომები

მონაცემთა ნაკრების ზომის შემცირება მეხსიერების დაზოგვისთვის
არასაჭირო სვეტების ამოშლა
Feature Selection

Correlation Analysis - მაღალი კორელაციის მქონე ფიჩერების ამოშლა
Feature Importance - Random Forest-ის მიერ გამოთვლილი მნიშვნელოვანი ფიჩერების შერჩევა

მოდელის ტრენინგი

ტესტირებული მოდელები

ძირითადი Random Forest მოდელი
გამოყენებული იქნა class_weight პარამეტრი კლასების ბალანსისთვის
Hyperparameter ოპტიმიზაცია

GridSearchCV გამოყენებულია ოპტიმალური პარამეტრების მოსაძებნად
ძირითადი პარამეტრები: n_estimators, max_depth, min_samples_split
საბოლოო მოდელის შერჩევა

შეირჩა Random Forest მოდელი მისი ინტერპრეტაციის სიმარტივის და კარგი შედეგების გამო არაწონასწორებული კლასების პრობლემაში.

MLflow Tracking: https://dagshub.com/giorgitorro/FraudDetection_gtoro22.mlflow/#/experiments/0?searchFilter=&orderByKey=attributes.start_time&orderByAsc=false&startTime=ALL&lifecycleFilter=Active&modelVersionFilter=All+Runs&datasetsFilter=W10%3D

MLflow გამოყენებულია ექსპერიმენტების ტრეკინგისთვის. ყველა ექსპერიმენტი ჩაწერილია DagsHub-ზე

ჩაწერილი მეტრიკები
Accuracy
Precision
Recall
F1 Score
ROC AUC

საუკეთესო მოდელის შედეგები

საუკეთესო მოდელმა მიაღწია შემდეგ შედეგებს ვალიდაციის სეტზე:

ROC AUC: 0.92
F1 Score: 0.65
Precision: 0.85
Recall: 0.55
მოდელმა კარგად გაუმკლავდა კლასების დისბალანსს და აჩვენა კარგი შედეგები AUC მეტრიკაზე.

