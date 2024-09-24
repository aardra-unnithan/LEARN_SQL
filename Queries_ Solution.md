1.
SELECT AVG(grade) AS avg_grade
FROM Enrollments;
![Screenshot 2024-09-24 220559](https://github.com/user-attachments/assets/67ed020d-56c3-4b38-8e39-510fb3175a9b)

2.
SELECT s.name, c.course_name
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
JOIN Courses c ON e.course_id = c.course_id;
![Screenshot 2024-09-24 222856](https://github.com/user-attachments/assets/32dd5d74-854d-48cb-8cd4-3bf89628e9cf)

3. 
SELECT grade_level, COUNT(*) AS student_count
FROM Students
GROUP BY grade_level;
![Screenshot 2024-09-24 221340](https://github.com/user-attachments/assets/038900be-852f-42e9-9a37-e420fef8bc86)

4.
SELECT c.course_name, MAX(e.grade) AS max_grade
FROM Enrollments e
JOIN Courses c ON e.course_id = c.course_id
GROUP BY c.course_name;
![Screenshot 2024-09-24 221442](https://github.com/user-attachments/assets/edc0663c-155a-4f7a-8380-ef5e2a642631)

5. 
SELECT AVG(e.grade) AS avg_grade
FROM Enrollments e
JOIN Students s ON e.student_id = s.student_id
WHERE s.grade_level = 3;
![Screenshot 2024-09-24 221606](https://github.com/user-attachments/assets/76a7e701-0bb6-4842-87e2-3652fa28a080)

6. 
SELECT s.name, c.course_name, c.credits
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
JOIN Courses c ON e.course_id = c.course_id;
![Screenshot 2024-09-24 223631](https://github.com/user-attachments/assets/9b312798-07a0-44b5-b5b4-e690258c8918)

7. 
SELECT c.course_name, AVG(e.grade) AS avg_grade
FROM Enrollments e
JOIN Courses c ON e.course_id = c.course_id
GROUP BY c.course_name
HAVING AVG(e.grade) > 3.0;
![Screenshot 2024-09-24 221806](https://github.com/user-attachments/assets/24cd5c6b-ce64-44a9-bd68-aeb3ac632863)

8. 
SELECT DISTINCT s.name
FROM Students s
WHERE NOT EXISTS (
    SELECT 1
    FROM Enrollments e
    WHERE e.student_id = s.student_id
    AND e.grade = 4.0

);
![Screenshot 2024-09-24 221857](https://github.com/user-attachments/assets/0e0ab676-875f-4abf-bff2-47d7c561dd6a)

9. 
 SELECT s.name
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
GROUP BY s.name
HAVING AVG(e.grade) > (SELECT AVG(grade) FROM Enrollments);
![Screenshot 2024-09-24 221950](https://github.com/user-attachments/assets/ea70a511-a7b7-497b-b735-9eaa569fbd5c)

10. 
 SELECT s.name, COUNT(e.course_id) AS total_courses, AVG(e.grade) AS avg_grade
FROM Students s
JOIN Enrollments e ON s.student_id = e.student_id
GROUP BY s.name;
![Screenshot 2024-09-24 222106](https://github.com/user-attachments/assets/e9babd50-7e8c-426d-8232-b2472cddab87)


