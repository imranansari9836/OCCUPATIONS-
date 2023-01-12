with A as
(
   select 
    case when occupation='Doctor' then name end as Doctor,
    case when occupation='Professor' then name end as Professor,
    case when occupation='Singer' then name end as Singer,
    case when occupation='Actor' then name end as Actor,
    row_number() over(partition by OCCUPATION order by name) as B
    from OCCUPATIONS)
    select min(Doctor),min(Professor),min(Singer),min(Actor)from A group by B;
 
