A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. 
The analytics team is particularly interested in understanding what songs users are listening to

The Sparkify schema has 5 tables (Star Schema), one is Fact the others are dimension tables.  
Fact Table;
songplays --> contains when, who listen which song of an artist 

Dimension Tables;
users --> users in the app
songs --> songs in music database
artists --> artists in music database
time --> broken down into specific time units

**Some Dashboard Queries;**
1. Monthly Most Popular Artist
    select a.name artist_name, t.year, t.month, count(*) 
      from ((songplays s 
      join artists a on a.artist_id = s.artist_id)  
      join time t s.start_time = t.start_time)
    group by a.name artist_name, t.year, t.month  
    order by 5 desc
   
2. User Weekly Trend
    select u.first_name, u.last_name, t.year, t.week, count(*) 
      from ((songplays s 
      join users u on u.user_id = s.user_id)  
      join time t s.start_time = t.start_time)
    group by u.first_name, u.last_name, t.year, t.week
    order by 5 desc  

data_check.jpynb is doing a few control on data. 