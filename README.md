# RDS-MYSQL-DATABASE-CONNECT-WITH-SQLECTRON



✅ Create an **RDS MySQL database**
✅ Connect it with **Sqlectron**
✅ Create and use a database inside RDS


---

## ✅ 1. Create RDS MySQL Database in AWS

### 🔹 Step-by-step:

1. Go to AWS Console → RDS
2. Click **Create Database**
3. Choose:

   * **Engine**: MySQL
   * **Version**: Choose latest (e.g., 8.0.35)
   * **Templates**: Free Tier (if available)
4. Settings:

   * DB Identifier: `university-db`
   * Master Username: `admin`
   * Password: `yourStrongPassword123`
5. Connectivity:

   * VPC: Default
   * Public Access: ✅ Yes
   * Availability Zone: Any
   * VPC security group: Choose or create one with **port 3306 open**
6. Click **Create database**
7. Wait till status = “Available”

---

## ✅ 2. Get Endpoint

Go to **Databases > university-db**, note the **Endpoint** (e.g., `university-db.xxxxx.rds.amazonaws.com`)
This is used in Sqlectron to connect.

---

## ✅ 3. Open Port 3306 in Security Group

1. Go to **EC2 → Security Groups**
2. Find the one attached to your RDS
3. In **Inbound rules**:

   * Type: MySQL/Aurora
   * Port: `3306`
   * Source: `0.0.0.0/0` (for testing) or your IP

---

## ✅ 4. Connect using Sqlectron

### 🔸 Install Sqlectron:

* [Download here](https://sqlectron.github.io/)

### 🔸 Add New Connection:

* Client: `mysql`
* Name: `university-db`
* Host: `<your RDS endpoint>`
* Port: `3306`
* Database: leave blank (we’ll create it)
* Username: `admin`
* Password: `yourStrongPassword123`

✅ Click **Test** → then **Connect**

---

## ✅ 5. Create a Database inside RDS

Once connected in Sqlectron, open a new SQL tab and run:

```sql
CREATE DATABASE UniversityDB;
USE UniversityDB;

CREATE TABLE Course (
  CourseID INT PRIMARY KEY,
  CourseName VARCHAR(100),
  Rating DECIMAL(3,1)
);

INSERT INTO Course VALUES
(1, 'AZ-204 Developing Azure solutions', 4.5),
(2, 'AZ-303 Architecting Azure solutions', 4.6),
(3, 'DP-203 Azure Data Engineer', 4.7);

SELECT * FROM Course;
```



