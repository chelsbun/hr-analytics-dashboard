# HR Analytics Dashboard

**Live Demo:** [https://chelsbun.github.io/hr-analytics-dashboard](https://chelsbun.github.io/hr-analytics-dashboard)

A comprehensive HR analytics system demonstrating advanced SQL skills and Workday-ready capabilities. Built to showcase enterprise-level data analysis and integration workflows for HR systems.

## 🎯 Project Overview

This dashboard automates the manual data audits I performed during my time at Insperity, reducing audit time from 30+ minutes to 3 seconds. It simulates real-world Workday functionality including data integration, custom reporting, and business process workflows.

## ✨ Key Features

### 📊 Advanced SQL Analytics
- **Data Quality Audit**: Automated validation of employee records, benefits enrollment, and payroll data
- **Benefits Cost Analysis**: Multi-dimensional cost trending with year-over-year comparisons
- **Demographic Analysis**: Population breakdowns with enrollment patterns by salary bands

### 🔌 Integration Tools Simulation
- **EIB-Style Data Import**: File upload, validation, and error handling workflows
- **Real-time Status Monitoring**: Integration health dashboard with activity logging
- **Multi-system Configuration**: Source system management and sync scheduling

### 📋 Report Writer & Calculated Fields
- **Interactive Report Builder**: Drag-and-drop field selection with live preview
- **Advanced Calculations**: Custom business logic with Workday-style formulas
- **Parameter-driven Reports**: Dynamic filtering and export capabilities

## 🛠️ Technical Skills Demonstrated

### Database & SQL
- Complex CTEs (Common Table Expressions)
- Window functions for trend analysis
- Multi-table JOINs across normalized schema
- Data validation and quality checks
- Performance optimization with indexing

### Frontend Development
- Responsive HTML/CSS design
- Interactive JavaScript functionality
- Real-time data visualization
- Professional enterprise UI/UX

### Integration Concepts
- ETL workflow simulation
- Error handling and logging
- File processing and validation
- API integration patterns

## 🏗️ Architecture

```
Frontend (HTML/CSS/JS)
├── Dashboard Interface
├── Query Execution Engine
└── Results Visualization

Database (Supabase/PostgreSQL)
├── Clients (Multi-tenant architecture)
├── Employees (Cross-client employee data)
├── Benefits Plans (Plan catalog)
├── Enrollments (Employee-plan relationships)
└── Payroll Records (Benefits deductions)
```

## 💼 Business Context

This project demonstrates understanding of:
- **HR data complexity** and compliance requirements
- **Multi-client architecture** typical in PEO/HRO environments
- **Benefits administration** workflows and calculations
- **Data quality challenges** in enterprise HR systems

## 🚀 Getting Started

1. **Visit the live demo**: [chelsbun.github.io/hr-analytics-dashboard](https://chelsbun.github.io/hr-analytics-dashboard)
2. **Click "Connect to Database"** (credentials pre-configured)
3. **Explore the analytics**:
   - Start with Data Quality Audit (shows real business value)
   - Try Benefits Cost Analysis (demonstrates SQL complexity)
   - Explore Integration Tools (shows Workday readiness)
   - Build custom reports (showcases calculated fields)

## 📈 Sample Queries

### Data Quality Audit (CTE with UNION ALL)
```sql
WITH data_quality_issues AS (
  SELECT 
    'Missing/Invalid SSN' as issue_type,
    c.company_name,
    e.first_name || ' ' || e.last_name as employee_name,
    'HIGH' as priority
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
  COUNT(*) as issue_count,
  STRING_AGG(employee_name, '; ') as affected_employees
FROM data_quality_issues
GROUP BY company_name, issue_type;
```

## 🎓 Background

Created by [Chelsea Bonyata](https://linkedin.com/in/chelsea-bonyata) as part of a Computer Science degree program at University of Houston-Downtown. Combines 5+ years of professional HR experience (including manual data audits at Insperity) with modern software development skills.

## 🔧 Technologies Used

- **Frontend**: HTML5, CSS3, JavaScript (ES6)
- **Database**: PostgreSQL (Supabase)
- **Analytics**: Advanced SQL, CTEs, Window Functions
- **Deployment**: GitHub Pages
- **Design**: Responsive web design, CSS Grid/Flexbox

## 📞 Contact

**Chelsea Bonyata**
- 📧 Email: chelseabonyata@gmail.com
- 💼 LinkedIn: [linkedin.com/in/chelsea-bonyata](https://linkedin.com/in/chelsea-bonyata)
- 🐙 GitHub: [github.com/chelsbun](https://github.com/chelsbun)

---

*This project demonstrates enterprise-level HR analytics capabilities and readiness for roles involving Workday development, SQL reporting, and HR system integration.*
