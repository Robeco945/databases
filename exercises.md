Roberto Caretto 
29.9.2024


# exercise 2
### question 1
 select * from goal !
![img.png](img.png)

### question 2
select name,type from airport where iso_country = "FI";
![img_1.png](img_1.png)

 ### question 3
select name from airport where iso_country = "FI" order by name;
![img_2.png](img_2.png)

### question 4
select name, type from airport where iso_country = "FI" order by type, name;
![img_3.png](img_3.png)

### question 5
select name from country where name like "F%";
![img_4.png](img_4.png)

### question 6
select name from country where name like "%F%";
![img_5.png](img_5.png)

### question 7
select location from game where screen_name = "Vesa";
![img_6.png](img_6.png)

### question 8 
select co2_consumed from game where screen_name = "Ilkka";
![img_7.png](img_7.png)

### question 9
select distinct co2_budget from game;
![img_8.png](img_8.png)

### question 10
select screen_name, co2_budget, co2_consumed, (co2_budget - co2_consumed) as co2_left from game where screen_name = 'Ilkka';
![img_9.png](img_9.png)

# exercise 3

### question 1
select country.name as 'country name', airport.name as 'airport name' from country, airport where country.iso_country = airport.iso_country and country.name = 'Iceland';
![img_10.png](img_10.png)

### question 2
select airport.name as "airport name" from airport where iso_country = "FR" and type = "large_airport";
![img_11.png](img_11.png)

### question 3
select country.name as "country_name", airport.name as "airport_name" from country, airport where country.iso_country = airport.iso_country and country.continent = "AN";
![img_12.png](img_12.png)

### question 4 
select elevation_ft from game, airport where location = ident and screen_name = "Heini";
![img_13.png](img_13.png)

### question 5
select (elevation_ft * 0.3048) as elevation_m from game, airport where location = ident and screen_name = "Heini";
![img_14.png](img_14.png)

### question 6
select name from airport, game where location = ident and screen_name = "Ilkka"
![img_15.png](img_15.png)

### question 7 
select country.name from country, game, airport where location = ident and screen_name = "Ilkka" and airport.iso_country = country.iso_country ;
![img_16.png](img_16.png)

### question 8
select name from goal, goal_reached, game where game.id = game_id and goal.id = goal_id and screen_name = "Heini";
![img_17.png](img_17.png)

### question 9
select airport.name from airport, game, goal_reached, goal where location = ident and goal.id = goal_id and game.id = game.id and screen_name = "Ilkka" and goal.name = "clouds";
![img_18.png](img_18.png)

### question 10
select country.name from country, game, airport, goal, goal_reached where airport.iso_country = country.iso_country and ident = location and game.id = game_id and screen_name = "Ilkka" and goal.id = goal_id and goal.name = "clouds";
![img_19.png](img_19.png)


# exercise 4

### question 1 
select country.name as 'country name', airport.name as 'airport name' from country inner join airport on airport.iso_country = country.iso_country where country.name = 'finland' and scheduled_service = 'yes';
![img_20.png](img_20.png)

### question 2
select screen_name, airport.name from game, airport where location = ident;
![img_21.png](img_21.png)

### question 3
select screen_name, country.name from game inner join airport on location = ident inner join country on country.iso_country = airport.iso_country;
![img_22.png](img_22.png)

### question 4
select airport.name, screen_name from airport left join game on location = ident where name like "%Hels%";
![img_23.png](img_23.png)

### question 5
select name, screen_name from goal left join goal_reached on goal.id = goal_id left join game on game.id = game_id;
![img_24.png](img_24.png)

# exercise 5

### question 1
select name from country where iso_country in (select iso_country from airport where name like "Satsuma%");
![img_25.png](img_25.png)

### question 2
select airport.name from airport, country where country.iso_country = airport.iso_country and country.name = "Monaco";
![img_26.png](img_26.png)

### question 3
select screen_name from game where id in (select game_id from goal_reached where goal_id in (select id from goal where name = "Clouds"));
![img_27.png](img_27.png)

### question 4
select name from country where iso_country not in (select iso_country from airport);
![img_28.png](img_28.png)

### question 5
select name from goal where id not in (select goal.id from goal, goal_reached, game where game.id = game_id and goal.id = goal_id and screen_name = "Heini");
![img_29.png](img_29.png)

# exercise 6

### question 1
select max(elevation_ft) from airport
![img_30.png](img_30.png)

### question 2
select distinct continent, count(*) from country group by continent; 
![img_31.png](img_31.png)

### question 3
select distinct screen_name, count(*) from game, goal_reached where id = game_id group by scr
![img_33.png](img_33.png)

### question 4
select screen_name from game where co2_consumed in (select min(co2_consumed) from game);
![img_34.png](img_34.png)

### question 5
 select country.name, count(*) from country, airport where airport.iso_country = country.iso_country group by country.iso_country order by count(*) desc limit 50;
 ![img_35.png](img_35.png)
 
### question 6
select country.name from country, airport where country.iso_country = airport.iso_country group by country.iso_country having count(*) > 1000;
![img_36.png](img_36.png)

### question 7
select name from airport where name in (select max(elevation_ft) from airport);
![img_37.png](img_37.png)

### question 8
select country.name from country, airport where country.iso_country = airport.iso_country and airport.name in (select max(elevation_ft) from airport);
![img_38.png](img_38.png)

### question 9
select count(*) from game, goal_reached where id = game_id and screen_name = "Vesa" ;
![img_39.png](img_39.png)

### question 10
select name from airport where latitude_deg in (select min(latitude_deg) from airport);
![img_40.png](img_40.png)

# exercise 7

### question 1
update game set location = (select ident from airport, country where country.iso_country = airport.iso_country and airport.name = "Nottingham Airport"), co2_consumed = co2_consumed + 500 where screen_name = "Vesa";
![img_41.png](img_41.png)

### question 2
choice b
![img_42.png](img_42.png)

### question 3
delete from goal_reached;
![img_43.png](img_43.png)

### question 4
delete from game;
![img_44.png](img_44.png)

