# HackerRank_SQL

Credit: Questions are from ["HackerRank"](https://www.hackerrank.com/)

#### Question 1:

Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively. <br/>
Full description link: ["HackerRank: Occupations"](https://www.hackerrank.com/contests/simply-sql/challenges/occupations). 

#### Answer 1:

with <br/>
cte1 as <br/>
(select D, row_number() over() as row_num from<br/>
(select <br/>
case when occupation like 'Doctor' then name end as D <br/>
from occupations group by D order by D) as F where D is not null),<br/>
cte2 as<br/>
(select P, row_number() over() as row_num from<br/>
(select <br/>
case when occupation like 'Professor' then name end as P<br/>
from occupations group by P order by P) as B where P is not null),<br/>
cte3 as<br/>
(select S, row_number() over() as row_num from<br/>
(select <br/>
case when occupation like 'Singer' then name end as S<br/>
from occupations group by S order by S ASC) as C where S is not null),<br/>
cte4 as<br/>
(select A, row_number() over() as row_num from<br/>
(select <br/>
case when occupation like 'Actor' then name end as A<br/>
from occupations group by A order by A ASC) as E where A is not null)<br/>
select D, P,S, A from cte1<br/>
right join cte2 on cte1.row_num = cte2.row_num<br/>
left join cte3 on cte3.row_num = cte2.row_num<br/>
left join cte4 on cte4.row_num = cte2.row_num<br/>

#### Output 1:

<img width="1006" alt="Screenshot 2021-09-22 at 11 18 43 AM" src="https://user-images.githubusercontent.com/47832124/134289864-39dc7402-873a-446d-8a1b-392a82200089.png">

<hr style="border:2px solid gray"> </hr> 

#### Question 2:

Generate the following two result sets:

1. Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).<br/>
2. Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:
There are a total of [occupation_count] [occupation]s. <br/>
Full description link: ["HackerRank: The PADS"](https://www.hackerrank.com/contests/simply-sql/challenges/the-pads). 

#### Answer 2:

with <br/>
cte1 as <br/>
(select concat('There are a total of ',count(O.name),' ', lower(O.occupation),'s.') as output <br/>
from occupations O group by O.occupation order by count(O.name), O.occupation),<br/>
cte2 as <br/>
(select concat(C.name,'(',substring(C.occupation,1,1 ),')') as output <br/>
 from occupations C)<br/>
select output from cte1 union select output from cte2 order by output<br/>

#### Output 2:

<img width="1007" alt="Screenshot 2021-09-22 at 11 28 41 AM" src="https://user-images.githubusercontent.com/47832124/134290727-e91d29e0-d4b2-41a6-ac63-4f1b052bd629.png">

<hr style="border:2px solid gray"> </hr> 

<!---
#### Question 3:

Query the Name of any student in STUDENTS who scored higher than  Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID. <br/>
Full description link: ["HackerRank: Higher Than 75 Marks"](https://www.hackerrank.com/contests/simply-sql/challenges/more-than-75-marks). 

#### Answer 3:

with <br/>
cte1 as <br/>
(select concat('There are a total of ',count(O.name),' ', lower(O.occupation),'s.') as output <br/>
from occupations O group by O.occupation order by count(O.name), O.occupation),<br/>
cte2 as <br/>
(select concat(C.name,'(',substring(C.occupation,1,1 ),')') as output <br/>
 from occupations C)<br/>
select output from cte1 union select output from cte2 order by output<br/>

#### Output 3:

<img width="1007" alt="Screenshot 2021-09-22 at 11 28 41 AM" src="https://user-images.githubusercontent.com/47832124/134290727-e91d29e0-d4b2-41a6-ac63-4f1b052bd629.png">

<hr style="border:2px solid gray"> </hr> 

#### Question 2:

Generate the following two result sets:

1. Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).<br/>
2. Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:
There are a total of [occupation_count] [occupation]s. <br/>
Full description link: ["HackerRank: The PADS"](https://www.hackerrank.com/contests/simply-sql/challenges/the-pads). 

#### Answer 2:

with <br/>
cte1 as <br/>
(select concat('There are a total of ',count(O.name),' ', lower(O.occupation),'s.') as output <br/>
from occupations O group by O.occupation order by count(O.name), O.occupation),<br/>
cte2 as <br/>
(select concat(C.name,'(',substring(C.occupation,1,1 ),')') as output <br/>
 from occupations C)<br/>
select output from cte1 union select output from cte2 order by output<br/>

#### Output 2:

<img width="1007" alt="Screenshot 2021-09-22 at 11 28 41 AM" src="https://user-images.githubusercontent.com/47832124/134290727-e91d29e0-d4b2-41a6-ac63-4f1b052bd629.png">

<hr style="border:2px solid gray"> </hr> 

#### Question 2:

Generate the following two result sets:

1. Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).<br/>
2. Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:
There are a total of [occupation_count] [occupation]s. <br/>
Full description link: ["HackerRank: The PADS"](https://www.hackerrank.com/contests/simply-sql/challenges/the-pads). 

#### Answer 2:

with <br/>
cte1 as <br/>
(select concat('There are a total of ',count(O.name),' ', lower(O.occupation),'s.') as output <br/>
from occupations O group by O.occupation order by count(O.name), O.occupation),<br/>
cte2 as <br/>
(select concat(C.name,'(',substring(C.occupation,1,1 ),')') as output <br/>
 from occupations C)<br/>
select output from cte1 union select output from cte2 order by output<br/>

#### Output 2:

<img width="1007" alt="Screenshot 2021-09-22 at 11 28 41 AM" src="https://user-images.githubusercontent.com/47832124/134290727-e91d29e0-d4b2-41a6-ac63-4f1b052bd629.png">

<hr style="border:2px solid gray"> </hr> 

#### Question 2:

Generate the following two result sets:

1. Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).<br/>
2. Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:
There are a total of [occupation_count] [occupation]s. <br/>
Full description link: ["HackerRank: The PADS"](https://www.hackerrank.com/contests/simply-sql/challenges/the-pads). 

#### Answer 2:

with <br/>
cte1 as <br/>
(select concat('There are a total of ',count(O.name),' ', lower(O.occupation),'s.') as output <br/>
from occupations O group by O.occupation order by count(O.name), O.occupation),<br/>
cte2 as <br/>
(select concat(C.name,'(',substring(C.occupation,1,1 ),')') as output <br/>
 from occupations C)<br/>
select output from cte1 union select output from cte2 order by output<br/>

#### Output 2:

<img width="1007" alt="Screenshot 2021-09-22 at 11 28 41 AM" src="https://user-images.githubusercontent.com/47832124/134290727-e91d29e0-d4b2-41a6-ac63-4f1b052bd629.png">

<hr style="border:2px solid gray"> </hr> 
--->
