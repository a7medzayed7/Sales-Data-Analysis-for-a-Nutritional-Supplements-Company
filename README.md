# Sales-Data-Analysis-for-a-Nutritional-Supplements-Company
## Phase 1: Understanding the Data (ASK)

### 1. Data Overview and Source
The dataset used in this project was collected from a former engineer who worked on a gym products sales analysis project. The products fall under the category of sports supplements commonly used by athletes, especially bodybuilders, to enhance performance, accelerate muscle recovery, and support muscle growth. 

The dataset includes detailed information about products, such as quantities sold, sales dates, and sales values. It also contains customer data, including geographical locations of sales. Sales cover multiple regions worldwide, enabling the study of purchasing patterns and market trends. 

To ensure privacy, sensitive personal information such as customer names and contact details is excluded. The dataset is used solely for academic purposes.

### 2. Reading and Understanding Data
The dataset consists of multiple interconnected tables:

- **Customers Table:** Customer information including Customer ID, Name, Type, and GeographyKey.  
- **Geography Table:** Linked to Customers via GeographyKey; contains city, state code, state name, country code, country name, and region key.  
- **Regions Table:** Describes geographical regions; linked to Geography via RegionKey.  
- **Products Table:** Contains product details; linked to ProductSubcategory via ProductSubcategoryKey.  
- **Product Subcategory Table:** Links each product to a subcategory and a main category.  
- **Product Cost History Table:** Contains unit cost information per product by Year, Month, CountryCode, and ProductID.  
- **Sales Details Table (Fact Table):** Contains all sales transactions including quantities, revenue, and links to Customers and Products.  
- **Sales Header Table:** Provides general information about each order such as OrderDate, DueDate, ShipDate, DiscountAmount, TotalAmount, SalesAmount.  
- **Returns Table:** Contains returned product details including ReturnQuantity, UnitPrice, and ReturnAmount.

### 3. Analytical Questions (ASK)
The main question driving this analysis is:

**"How can the company's overall performance be evaluated through sales data?"**

Sub-questions include:

#### Revenue & Financial Analysis:
- Total Revenue, Cost, Gross Margin, and Quantities.  
- Average Order Value (AOV).  
- Year-over-Year (YoY) changes in revenue.  
- Top-performing regions, products, and business types.  

#### Customer Behavior Analysis:
- Total number of customers and orders.  
- Percentage of inactive customers.  
- Order frequency and customer retention (Churn Analysis).  
- Impact of new vs. returning customers.  

#### Product Analysis:
- Most profitable price categories.  
- Relationship between product price, revenue, and gross margin.  

#### Returns Analysis:
- Return trends over time and by region.  
- Top returned products.  
- Customer return behavior.  

#### Time Analysis:
- Best and worst months for revenue, cost, and gross margin.  
- Month-over-Month (MoM) and Year-over-Year (YoY) growth rates.  
- Day-to-Year (DTY) cumulative change analysis.  

#### Forecasting:
- Projected sales for 2014 and assessment of growth expectations.

---

## Phase 2: Data Preparation and Cleaning (ETL)

### 1. Extract
Data was imported from Excel worksheets into **Power Query** for further processing. All relevant tables were loaded and documented.

### 2. Transform

#### A. Data Cleaning
- **Validate Data Types:** Ensured correct types for numeric, text, and date fields.  
- **Check Data Structure:** Verified table structures and column consistency.  
- **Remove Duplicates:** Deleted duplicate rows.  
- **Handle Missing Values:** Identified and handled nulls appropriately.  
- **Trim Text Fields:** Removed extra spaces.  
- **Detect Outliers:** Manual inspection to identify abnormal values.  
- **Handle Inconsistent Data:** Standardized formats for city names, product categories, etc.  
- **Find and Replace:** Corrected common data errors.  
- **Check for Data Spillage:** Ensured no overlapping or misaligned columns.

#### B. Data Transformation & Denormalization
- Merged related tables to reduce complexity.  
- Created a **Denormalized Star Schema** for efficient analysis.  
- Benefits of Denormalization:  
  - Simplified reading and analysis.  
  - Improved query performance.  
  - Easier DAX formulas and reporting.  

### 3. Data Modeling
- **Star Schema**:  
  - Fact Tables: `Sales Details`, `Returns`.  
  - Dimension Tables: `Customers`, `Products`, `Regions`, `Geography`.  
- **Relationship Building:**  
  - One-to-Many relationships were created between dimensions and facts.  
- **Customer Dim Table:** Created by merging `Customers`, `Geography`, and `Regions`.  
- **Product Dim Table:** Created by merging `Products` with `Product Subcategories`.  
- **Sales Fact Table:** Combined `Sales Details` with `Sales Header` and `Product Cost History` to include all relevant metrics.  
- **Handling Discounts:**  
## Phase 3: Data Analysis

### Key Metrics Calculated (using DAX in Power BI):
- Revenue, Cost, Gross Margin, Quantity.  
- Number of Customers and Orders.  
- Customers Without Orders.  
- Average Order Value (AOV).  
- Average Orders per Customer.  
- New vs. Retained Customers.  
- Total Returns, Returns Quantity, Return Orders, and Return Customers.  
- Gross Margin %, Cost %, Returns %.

### Top Products Analysis:
- By Revenue, Cost, Gross Margin, Returns, Gross Margin %.  

### Year-over-Year (YoY) Analysis:
- Revenue, Cost, Gross Margin, Total Returns, Returns Quantity, Returns Customers, and Returns Orders.

### Year-to-Date (YTD) KPIs:
- YTD Revenue, YTD Cost, YTD Gross Margin.

### Category Price Analysis:
- Products categorized into:  
- 0–1000  
- 1001–2000  
- >2000  
- Analyzed Revenue, Cost, and Gross Margin by price category.

---

## Phase 4: Visualization (Dashboard)

### Design Principles:
- **Keep It Simple:** Minimalist design for clarity.  
- Limited color palette for readability.  
- Logical layout for smooth visual flow.  

### Dashboards Created:
1. **Overview Dashboard**  
2. **Customer Analysis Dashboard**  
3. **Product Analysis Dashboard**  
4. **Time Analysis Dashboard**  
5. **Returns Analysis Dashboard**  
6. **Location Analysis Dashboard**  

### Color Palette:
- Revenue: Sky Blue `#1FBBE4`  
- Cost: Dark Red `#E74C3C`  
- Gross Margin: Soft Green `#44BE85`  

Each dashboard contains:  
- Top KPIs (Cards)  
- Visual charts (Line, Bar, Column, Matrix)  
- Filters/Slicers for interactivity  
- Icons for navigation between dashboards  

---

## Conclusion
By following the complete **data analytics lifecycle** — from understanding, cleaning, transforming, modeling, analyzing, and visualizing — this project provides clear, actionable insights into the sales of gym supplements. The use of Power BI and DAX enabled detailed analysis across financials, customer behavior, product performance, and returns, facilitating informed decision-making for business optimization.
