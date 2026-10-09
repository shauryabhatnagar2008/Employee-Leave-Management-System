# Employee Leave Management System (ELMS)

A Java Swing desktop application with MySQL backend built using the MVC + DAO architecture, styled with **FlatLaf Dark** and custom **Graphics2D** glassmorphic components, animations, and role-based workflows.

---

## 🌟 Key Features

- **Role-Based Access Control**:
  - **Employee**: View leave balances, apply for leave (with working days computation), track request status, view complete history.
  - **Manager**: Review and approve/reject team leave requests with custom remarks, view team leave calendar/records.
  - **Admin**: Full analytics dashboard, add/edit/deactivate staff, reset passwords, manage system-wide leave requests, and export reports to CSV.
- **Modern UI / Aesthetics**:
  - Deep dark indigo & violet gradient palette (`FlatDarkLaf` + customized `UIManager`).
  - Glassmorphic card panels with rounded corners and glowing borders.
  - 60 FPS animated hover buttons and background floating orbs.
  - Interactive collapsible sidebar navigation.
  - Customized tables with status badges (Pending, Approved, Rejected, Cancelled).

---

## 🗄️ Database Setup

1. Open your MySQL client (MySQL Workbench, phpMyAdmin, or command-line client).
2. Execute the schema script located at:
   ```bash
   mysql -u root -p < sql/schema.sql
   ```
3. This creates the database `elms_db`, creates all required tables (`users`, `leave_types`, `leave_balances`, `leave_requests`), and seeds default accounts and leave quotas.

---

## ⚙️ Configuration

Configure your database connection in `config.properties` at the project root:

```properties
db.url=jdbc:mysql://localhost:3306/elms_db?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
db.user=root
db.password=your_mysql_password
```

*(You can also set environment variables `ELMS_DB_URL`, `ELMS_DB_USER`, `ELMS_DB_PASSWORD`, or pass `-Delms.db.password=...` at runtime.)*

---

## 🚀 How to Run

### Method 1: Using the Pre-built Standalone JAR
```bash
java -jar target/elms-1.0-jar-with-dependencies.jar
```

### Method 2: Build and Run with Maven Wrapper
```bash
# Build
.\mvnw.cmd clean package -DskipTests

# Run
java -jar target/elms-1.0-jar-with-dependencies.jar
```

---

## 🔑 Demo Credentials

| Role | Employee ID | Password | Access / Capabilities |
|---|---|---|---|
| **Administrator** | `ADMIN001` | `admin@123` | System analytics, Staff CRUD, System-wide requests, CSV export |
| **Manager** | `MGR001` | `manager@123` | Team approvals, Team leave records, KPI metrics |
| **Employee** | `EMP001` | `emp@123` | Apply for leaves, Balance tracking, History |

---

## 📁 Project Architecture

```
src/main/java/com/elms/
├── Main.java                          # Application entry point
├── model/                             # Domain Entities (User, LeaveRequest, LeaveBalance, LeaveType)
├── dao/                               # Database Access Layer (UserDAO, LeaveRequestDAO, etc.)
├── controller/                        # Business Controllers (Auth, Employee, Manager, Admin)
├── util/                              # Utilities (DBConnection, ThemeManager, DateUtil, PasswordUtil, SessionManager)
└── view/
    ├── LoginFrame.java                # Animated Login Window
    ├── components/                    # UI Components (GlassPanel, AnimatedButton, SidebarNav, etc.)
    ├── employee/                      # Employee Dashboard & Panels
    ├── manager/                       # Manager Dashboard & Approval Panels
    └── admin/                         # Admin Dashboard, Management & Reports Panels
```
