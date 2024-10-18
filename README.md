# MIST4610-Project1

## Team Name
4610Fa24Group9

## Team Members:
1. Dylan Van Saun https://github.com/dylanvansaun
2. Zoey Cao https://github.com/zoeync
3. Jennifer Tran https://github.com/j-tran1
4. Margaret Cox https://github.com/mac14681
5. Jayden Smith https://github.com/jaydenSmith4321

## Scenario Description:
Our task is to model and build a relational database for the general workings of a university library system. The central entity in the model is the Library entity of the university library system, with contains each library that the university has. Each library operates in conjunction with a book supplier, and students can check out various copies of books (written by different authors) from the libraries while employees facilitate the transactions. The libraries also have partnerships with various volunteer organizations, and students can volunteer at the libraries with these organizations. Our goal is to accurately model these relationships, create sample data, and populate the entities and attributes with this sample data. We also aim to create functioning queries from this data to gain meaningful business and managerial insights into the university library system’s operations. 

## Data Model:
Explanation of the data model:

Our data model represents a university library system. The Library entity contains details about each library, including its name, address, phone number, and campus location. Each library supplies many books, and this is represented by a one-to-many relationship between the Library and CopyOfBook tables. The CopyOfBook entity tracks individual copies of books stored in each library. A book may have multiple copies, but it is tied to a single book in the Book table, which holds information like title, genre, cover material, and publish date. The Author table is linked to the Book table through a one-to-many relationship, showing that a book can have a single author, but each author can write multiple books. While this may not be true in nature, we did not want to overcomplicate the model.

The Student entity stores student information, such as their address, email, and graduation date. Students check out books, represented by a one-to-many relationship between BookCheckOut and Student. The BookCheckOut table tracks the details of books borrowed by students, including check-out dates, due dates, and return dates. Each BookCheckOut also ties back to a specific book in the CopyOfBook entity. Additionally, BookCheckOut tracks the employee that was in charge of that specific check out occurance. The Employee entity holds details about library staff, and there's a one-to-many relationship between Library and Employee, reflecting that each library has multiple employees but an employee may only work at one library. There is also a one-to-many recursive relationship within the Employee table that represents the manager of each library.

The BookBuyingTransaction and BookSupplier entities represent the procurement process of the books. BookBuyingTransaction tracks each invoice and details about quantities, order costs, and purchase dates. These supplies come from a supplier, which is represented by the BookSupplier table. BookSupplier stores information about suppliers, including their names and contact information.

Lastly, the Partnership entity represents the collaborations between Library and VolunteerOrganization, with a many-to-many relationship showing that each library may have multiple partnerships with volunteer organizations. These volunteer organizations track information such as contact details and organization type. The VolunteerWork table shows which students are associated with specific VolunteerOrganizations, allowing the system to track the contributions made by students in the library's volunteering activities.

![Group 9 Final Data Model](https://github.com/user-attachments/assets/7bbb821d-43d2-49c6-9391-cc9d49cb4ae4)

## Data Dictionary:
![image](https://github.com/user-attachments/assets/6d8e683b-6e52-4902-bcb3-4c3c10f94dc5)
![image](https://github.com/user-attachments/assets/51f092be-b562-40f9-94c2-146b67a69b9e)
![image](https://github.com/user-attachments/assets/861fd992-906f-45eb-a1b6-c4870eb93078)
![image](https://github.com/user-attachments/assets/465233e5-60b1-41ac-b917-7985ed4df42a)
![image](https://github.com/user-attachments/assets/042d04e5-981a-40db-a780-10db37594585)
![image](https://github.com/user-attachments/assets/cf65ba86-b340-4592-ab0a-12e8bb2a043c)
![image](https://github.com/user-attachments/assets/d3afe7a0-cc49-49e2-a556-3efe021bc8aa)
![image](https://github.com/user-attachments/assets/0d6b2cb5-a86e-4864-bcd2-fd36320ab3de)
![image](https://github.com/user-attachments/assets/88644432-75cd-40df-9fbd-1b69deb4a82f)
![image](https://github.com/user-attachments/assets/73a72317-9c66-40c3-899e-94fadece3900)
![image](https://github.com/user-attachments/assets/e5310cbb-733a-49e0-aaf9-fb1d3b33aac2)
![image](https://github.com/user-attachments/assets/1042eeaa-7ee9-487d-8ee0-f4e53a9070ee)

## Queries:
![image](https://github.com/user-attachments/assets/68968c75-fea4-461b-b730-3e3a3cd538e6)
1. Query 1 shows the specific books that have not been checked out with the book title, genre, copy ID and library ID.
![image](https://github.com/user-attachments/assets/90612889-e598-4e5e-a343-e08c1dd79d99)
In query 1, we can see which book titles have never been checked out, as well as the specific copy, genre, and library the book belongs to. From a managerial perspective, this query allows managers to identify the books or genres that might not be popular with students, which would help them determine what types of books could be replaced with more popular ones. In addition, knowing the copy and library also makes it easier to tailor decisions based on the library’s demand. For example, if certain genres aren’t performing well at a particular location, managers can adjust that location’s inventory accordingly. Overall, this query helps managers ensure that the library’s shelf space is being used effectively and students have access to books they’re more likely to check out.

2. Query 2 lists the volunteer organizations that have less than 75 total volunteer hours.
![image](https://github.com/user-attachments/assets/00a22376-bcbc-41a7-a1e1-2915ba339c03)
In query 2, we can see which organizations do not meet the library’s >75 hours criteria for ‘high engagement’, meaning not many students are part of the organization or they are not putting a lot of hours into them. From a managerial perspective, this information allows managers to either recruit more volunteers or encourage current organizations to be more involved. Without enough volunteer hours, some libraries might not be able to meet the university’s needs, so it's important to know which organizations aren’t contributing as much to ensure everything runs smoothly.

3. Query 3 lists the number of books checked out overall from each library and includes a percentage of books checked out compared to the total copies of books from that library.
![image](https://github.com/user-attachments/assets/9c9c7a37-c661-4da3-823b-9d09edc82f1c)
In query 3, we can see which libraries have the most traffic, using the library name, library ID, and the number and percentage of books that are checked out in that library. From a managerial perspective, we can see which libraries have the least traffic and decide if we should promote them. In addition, we can decide if libraries with higher traffic may benefit from getting more inventory to meet demand based on the percentage of how many copies are checked out in that library. For instance, if 100% of the copies are checked out in a specific library, it may be reasonable to get more inventory. We can also see trends based on campus location with which the libraries are located. If a library in a crowded part of campus is getting a lower amount of books checked out, it may indicate an issue. If a library in a less crowded area of campus has higher than usual traffic, it may indicate that we should look into allocating more resources there to support it.

4. Query 4 lists the percentage of total cost spent on orders of books for each library.
![image](https://github.com/user-attachments/assets/be7be48f-8d6e-4009-aa6f-6588558930d5)
From query 4, we can see which libraries, with their respective IDs, have spent how much in total and what their percentage is of the total overall book spending across all libraries. From a managerial perspective, we will see which libraries are in line with the budget, which ones are overspending and which ones are underspending. Each library, based on traffic and size, will have an allocated percentage of the budget for buying books, so we will use this data to compare against that percentage. If we see which libraries are overspending, we can mediate that issue. This query also helps us know if we are budgeting correctly. For instance, if a library is constantly overspending, it may be an indicator that they need a bigger portion of the budget.

5. Query 5 lists out the number of checkout transactions each employee has done.
![image](https://github.com/user-attachments/assets/6c93f673-1025-4d86-a803-553ec5122d79)
Query 5 shows the employee’s name, their respective library IDs, and the number of checkouts they have done in total. From a managerial perspective, it allows a manager to see which employees are below a certain threshold in regards to checking out books. If an employee is below that threshold, it could mean that they’re not working efficiently or enough. This data allows managers to hold performance reviews, discuss reasons behind underperformance and find ways to improve. In addition, tracking the number of checkout transactions each employee completes can help managers spot workloads that are not balanced. For example, if some employees are consistently handling a higher amount of checkouts, they may feel burnt out, so managers can potentially distribute workloads more evenly. This will help improve individual performance and lead to a more balanced, efficient team.

6. Query 6 lists the name of the manager, their library, and the number of employees they are in charge of.
![image](https://github.com/user-attachments/assets/acdde021-75e0-4a32-8ae0-8fa8bf37a018)
Query 6 is helpful because it allows managers to see the name of each manager, their library, and the number of employees they supervise, which can show whether certain libraries are understaffed or overstaffed. From a managerial perspective, this information helps supervisors keep track of who they are in charge of and who is working for them. As bosses, they can be more focused on the needs of their direct subordinates. In addition, supervisors can also make better decisions about reallocating resources to make sure that every supervisor has enough staff support. For instance, the Main Library only has a supervisor and one subordinate, so that might be a sign that more staff is needed by either bringing in employees from other libraries or by hiring someone externally.

7. Query 7 lists out the students that have not returned their books on time and the corresponding book titles, library names, and book copy IDs.
![image](https://github.com/user-attachments/assets/aca8a0b3-7757-469f-83e9-1a4f38a9056c)
Query 7 allows managers to track book titles that were returned late, and give information about the student, specific book copy, and the library. From a managerial perspective, this data is valuable because it enables managers to directly address recurring issues with specific students. For example, managers can suspend borrowing privileges for students who have returned books late multiple times, like Ellie Van Saun, who has missed three due dates. By identifying these patterns, managers can hold students accountable and help keep the library's book return system running smoothly.

8. Query 8 lists which libraries that are partnered with which volunteer organizations.
![image](https://github.com/user-attachments/assets/b3e63825-23a1-488a-8657-8527af98fb0f)
Query 8 makes a list of the libraries who are currently in partnerships with volunteer organizations and which organiations they are partnered with. From a managerial perspective, knowing which libraries are partnered with which volunteer organizations means that managers can determine whether these partnerships align with the library’s needs. It also allows managers to identify opportunities for expanding partnerships, especially since each library currently only partners with one volunteer organization but could partner with more. This would help managers broaden the library’s outreach, increase volunteer support, and strengthen the library's role in supporting the university.

9. Query 9 lists out suppliers’ names and IDs, the amount of books and the overall costs of their orders that they have sold to all libraries. The results are ordered by the highest-selling supplier, followed by the highest number of books sold.
![image](https://github.com/user-attachments/assets/7d7e0b78-4c35-4965-b601-0e98020ac21b)
Query 9 shows the supplier’s names, their IDs, the total amount of books they sold to the libraries in our system and the cumulative cost of all orders from all libraries. From a managerial perspective, knowing which suppliers are the campus libraries’ top suppliers is useful. We can see which suppliers the libraries are doing more business with depending on who the libraries are buying the most books from and how much the overall cost of those orders are. We can also use this data to determine which suppliers we can become loyal customers to and potentially solidify a stronger business partnership with them, which can lead to possible loyalty discounts with a consistent, steady supply of books whenever the university’s libraries need it. In addition, we can use this data to see which suppliers we aren’t ordering from as much. There could be possible reasons as to why we are doing business with one supplier over the other, and after careful evaluation on why, we can make the decision to try to solidify a stronger partnership or decide not to do business with them anymore.

10. Query 10 lists all employees in the library system who have ‘Assistant’ in their job title with the library name and library ID.
![image](https://github.com/user-attachments/assets/17aa4e9a-704b-4108-ac72-c8c16ebbaaa7)
Query 10 provides a clear overview of the distribution of assistants across all of the libraries by listing the employee’s name, their job position and the library name and ID of where they work. From a managerial perspective, It is important to see how many assistants are working at each library because it allows managers to evaluate whether resources are being allocated effectively. If some libraries have many assistants while others have only a few, it might indicate that there’s an uneven level of support for certain libraries. With this data, managers can make more informed decisions on staffing to ensure that all libraries have enough support to meet their needs efficiently.

## Group Presentation:
[Group Project 1_ Library System.pptx](https://github.com/user-attachments/files/17437640/Group.Project.1_.Library.System.pptx)

## Database Information:
Name of the database: ns_4610Fa24Group9

Additional Information: Each query listed above is logged in the databse using stored procedures which can be called upon by using: CALL TP_QX();
