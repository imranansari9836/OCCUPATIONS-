    with a as (
select 
    case when occupation='doctor' then name end as doctor ,
    case when occupation='professor' then name end as professor ,
    case when occupation='singer' then name end as singer, 
    case when occupation='actor' then name end as actor, 
    row_number() over (partition by occupation order by name) as ran 
from occupations)
select min(doctor), min(professor), min(singer), min(actor) from a group by ran
