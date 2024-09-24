1. Write a query to find the average grade of all students across all courses.
 SELECT AVG(grade) AS avg_grade
FROM Enrollments;
![Screenshot 2024-09-24 220559](https://github.com/user-attachments/assets/67ed020d-56c3-4b38-8e39-510fb3175a9b)

2. Write a query to list the names of students along with the courses they are enrolled in. Include the course name in your result.
SELECT s.name, c.course_name
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
JOIN Courses c ON e.course_id = c.course_id;
![Screenshot 2024-09-24 222856](https://github.com/user-attachments/assets/32dd5d74-854d-48cb-8cd4-3bf89628e9cf)

3. Write a query to count the number of students in each grade level.
SELECT grade_level, COUNT(*) AS student_count
FROM Students
GROUP BY grade_level;
![Screenshot 2024-09-24 221340](https://github.com/user-attachments/assets/038900be-852f-42e9-9a37-e420fef8bc86)

4. Write a query to find the maximum grade achieved in each course.
SELECT c.course_name, MAX(e.grade) AS max_grade
FROM Enrollments e
JOIN Courses c ON e.course_id = c.course_id
GROUP BY c.course_name;
![Screenshot 2024-09-24 221442](https://github.com/user-attachments/assets/edc0663c-155a-4f7a-8380-ef5e2a642631)

5. Write a query to find the average grade of students who are in grade level 3.
SELECT AVG(e.grade) AS avg_grade
FROM Enrollments e
JOIN Students s ON e.student_id = s.student_id
WHERE s.grade_level = 3;
![Screenshot 2024-09-24 221606](https://github.com/user-attachments/assets/76a7e701-0bb6-4842-87e2-3652fa28a080)

6. Write a query to get a list of students, their enrolled courses, and the credit hours for each course.
SELECT s.name, c.course_name, c.credits
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
JOIN Courses c ON e.course_id = c.course_id;
![Screenshot 2024-09-24 223631](https://github.com/user-attachments/assets/9b312798-07a0-44b5-b5b4-e690258c8918)

7. Write a query to find all courses that have an average grade greater than 3.0.
SELECT c.course_name, AVG(e.grade) AS avg_grade
FROM Enrollments e
JOIN Courses c ON e.course_id = c.course_id
GROUP BY c.course_name
HAVING AVG(e.grade) > 3.0;
![Screenshot 2024-09-24 221806](https://github.com/user-attachments/assets/24cd5c6b-ce64-44a9-bd68-aeb3ac632863)

8. Write a query to find students who have not received a grade of 4.0 in any course.
SELECT DISTINCT s.name
FROM Students s
WHERE NOT EXISTS (
    SELECT 1
    FROM Enrollments e
    WHERE e.student_id = s.student_id
    AND e.grade = 4.0

);
![Screenshot 2024-09-24 221857](https://github.com/user-attachments/assets/0e0ab676-875f-4abf-bff2-47d7c561dd6a)

9. Write a query to find the names of students whose average grade is greater than the average grade of all students.
 SELECT s.name
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
GROUP BY s.name
HAVING AVG(e.grade) > (SELECT AVG(grade) FROM Enrollments);
![Screenshot 2024-09-24 221950](https://github.com/user-attachments/assets/ea70a511-a7b7-497b-b735-9eaa569fbd5c)

10. Write a query to display each student's name, the total number of courses they are enrolled in, and their average grade.
 SELECT s.name, COUNT(e.course_id) AS total_courses, AVG(e.grade) AS avg_grade
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
GROUP BY s.name;
![Screenshot 2024-09-24 222106](https://github.com/user-attachments/assets/e9babd50-7e8c-426d-8232-b2472cddab87)


