#  EduHub MongoDB Database Project

##  Project Overview
A complete **MongoDB database system** for an online e-learning platform called **EduHub**.  
This project demonstrates comprehensive MongoDB skills including **data modeling**, **CRUD operations**, **aggregation pipelines**, **performance optimization**, and **data validation**.

---

##  Project Structure
```
mongodb-eduhub-project/
├── notebooks/
│   └── eduhub_mongodb_project.ipynb     # Main Jupyter notebook
├── src/
│   └── eduhub_queries.py                # Python backup file
├── data/
│   ├── sample_data.json                 # Exported sample data
│   └── database_schema.json             # Schema documentation
├── docs/
│   ├── performance_analysis.md          # Performance documentation
│   └── presentation.pptx                # Project presentation
└── README.md                            # This file
```

---

##  Prerequisites
- MongoDB **v8.0+**
- MongoDB Compass (GUI)
- Python **3.8+**
- Jupyter Notebook
- Required Python Libraries:
  - `pymongo`
  - `pandas`
  - `python-dotenv`

---

##  Installation and Setup

### 1️⃣ MongoDB Setup
```bash
# Install MongoDB Community Edition
# Download from: https://www.mongodb.com/try/download/community

# Start MongoDB service
mongod --dbpath /path/to/your/database
```

### 2️⃣ Python Environment Setup
```bash
# Install required packages
pip install pymongo pandas jupyter python-dotenv

# Launch Jupyter Notebook
jupyter notebook
```

### 3️⃣ Project Execution
- Open `notebooks/eduhub_mongodb_project.ipynb` in Jupyter.  
- Execute cells sequentially from top to bottom.  
- All code includes clear documentation and can be executed directly.

---

##  Database Schema

### Collections
| Collection | Description |
|-------------|-------------|
| `users` | Students and instructors with profiles |
| `courses` | Course information and metadata |
| `enrollments` | Student course enrollments and progress |
| `lessons` | Individual lessons within courses |
| `assignments` | Course assignments and homework |
| `submissions` | Student assignment submissions and grades |

### Key Relationships
- Courses → Instructors (`courses.instructorId → users.userId`)
- Enrollments → Students & Courses (`enrollments.studentId`, `enrollments.courseId`)
- Lessons & Assignments → Courses
- Submissions → Students & Assignments

---

##  Features Implemented

### Phase 1: Database Setup & Modeling
- Created database and collections  
- Designed document schemas  
- Implemented data validation rules  

### Phase 2: Data Population
- Inserted **147+ documents** across 6 collections  
- Created realistic relationships between users, courses, and enrollments  

### Phase 3: CRUD Operations
- Implemented **Create, Read, Update, Delete** operations  
- Developed complex queries using various operators  

### Phase 4: Advanced Queries & Aggregation
- Built **6 aggregation pipelines** for analytics:  
  - Enrollment stats  
  - Student performance  
  - Instructor analytics  

### Phase 5: Indexing & Performance
- Created **11 indexes** to optimize performance  
- Added **full-text search** for course discovery  
- Achieved average query improvement of **+6.26%** (max **13.1%**)  

### Phase 6: Data Validation & Error Handling
- Implemented **MongoDB $jsonSchema** validation  
- Created error-handling wrappers for key operations  
- Verified referential and data integrity  

---

##  Sample Queries and Analytics

###  Basic Course Search
```python
# Find Python courses
courses = db.courses.find({
    "title": {"$regex": "Python", "$options": "i"}
})
```

###  Student Performance Analysis
```python
pipeline = [
    {"$match": {"status": "graded"}},
    {"$group": {
        "_id": "$studentId",
        "averageGrade": {"$avg": "$grade"}
    }}
]
```

###  Enrollment Statistics
```python
pipeline = [
    {"$group": {
        "_id": "$courseId",
        "totalEnrollments": {"$sum": 1}
    }},
    {"$sort": {"totalEnrollments": -1}}
]
```

---

##  Performance Metrics

| Metric | Value |
|---------|-------|
| Total Documents | **147+** |
| Collections | **6** |
| Indexes | **11** |
| Avg Query Improvement | **+6.26%** |
| Max Improvement | **+13.10%** |

---

##  Troubleshooting

### Common Issues
| Problem | Solution |
|----------|-----------|
|  Connection Refused | Ensure MongoDB service is running |
|  Import Errors | Verify all Python packages are installed |
|  Validation Errors | Check data types and required fields |
|  Duplicate Key Errors | Use unique identifiers for documents |

### Performance Tips
- Use **projection** to limit fields  
- Create **indexes** for frequent query patterns  
- Use **aggregation pipelines** for complex analytics  
- Monitor performance using `explain()`  

---

##  Project Deliverables

### Primary Files
-  **Jupyter Notebook** – `notebooks/eduhub_mongodb_project.ipynb`
-  **Python Script** – `src/eduhub_queries.py`
-  **Sample Data** – `data/sample_data.json`
-  **Documentation** – `README.md`, `performance_analysis.md`

### Additional Files
- Database schema documentation  
- Performance analysis report  
- Validation rules  
- Exported sample datasets  

---

##  Author
**Student Project – MongoDB Database Engineering**

Email: adewalelight44@gmail.com  
LinkedIn: [Adewale Light](www.linkedin.com/in/lightadewale)

---

##  License
This project is licensed under the **MIT License**.  
Feel free to use and modify it for educational or professional purposes.

---

##  Conclusion
This project demonstrates a **complete MongoDB backend** for an e-learning platform — covering **database design**, **query optimization**, **performance tuning**, and **data integrity management**.  
The EduHub database is **production-ready, scalable**, and adheres to **industry best practices**.
