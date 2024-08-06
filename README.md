
# RETAIL TRANSACTION DATASET PROJECT

# PROBLEM STATEMENT 
This is a dataset containing retail transactions from a large retailer, with over 100 thousand records spanning 2 years. Each record represents a single transaction and includes features such as:
- Customer ID (Anonymous)
- Product ID
- Quantity
- Price
- Transaction Date
- Discount Applied
- Payment Method
- Store Location etc.
My goal is to analyze this dataset to determine:

1. The Total Amount by Day Name
2. The Total Amount by Month Name
3. The Total Amount Quarterly
4. The Total Amount Yearly
5. The Total Number of Product sold
6. The Total Amount of Discount Applied for each Payment Method.

# LIBRARY USED
1. Matplotlib
2. Pandas
3. Numpy

# STEPS
- Rounding up the TotalAmount column to a nearest decimal place. Retail["TotalAmount"]=Retail["TotalAmount"].round().
- Converting the TransactionDate column from an object type to datetime type. Retail["TransactionDate"]=pd.to_datetime(Retail["TransactionDate"])

1. TOTAL AMOUNT BY DAY NAME
Retail["Day_Name"]=Retail["TransactionDate"].dt.day_name()
DayName=Retail.groupby("Day_Name")["TotalAmount"].sum()
DayName

Name=DayName.index  
Number=DayName.values

plt.barh(Name,Number)
plt.title("TRANSACTION PER DAY", fontsize=15, fontstyle="italic", fontweight="bold")  
plt.savefig("TRANSACTION PER DAY")  
plt.show()

![TRANSACTION PER DAY](https://github.com/user-attachments/assets/f7f97d47-6bc8-42de-b483-952e41858e8e)

2. TOTAL AMOUNT BY MONTH NAME
Retail["Month_Name"]=Retail["TransactionDate"].dt.month_name()
MonthName=Retail.groupby("Month_Name")["TotalAmount"].sum().round()  
MonthName

Name1=MonthName.index  
Number1=MonthName.values

plt.plot(Name1,Number1,marker="o")  
plt.title("TRANSACTION PER MONTH", fontstyle="oblique", fontsize=15, fontweight="bold")
plt.xlabel("Month")  
plt.ylabel("Total Amount")  
plt.savefig("TRANSACTION PER MONTH")  
plt.show()

![TRANSACTION PER MONTH](https://github.com/user-attachments/assets/9a76af9c-bde8-4f76-8d9c-4a01a02852ee)

3. TOTAL AMOUNT BY QUARTER 
Retail["Quarter"]=Retail["TransactionDate"].dt.quarter
Quarter=Retail.groupby("Quarter")["TotalAmount"].sum().round()
Quarter

Name2=Quarter.index  
Number2=Quarter.values

plt.pie(Number2,labels=Name2,autopct="%1.0f%%",shadow=True,explode=[0,0.1,0,0.1])  
plt.title("TRANSACTION PER QUARTER", fontstyle="italic", fontsize=15, c="#808000",fontweight="bold")  
plt.savefig("TRANSACTION PER QUARTER")  
plt.show()

![TRANSACTION PER QUARTER](https://github.com/user-attachments/assets/49488021-fb16-4d72-88b8-1f1209af5585)

4. TOTAL AMOUNT YEARLY 
Retail["Year"]=Retail["TransactionDate"].dt.year  
Years=Retail.groupby("Year")["TotalAmount"].sum().round()  
Years

Name3=Years.index  
Number3=Years.values

plt.bar(Name3,Number3,color="g")  
plt.title("TRANSACTION PER YEAR", fontsize=15, fontstyle="italic", fontweight="bold", c="purple")  
plt.xlabel("Year")  
plt.ylabel("Total Amount")  
plt.savefig("TRANSACTION PER YEAR")  
plt.show()

![TRANSACTION PER YEAR](https://github.com/user-attachments/assets/278ecac8-6cd9-46a7-bb4c-e40e5027cd3c)

5. TOTAL NUMBER OF PRODUCT SOLD 
ProductCat=Retail.groupby("ProductCategory")["TotalAmount"].count()
ProductCat

Name4=ProductCat.index  
Number4=ProductCat.values

plt.pie(Number4,labels=Name4,shadow=True,autopct="%1.0f%%",explode=[0.1,0.1,0,0])  
plt.title("TOTAL NUMBER OF PRODUCTS SOLD", fontstyle="italic", fontweight="bold", fontsize=12,c="g")  
plt.savefig("TOTAL NUMBER OF PRODUCT SOLD")  
plt.show()

![TOTAL NUMBER OF PRODUCT SOLD](https://github.com/user-attachments/assets/edb215d2-4364-4a9d-ba5a-84f236fb3360)

6. TOTAL AMOUNT OF DISCOUNT APPLIED FOR EACH PAYMENT METHOD
PayMet=Retail.groupby("PaymentMethod")["DiscountApplied(%)"].sum()
PayMet

Name5=PayMet.index  
Number5=PayMet.values

plt.plot(Name5,Number5,marker="+")  
plt.title("DISCOUNT APPLIED FOR EACH PAYMENT METHOD", fontsize=10, fontstyle="oblique", fontweight="bold",c="b")  
plt.xlabel("Payment Method")  
plt.ylabel("Discount Applied(%)")  
plt.savefig("DISCOUNT APPLIED")
plt.show()

![DISCOUNT APPLIED](https://github.com/user-attachments/assets/c6921d32-a99c-4da3-a41a-786ac29cc256)

# SCREENSHOT OF THE CHART IN SUBPLOT
fig,Retails=plt.subplots(nrows=2,ncols=3,figsize=(14,8))  
fig.suptitle("RETAIL TRANSACTION REPORT", fontsize=40, fontstyle="normal", fontweight="bold", c="#FF0000")  
Retails[0,0].barh(Name,Number)  
Retails[0,1].plot(Name1,Number1,marker="o")  
Retails[0,2].pie(Number2,labels=Name2, autopct="%1.0f%%", shadow=True, explode=[0,0.1,0,0.1])  
Retails[1,0].bar(Name3,Number3,color="g")  
Retails[1,1].pie(Number4,labels=Name4, shadow=True, autopct="%1.0f%%", explode=[0.1,0.1,0,0])  
Retails[1,2].plot(Name5,Number5,marker="+")  
Retails[0,0].set(title="TRANSACTION PER DAY")  
Retails[0,1].set(title="TRANSACTION PER MONTH")  
Retails[0,2].set(title="TRANSACTION PER QUARTER")  
Retails[1,0].set(title="TRANSACTION PER YEAR")  
Retails[1,1].set(title="TOTAL NUMBER OF PRODUCTS SOLD")
Retails[1,2].set(title="DISCOUNT APPLIED FOR EACH PAYMENT METHOD")  
plt.tight_layout()  
plt.savefig("RETAIL")  
plt.show()

![RETAIL](https://github.com/user-attachments/assets/5af488cc-4842-4910-89b8-16d7c525f750)
