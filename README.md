# HackerRank_SQL

Credit: Questions are from ["HackerRank"](https://www.hackerrank.com/)

#### Question 1:

Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively. Full description link: ["HackerRank: Occupations"](https://www.hackerrank.com/contests/simply-sql/challenges/occupations). 

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

#### Output:

<img width="1006" alt="Screenshot 2021-09-22 at 11 18 43 AM" src="https://user-images.githubusercontent.com/47832124/134289864-39dc7402-873a-446d-8a1b-392a82200089.png">

<hr style="border:2px solid gray"> </hr> 
