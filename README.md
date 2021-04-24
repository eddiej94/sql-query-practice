# sql-query-practice


### Round 1

Connect to the LikeyPix database in Beekeeper, and answer the following questions:

1. Write a query that returns all Users

```
select * from users;
```

2. Write a query that returns all Posts

```
select * from posts;

```

3. Write a query that returns the count of all Posts

```
select count (*)
from posts

```

4. Which Post had the most Comments?

Answer: post id (1) has the most comments "3" to be exact.

5. Write a query that returns the Post which had the least Comments

```
select count(*) as num, post_id from comments
group by post_id
order by num asc
limit 1
;

```

6. Which User has the most Comments?

Answer: user id 1 has the most comments

7. Write a single query to get all of the Posts and their Comments (You'll see the same Post repeated in the results)

```
select * from posts 
  join comments 
  on posts.id = comments.post_id

```

### Round 2

- Disconnect from the `likeypix` database connection
- Connect to the `classroom` database connection

1. Write a query to get the first name, last name, and github URL for every Student in the `students` table

```
select first_name, last_name, github_url from students


```

2. Write a query to get a list of Students who do not have a LinkedIn URL

```
select * from students
	where linkedin_url = ''

```

3. Write a query to get a list of Teachers with the "Teaching Assistant" Role

```
select * from teachers
	where teacher_role_id = 2

```

4. Write a query to get a list of Students, and their Class' `slug`

```
select classes.slug, students.first_name, students.last_name
from classes join students
on classes.id = students.class_id

```

5. Write a query to get the length of every students First Name

```
select length(first_name) from students	


```

6. What is the ID of the Student with the longest Last Name?

Answer: 
```
select length(last_name), id 
from students	
order by length(last_name) desc;
```

7. Write a query to get a list of Students in reverse alphabetical order of First Name

```
select * from students
  ORDER BY first_name desc;

```

### Round 3

- Disconnect from the `classroom` database connection
- Connect to the `food` database connection

This Round is going to require you to get curious about your surroundings. At some point in your path as a developer, you will work on a project that already has an existing database. That database may be quite old, or have been built on a different set of standards.

These questions will be focused on exploring an unknown database that does not follow the standards we have established in class. See if you can work out answers to the following questions:


1. What table contains information about individual food items? 

Answer: food_des

2. Using the table from the previous answer as your starting point - what table do you think contains Food Group information about individual foods?

Answer: fd_group

3. Write a query to get the name of a food, and its corresponding food group name 

```
select food_des.comname, food_des.long_desc, fd_group.fddrp_desc  
    from food_des join fd_group
    on food_des.fdgrp_cd = fd_group.fdgrp_cd;

```

4. Identify the table that has information about data sources

Answer: data_src

5. Using the table from your previous answer, write a query that will get the oldest data source

```
select food_des.comname, food_des.long_desc, fd_group.fddrp_desc  from food_des
	join fd_group
    on food_des.fdgrp_cd = fd_group.fdgrp_cd;

```

6. How many foods contain "Egg" in their description?

Answer: select count(*) from food_des
where long_desc 
ilike '%egg%'; 

101 

7. Write a query that will return a count of foods in each food group

```
select fd_group.fddrp_desc,
	count (fd_group.fddrp_desc) num 
    from food_des
    join fd_group
    on food_des.fdgrp_cd = fd_group.fdgrp_cd
    group by fd_group,fddrp_desc;

```
