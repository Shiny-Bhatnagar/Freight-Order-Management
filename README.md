# Freight-Order-Management - Shipper Scenario
 
## Scenario Overview
A shipper, ElectroTech Inc., needs to transport products from a manufacturing plant in Austin, Texas to multiple distribution centers.

### Features:
- **Freight Order Creation and Tracking**
- **Freight Unit Assignment Using Custom Logic**
- **Integration with Fiori-based Freight Order Tracking App**
- **Custom BAdI Implementation for Cost Calculation**

### Prerequisites:
- SAP S/4 HANA
- SAP Transportation Management (TM) configured
- ABAP Development

## Deployment

### Overview
This project implements a shipper scenario where:
1. Freight Units are created based on delivery orders.
2. Freight Orders are planned and scheduled.
3. Custom Logic is used for freight unit assignment and charge calculation.

### Process Flow:
1. Sales Orders
2. Freight Units are grouped into freight orders based on custom rules.
3. Freight orders are tracked and managed using Fiori.

---

## Configuration Steps: Shipper Scenario

### 1. Define Freight Order Types
- Go to **SPRO** -> **Transportation Management** -> **Freight Unit Management** -> **Define Freight Order Types**.
- Create a new Freight Order type 'ZF0T' to manage the lifecycle of your freight orders.

### 2. Configure Freight Unit Building Rules
- Go to **SPRO** -> **Transportation Management** -> **Freight Unit Management** -> **Define Freight Unit Building Rules**
- Create a new Freight Unit Building Rule 'ZFU_RULE' with the following key configurations:
  - **Splitting Criteria**: Set rules for splitting based on weight, volume, or product category.
  - **Grouping Rules**: Define how multiple orders/deliveries should be combined into a single freight unit.
  - **Source Object**: Map the freight unit creation source to deliveries, orders, or stock transfers.

### 3. Set Up Freight Unit Types
- Navigate to **SPRO** -> **Transportation Management** -> **Freight Unit Management** -> **Define Freight Unit Types**
- Create a Freight Unit type 'ZFUT' and associate it with the building rule 'ZFU_RULE'.

### 4. Define Freight Unit Creation in Integration Settings
- Go to **SPRO** -> **Transportation Management** ->**Integration** -> **Define Freight Unit Creation Creation Settings**
- Map the freight unit type 'ZFUT' to the source object (e.g., sales orders or deliveries)
- Activate the integration so freight units are automatically created when source documents are replicated to SAP TM.
  
  ![Screenshot 2025-01-20 at 3 34 40 PM](https://github.com/user-attachments/assets/e8fb4d1e-55db-4e8b-b9aa-87a37429174e)


### 5. Activate BAdI for Freight Unit Assignment
- Implement the 'Z_CUSTOM_FU_ASSIGNMENT' BAdI to customize how Freight Units are assigned to Freight Orders based on specific business rules, such as:
  - Product type
  - Delivery priority
  - Source and destination locations
### 6. Freight Order Planning and Scheduling 
- Go to SAP TM Cockpit.
- Use the planning view to drag-and-drop Freight Units into Freight Orders.
- Configure automated planning by defining optimizer settings under:
  - **SPRO** -> **Transportation Management** -> ** Transportation Planning** -> **Define Planning Settings**.
    
![Screenshot 2025-01-20 at 3 26 19 PM](https://github.com/user-attachments/assets/f2598904-3b57-46cd-87f5-87ee0dacb74e)
![Screenshot 2025-01-20 at 3 13 49 PM](https://github.com/user-attachments/assets/327ff241-2099-4a7b-b1a4-ca49b158f978)

  

  
