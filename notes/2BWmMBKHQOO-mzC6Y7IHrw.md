1.1
```sql=
SELECT * 
FROM course as c
WHERE c.dept_name = "Comp. Sci." AND c.credits >= 3;
```
1.2
```sql=
SELECT DISTINCT s.name, c.dept_name
FROM student s
JOIN takes t ON s.ID = t.ID
JOIN course c ON t.course_id = c.course_id
```
```sql=
SELECT DISTINCT student.name, department.dept_name
FROM student, takes, course, department
WHERE student.ID = takes.ID
AND takes.course_id = course.course_id
AND course.dept_name = department.dept_name;
```
1.3
```sql=
SELECT s.name, s.ID
FROM student as s, takes as t
WHERE s.ID = t.ID
AND t.course_id = 'CS-101'
AND t.semester = 'Fall'
AND t.year = 2009
AND t.grade = 'F'
```
```sql=
SELECT s.name, s.ID
FROM student s
JOIN takes t ON s.ID = t.ID
WHERE t.course_id = 'CS-101'
AND t.semester = 'Fall'
AND t.year = 2009
AND t.grade = 'F'
```
1.4
```sql=
SELECT s.name, s.ID
FROM student as s, takes as t
WHERE s.ID = t.ID
AND t.course_id = 'BIO-101'
AND t.grade IN ('A', 'A-', 'B')
```
```sql=
SELECT s.name, s.ID
FROM student s
JOIN takes t ON s.ID = t.ID
WHERE t.course_id = 'BIO-101'
AND t.grade IN ('A', 'A-', 'B')
```
1.5
```sql=
SELECT DISTINCT s.name, s.ID
FROM student as s
JOIN takes t ON s.ID = t.ID
JOIN course c ON t.course_id = c.course_id
WHERE t.grade = 'A'
AND c.title IN ('Robotics', 'Investment Banking', 'Game Design')
```
1.6
```sql=
SELECT SUM(instructor.salary)
FROM instructor
WHERE instructor.dept_name = 'Comp. Sci.'
```
1.7
```sql=
SELECT s.building, COUNT(s.course_id)
FROM section s
WHERE s.year = 2010 AND s.semester = 'Spring'
GROUP BY s.building
```
4.1
```sql=
SELECT m.Title
FROM Movie m
WHERE m.Year > 2010
```
4.2
```sql=
SELECT *
FROM Actor a
WHERE a.Fname like '%jen%'
```
4.3
```sql=
SELECT p.Fname, p.lname
FROM Person p
JOIN Favorite f ON p.ID = f.ID
WHERE f.Title = 'Ratatouille'
```
4.4
```sql=
SELECT p.Fname, p.lname
FROM Person p
JOIN Favorite f ON p.ID = f.ID
WHERE f.Title NOT IN ('Ratatouille', 'Inception', 'Good Will hunting',
'Forrest Gump')
```
4.5
```sql=
SELECT DISTINCT *
FROM Actor a
JOIN Actors_In ai ON a.Fname = ai.Fname, a.lname = ai.lname
WHERE ai.Title IN (SELECT DISTINCT s.Title
                  FROM Saw s
                  JOIN Person p ON s.ID = p.ID
                  WHERE s.numStars >= 4
                  AND p.Fname = 'Kevin')
```
4.6
```sql=
SELECT m.MPAA, COUNT((m.Title, m.Year))
FROM Movie m
JOIN Saw s ON m.Title = s.Title, m.Year = s.Year
JOIN Person p on s.ID = p.ID
WHERE p.Fname = 'Kevin'
GROUP BY m.MPAA
```