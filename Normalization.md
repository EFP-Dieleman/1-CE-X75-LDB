# Normalization

Normalization, proposed by Edgar F. Codd, involves structuring a relational database to reduce data redundancy and dependency by organizing tables and relationships. 
The process unfolds through a series of normalization forms, each addressing specific issues.

## First Normal Form (1NF)

A table is considered to be in 1NF if it doesn't contain **repeating groups of data** and each column contains **atomic values** (indivisible and single-valued). 

**Example:**

Consider a table representing student lessons:

| student_id | subjects                 |
|------------|--------------------------|
| 1          | Math, Physics, Chemistry |
| 2          | English, Biology         |

This table is not in 1NF because the "Subjects" column contains a list of values. To bring it into 1NF, we can break down the subjects into separate rows:

| student_id | subject    |
|------------|------------|
| 1          | Math       |
| 1          | Physics    |
| 1          | Chemistry  |
| 2          | English    |
| 2          | Biology    |

Now, each cell in the "Subject" column contains a single value, and the table conforms to 1NF. 
This makes it easier to manage, query, and maintain the data.

In summary, 1NF ensures that a table has a flat structure with no nested arrays or repeating groups, and each column holds atomic values.


## Second Normal Form (2NF)
   - Meet the requirements of 1NF.
   - Remove partial dependencies by ensuring that non-prime attributes are fully functionally dependent on the primary key.


Before second normal form

| Order_ID | Product    | Category     |
|----------|------------|--------------|
| 1        | Laptop     | Electronics  |
| 2        | Coffee Mug | Kitchen      |


After

| Order_ID | Product    | 
|----------|------------|
| 1        | Laptop     |
| 2        | Coffee Mug |


| Product    | Category     |
|------------|--------------|
| Laptop     | Electronics  |
| Coffee Mug | Kitchen      |


## Third Normal Form (3NF)
   - Meet the requirements of 2NF.
   - Eliminate transitive dependencies by removing columns that are dependent on other **non-prime attributes**.

**Example of Third Normal Form (3NF):**

Consider a database for a library system where information about books, authors, and publishers is stored. Initially, the data is in a denormalized state.

**Before 3NF:**

**Books Table:**

| ISBN         | Title                   | Author          | Author_Country | Publisher           | Publisher_Country |
|--------------|-------------------------|------------------|-----------------|---------------------|-------------------|
| 978-0061120084 | To Kill a Mockingbird  | Harper Lee       | USA             | HarperCollins       | USA               |
| 978-0141182605 | 1984                    | George Orwell    | UK              | Penguin Books       | UK                |
| 978-0544003415 | The Hobbit              | J.R.R. Tolkien   | UK              | Houghton Mifflin    | USA               |

Here, 'Author_Country' and 'Publisher_Country' are transitively dependent on 'Author' and 'Publisher,' respectively.

**After 3NF:**

Create separate tables for authors and publishers:

**Authors Table:**

| Author          | Author_Country |
|------------------|-----------------|
| Harper Lee       | USA             |
| George Orwell    | UK              |
| J.R.R. Tolkien   | UK              |

**Publishers Table:**

| Publisher           | Publisher_Country |
|---------------------|-------------------|
| HarperCollins       | USA               |
| Penguin Books       | UK                |
| Houghton Mifflin    | USA               |

**Books Table (Updated):**

| ISBN         | Title                   | Author          | Publisher           |
|--------------|-------------------------|------------------|---------------------|
| 978-0061120084 | To Kill a Mockingbird  | Harper Lee       | HarperCollins       |
| 978-0141182605 | 1984                    | George Orwell    | Penguin Books       |
| 978-0544003415 | The Hobbit              | J.R.R. Tolkien   | Houghton Mifflin    |

Now, 'Author_Country' and 'Publisher_Country' are directly dependent on their respective primary keys in the 'Authors' and 'Publishers' tables, adhering to 3NF.

This normalization ensures that data is organized efficiently, avoids redundancy, and simplifies updates without introducing unnecessary dependencies. The resulting structure supports data integrity and provides a foundation for scalable and maintainable database management.


## Other Normal Forms

**Boyce-Codd Normal Form (BCNF):**
   - A more stringent version of 3NF.
   - Every determinant must be a superkey.

**Fourth Normal Form (4NF):**
   - Deals with multi-valued dependencies.
   - Ensures that a multi-valued dependency is represented by a separate table.

**Fifth Normal Form (5NF):**
   - Addresses cases where information can be derived from the values in a table in more than one way.
   - Introduces the concept of join dependencies.

**Domain-Key Normal Form (DK/NF):**
   - A refinement of BCNF.
   - Ensures that all constraints are expressed in terms of the domain and the key.
