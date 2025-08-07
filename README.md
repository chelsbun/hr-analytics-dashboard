# HR Analytics Dashboard

**Live Demo:** [chelsbun.github.io/hr-analytics-dashboard](https://chelsbun.github.io/hr-analytics-dashboard)  
*By Chelsea Bonyata | Insperity Software Engineer Candidate*

---

## 🚀 TL;DR

Automates HR data audits, compliance, and reporting—transforming 30-minute manual processes into 3-second analytics.  
Built with advanced SQL, dynamic JavaScript, and Workday-style integrations. Inspired by real-world Insperity experience.

---

## 🎯 Project Overview

The HR Analytics Dashboard is a comprehensive HR analytics and reporting system built for modern HRIS/PEO/Workday use cases.  
It automates complex data audits, benefits analytics, demographic reports, and simulates real-world data integration (EIB) workflows—mirroring the challenges I encountered as an HR specialist at Insperity.

**Key value:**
- Automates manual audits (missing/invalid SSNs, benefit compliance, payroll checks)
- Delivers actionable business insights (cost analysis, enrollment patterns)
- Simulates Workday-style reporting, data import, and integration

---

## 💼 Business Context

This project directly reflects the *actual pain points* faced in HR operations:

- Reduces compliance and audit errors that can trigger IRS penalties or billing issues
- Models a **multi-client environment** (like Insperity/PEO/HRO) with cross-client analytics
- Brings Workday-level automation and business logic to everyday HR tasks

---

### What Makes This Stand Out?

- **Not just a CRUD dashboard:** all features mirror real HR business processes  
- **Built with actual SQL and data models** used in enterprise HR/PEO environments  
- **Demonstrates both technical and domain expertise**

---

## ✨ Key Features & Impact

### 📊 Advanced SQL Analytics

- **Data Quality Audit:** Instantly finds missing/invalid SSNs, benefit mismatches, or payroll errors—compliance issues surface in seconds, not hours.
- **Benefits Cost Analysis:** Year-over-year cost breakdowns and multi-dimensional trending across clients—enables proactive cost management.
- **Demographic Analysis:** Salary band and enrollment reports—spot trends, disparities, or opportunities for engagement.

### 🔌 Integration Tools Simulation

- **EIB-Style Data Import:** Drag-and-drop file upload, real-time validation, error handling, and metrics.  
  Activity logs and import statuses mirror what HR teams use daily in Workday.
- **Multi-System & Sync Management:** Simulate data sync across multiple HRIS systems (Insperity HRIS, ADP, BambooHR, etc.), with configuration for scheduling and error handling.

### 📋 Report Writer & Calculated Fields

- **Interactive Report Builder:** Drag-and-drop fields, live report preview, export, and schedule.
- **Workday-Style Calculations:** Custom business formulas (e.g., Years of Service, % of Salary, Total Compensation) with readable syntax.

---

## 🛠️ Technical Skills Demonstrated

- **Database & SQL:** Advanced CTEs (Common Table Expressions), UNION ALL, window functions, multi-table JOINs, data validation
- **Frontend Development:** Responsive HTML/CSS, modern JavaScript (ES6+), dynamic UI/UX, real-time visualization
- **Integration Concepts:** Simulated ETL workflows, file processing, error handling, API integration patterns

---

## 🏗️ Architecture

- **Frontend (HTML/CSS/JS)**
  - Dashboard Interface
  - Query Execution Engine
  - Results Visualization
- **Database (Supabase/PostgreSQL)**
  - Clients (multi-tenant support)
  - Employees (cross-client, normalized)
  - Benefits Plans (catalog)
  - Enrollments (employee-plan mapping)
  - Payroll Records (deductions, gross pay)

---

## 📝 Sample Business Query

```sql
WITH data_quality_issues AS (
  SELECT 
    'Missing/Invalid SSN' AS issue_type,
    c.company_name,
    e.first_name || ' ' || e.last_name AS employee_name,
    'HIGH' AS priority
  FROM employees e
  JOIN clients c ON e.client_id = c.client_id
  WHERE e.ssn IS NULL

  UNION ALL

  SELECT 
    'Terminated Employee Active Benefits',
    c.company_name,
    e.first_name || ' ' || e.last_name,
    'HIGH'
  FROM employees e
  JOIN clients c ON e.client_id = c.client_id
  JOIN enrollments en ON e.employee_id = en.employee_id
  WHERE e.status = 'TERMINATED' AND en.status = 'ACTIVE'
)
SELECT 
  company_name,
  issue_type,
  COUNT(*) AS issue_count,
  STRING_AGG(employee_name, '; ') AS affected_employees
FROM data_quality_issues
GROUP BY company_name, issue_type;
```

---

## 🏆 Technical Challenges Overcome

- Built multi-tenant queries for cross-client analytics and reporting
- Automated error handling for ETL/data import simulations
- Modeled real Workday business logic in JavaScript and SQL
- Designed a fully responsive dashboard for all device sizes

---

## 🖥️ Try It Yourself! (Demo Instructions)

- **Go to:** [Live Demo](https://chelsbun.github.io/hr-analytics-dashboard)
- **Click:** “Connect to Database” (demo credentials are pre-loaded)
- **Explore each feature:**
  - Run Data Quality Audit
  - Try Benefits Cost Analysis
  - Simulate an Integration Import
  - Build and preview custom reports
- *(No login required!)*

---

## 👤 For Recruiters / Workday Teams

This project proves my ability to:
- Automate and optimize compliance and audit workflows
- Build scalable analytics, integration, and reporting tools for HR
- Integrate complex business logic from actual PEO/Workday experience
- Translate real HR pain points into working software

*Ask me about how these tools could improve your HR, payroll, or compliance operations!*

---

## 🎓 Background

**Chelsea Bonyata**  
- B.S. Computer Science, University of Houston-Downtown (in progress)  
- 5+ years HR/benefits experience (Insperity Health & Welfare Specialist)  
- Hands-on audit, reporting, and integration background

---

## 🔧 Technologies Used

- **Frontend:** HTML5, CSS3, JavaScript (ES6+)
- **Database:** PostgreSQL (Supabase)
- **Analytics:** Advanced SQL, CTEs, Window Functions
- **Deployment:** GitHub Pages
- **Design:** Responsive web design, CSS Grid/Flexbox

---

## 📞 Contact

Chelsea Bonyata  
📧 [chelseabonyata@gmail.com](mailto:chelseabonyata@gmail.com)  
💼 [LinkedIn](https://www.linkedin.com/in/chelsea-bonyata-477236152/)  
🐙 [GitHub](https://github.com/chelsbun)

---

**Ready to bring real automation and analytics to your HR systems? Let’s talk!**
