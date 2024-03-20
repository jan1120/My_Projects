use jandb;

create table airbnb_listings (
al_id int,
city varchar (50),
country varchar (50),
number_of_rooms int,
year_listed int

)

insert into airbnb_listings
values
(1,'Paris','France', 5, 2018),
(2, 'Tokyo','Japan', 2, 2017),
(3, 'New York', 'USA', 2, 2022)


select * from airbnb_listings;

-- Get all the columns from a table

select *
from airbnb_listings;

 --Return the city column from the table
 
 select city
 from airbnb_listings

--  Get the city and year_listed columns from the table

select city, year_listed
from airbnb_listings;

-- Get the listing id, city, ordered by the number_of_rooms in ascending order
select al_id, city
from airbnb_listings
order by number_of_rooms asc;

-- Get the listing id, city, ordered by the number_of_rooms in descending order
select al_id, city
from airbnb_listings
order by number_of_rooms desc;

--Get the first 5 rows from the airbnb_listings table

select top 1 * 
from airbnb_listings
order by number_of_rooms;



--Get a unique list of cities where there are listings
select distinct city
from airbnb_listings;

--Get all the listings where number_of_rooms is more or equal to 3
select *
from airbnb_listings
where number_of_rooms >=3;

-- Get all the listings where number_of_rooms is more than 3
select *
from airbnb_listings
where number_of_rooms > 3;

-- Get all the listings where number_of_rooms is exactly equal to 3

select *
from airbnb_listings
where number_of_rooms = 3;

-- Get all the listings where number_of_rooms is lower or equal to 3
select * 
from airbnb_listings
where number_of_rooms <=3;

-- Get all the listings where number_of_rooms is lower than 3

select * 
from airbnb_listings
where number_of_rooms < 3;

--Get all the listings with 3 to 6 rooms

select *
from airbnb_listings
where number_of_rooms between 3 and 6;

-- Get all the listings that are based in ‘Paris

select *
from airbnb_listings
where city ='Paris';

--Get the listings based in the and in ‘USA’ ‘France’
select *
from airbnb_listings
where country in ('USA','France');

--Get all the listings where the city starts with ‘j’ and where the city does not end in 't’
select *
from airbnb_listings
where city like 'j%' and city not like '%t';

--Get all the listings in Paris where number_of_rooms is bigger than 3
select *
from airbnb_listings
where city = 'Paris' and number_of_rooms <=3;

--Get all the listings in Paris OR the ones that were listed after 2012

select *
from airbnb_listings 
where city = 'Paris' and year_listed >2012;

-- Return the listings where number_of_rooms is missing

select *
from airbnb_listings
where number_of_rooms is null;

--Return the listings where number_of_rooms is not missing

select *
from airbnb_listings
where number_of_rooms is not null;

-- Get the total number of rooms available across all listings

select sum(number_of_rooms)
from airbnb_listings;

-- Get the average number of rooms per listing across all listings

select avg(number_of_rooms)
from airbnb_listings;

--Get the listing with the highest number of rooms across all listings

select max(number_of_rooms)
from airbnb_listings;

--Get the listing with the lowest number of rooms across all listings

select min(number_of_rooms)
from airbnb_listings;

--Get the total number of rooms for each country
select country, sum(number_of_rooms) as Total
from airbnb_listings
group by country;

--Get the average number of rooms for each country
select country, avg(number_of_rooms) as total
from airbnb_listings
group by country;

--Get the listing with the maximum number of rooms per country
select country, max(number_of_rooms) as Total
from airbnb_listings
group by country;

--For each country, get the average number of rooms per listing, sorted by ascending order
select country, avg(number_of_rooms) as Total
from airbnb_listings
group by country
order by Total asc;

-- For Japan and the USA, get the average number of rooms per listing in each country
select country, avg(number_of_rooms) as Total
from airbnb_listings
where country in ('USA','Japan')
group by country;

--Get the number of cities per country, where there are listings

select country, count(city) as number_of_cities
from airbnb_listings
group by country;

-- Get all the years where there were more than 100 listings per year
select year_listed
from airbnb_listings
group by year_listed
having count(*)>100;







