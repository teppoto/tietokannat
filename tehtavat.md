**Tietokantatehtävät**

**Osio 3 Yhteen tauluun kohdistuvien kyselyiden harjoitukset**

3.1: Tee kysely, joka tulostaa kaikki sarakkeet goal-talusta.
select*from goal;

![kuva](https://github.com/user-attachments/assets/687ed1a6-5e72-4e72-affb-65f914c26c14)

3.2: Tee kysely, joka tulostaa nimen ja tyypin kaikista Suomessa sijaitsevista lentokentistä. Suomen maatunnus on: FI
select name, type from airport where iso_country = "FI";

![kuva](https://github.com/user-attachments/assets/d16fbbfd-04c1-4179-a1de-ff8f5d5ea3b6)

huom. kuva katkaistu, koska se olisi muuten liian iso.

3.3: Tee kysely, joka tulostaa suomalaisten lentokenttien nimet aakkosjärjestyksessä. Suomen maatunnus: FI
select name from airport where iso_country = "FI" order by name;

![kuva](https://github.com/user-attachments/assets/a013af8e-3305-4049-9cf0-ba98bef37586)

huom. kuva katkaistu, koska se olisi muuten liian iso.

3.4: Tee kysely, joka tulostaa nimen ja tyypin kaikista Suomessa sijaitsevista lentokentistä. Järjestä tulos ensisijaisesti tyypin mukaan ja toissijaisesti nimen mukaan.
select name, type from airport where iso_country = "FI" order by type, name;

![kuva](https://github.com/user-attachments/assets/eb478f42-42f1-406b-b458-69087d7eac5e)

huom. kuva katkaistu, koska se olisi muuten liian iso.

3.5: Tee kysely, joka tulostaa kaikki F-kirjaimella alkavat maan nimet country-taulusta.
select name from country where name like 'F%';

![kuva](https://github.com/user-attachments/assets/5e8cd82c-a0b8-4396-bff5-9c0fe5c8a845)

3.6: Tee kysely, joka tulostaa kaikki country-taulun maiden nimet, joissa esiintyy F-kirjain.
select name from country where name like '%F%';

![kuva](https://github.com/user-attachments/assets/5a11946f-2945-4efb-93a6-f3d039a79ad2)

3.7: Missä locationissa Vesa sijaitsee?
select location from game where screen_name = "Vesa";

![kuva](https://github.com/user-attachments/assets/cfd01c93-35e1-410b-999c-5967f56628bb)

3.8: Kuinkan paljon Ilkka on kuluttanut CO2 budjettia?
select co2_consumed from game where screen_name = "Ilkka";

![kuva](https://github.com/user-attachments/assets/87533c4f-9918-415b-ad4b-13291f3773ec)

3.9: Kuinka paljon alkuperäinen CO2 budjetti on (tulosta CO2 budjetin arvo vain kerran)?
select distinct co2_budget from game;

![kuva](https://github.com/user-attachments/assets/84fa2677-5f90-4bc8-a518-2b8967c85e6f)


**Osio 4 Where-osan liitosehto harjoitukset**

4.1: Tee kysely, joka listaa maan nimen ja lentokentän nimen. Valitse maaksi Islanti ja anna country-taulun name-kentälle alias ”country name” ja airport taulun name-kentälle alias ”airport name”.
select country.name, airport.name as 'airport name' from airport, country where country.iso_country = airport.iso_country and country.name = "Iceland";

![kuva](https://github.com/user-attachments/assets/821a12fc-4629-4d80-b51e-8203ae47527e)

4.2: Listaa Ranskan isojen lentokenttien nimet. Anna kentän nimelle alias "airport name".
select airport.name as 'airport name' from airport, country where airport.iso_country = country.iso_country and country.name = "France" and airport.type = "large_airport";

![kuva](https://github.com/user-attachments/assets/ec0b28a2-ea97-4a9f-ae96-b42194e4a145)

4.3: Tee kysely, joka listaa kaikki Antarktiksella sijaitsevien lentokenttien nimet ja vastaava maan nimi. 
select country.name as 'country_name', airport.name as 'airport_name' from airport, country where airport.iso_country = country.iso_country and country.continent = "AN";

![kuva](https://github.com/user-attachments/assets/a9b2ae6f-912e-460f-be2f-f388c8b50180)

4.4: Kuinka korkealla Heini on paraikaa merenpinnasta mitattuna?
select elevation_ft from airport, game where location = ident and screen_name = "Heini";

![kuva](https://github.com/user-attachments/assets/52e8da02-eb0f-4495-9044-9032f8f5f65f)

4.5: Kuinka korkealla Heini on paraikaa merenpinnasta mitattuna?
select elevation_ft * 0.3048 as elevation_m from airport, game where location = ident and screen_name = "Heini";

![kuva](https://github.com/user-attachments/assets/75dbf3cc-4246-497a-941f-714ed314f264)

4.6: Minkä nimisellä lentokentällä Ilkka on?
select name from airport, game where location = ident and screen_name = "Ilkka";

![kuva](https://github.com/user-attachments/assets/c2994f62-3437-4347-bfac-3232a936a903)

4.7: Minkä nimisessä maassa Ilkka on?
select country.name from game, airport, country where location = ident and airport.iso_country = country.iso_country and screen_name = "Ilkka";

![kuva](https://github.com/user-attachments/assets/3aeb53ff-d3b1-4cc7-a2e4-7bff41b20f95)

4.8: Minkä nimiset säätila-tavoitteet Heini on saavuttanut?
select name from goal, goal_reached, game where game.id = game_id and goal.id = goal_id and screen_name = "Heini";

![kuva](https://github.com/user-attachments/assets/ec18b021-5646-4f2a-a275-bcd9ea4579be)

4.9: Minkä nimisellä lentokentällä Ilkka saavutti säätilan clouds?
select airport.name from game, goal, goal_reached, airport where game.id = game_id and goal.id = goal_id and location = ident and screen_name = "Ilkka" and goal.name = "CLOUDS";

![kuva](https://github.com/user-attachments/assets/534c5705-e75b-482a-b473-1e11c5cd685d)

4.10: Minkä nimisessä maassa Ilkka saavutti säätilan clouds?
select country.name from game, goal, goal_reached, airport, country where game.id = game_id and goal.id = goal_id and location = ident and screen_name = "Ilkka" and goal.name = "CLOUDS" and airport.iso_country = country.iso_country;

![kuva](https://github.com/user-attachments/assets/41e0b257-eb38-4599-9c70-0df407b5c4b2)


**Osio 5 Join harjoitukset**

5.1: Luettele suomalaiset lentokentät, joilla on aikataulutettuja palveluja. Lopputulokseen halutaan sekä maan nimi että lentokentän nimi.
select country.name as "country name", airport.name as "airport name" from country inner join airport on airport.iso_country = country.iso_country where country.name = "Finland" and scheduled_service = "yes";

![kuva](https://github.com/user-attachments/assets/6d6f5da1-052b-47fc-b914-b7c1ad34f131)

5.2: Luettele pelaajanimet ja niiden lentokentrien nimet, joilla he ovat nyt.
select screen_name, airport.name from game inner join airport on airport.ident = game.location;

![kuva](https://github.com/user-attachments/assets/a68f7519-f44c-462a-a604-984755f5ba9d)

5.3: Luettele pelaajanimet ja maat, joissa he ovat nyt.
select screen_name, country.name from game inner join airport on airport.ident = game.location inner join country on country.iso_country = airport.iso_country;

![kuva](https://github.com/user-attachments/assets/0f802e25-2cd5-4f02-bec0-d2bdc5b9d7eb)

5.4: Luette kaikkien niiden lentokenttien nimet, jotka sisältävät merkkijonon "Hels" ja pelaajan nimi, jos joku pelaaja sattuu ko. kentällä olemaan.
select airport.name, screen_name from airport left join game on ident = location where name like "%Hels%";

![kuva](https://github.com/user-attachments/assets/7cfc42a2-5594-4ee9-aa59-f8b1a028844c)

5.5: Luettele kaikki säätilatavoitteiden nimet ja pelaajan nimi, jos pelaaja on sen saavuttanut.
select goal.name, screen_name from goal left join goal_reached on goal.id = goal_reached.goal_id left join game on game.id = goal_reached.game_id;

![kuva](https://github.com/user-attachments/assets/4247f794-d284-464b-9a92-aa96d9693cb3)

**Osio 6 Sisäkysely harjoitukset**

6.1: Minkä nimisessä maassa sijaitsee sanalla ”Satsuma” alkava lentokenttä?
select name from country where iso_country in (select iso_country from airport where name like "%Satsuma%");

![kuva](https://github.com/user-attachments/assets/49a669cc-96e2-4fa7-95d7-7591912e09b2)

6.2: Luettele Monacossa sijaitsevien lentokenttien nimet.
select name from airport where iso_country in (select iso_country from country where name = "Monaco");

![kuva](https://github.com/user-attachments/assets/cdda283e-ff36-4fba-a020-8069e584c652)

6.3: Luettele nimimerkit, jotka ovat saavuttaneet säätilatavoitteen pilvistä (CLOUDS).
select screen_name from game where game.id in(select game_id from goal_reached where goal_id in(select goal.id from goal where name = "CLOUDS"));

![kuva](https://github.com/user-attachments/assets/702b5aee-113f-4fa2-adc2-cc8ec3a8f136)

6.4: Luettele kaikki maat, joissa ei ole lentokenttää.
select name from country where iso_country not in(select iso_country from airport);

![kuva](https://github.com/user-attachments/assets/5d1a8a61-521e-402c-8454-19f5bc9a3fb5)

6.5: Minkä nimiset säätilatavoitteet Heiniltä on saavuttamatta?
select name from goal where id not in(select goal.id from goal, goal_reached, game where game.id = game_id and goal.id = goal_id and screen_name = "Heini");

![kuva](https://github.com/user-attachments/assets/9c09a2ae-7476-4624-8dfa-4b1d384fa0dc)


**Osio 7 Koostetieto kyselyt harjoitukset**

7.1: Kuinka korkealla sijaitsee korkeimmalla sijaitseva lentokenttä?
select max(elevation_ft) from airport;

![kuva](https://github.com/user-attachments/assets/e9e8c383-d76e-45af-859f-be8457e1823c)

7.2: Tee kysely, joka listaa kunkin maanosan, ja niissä sijaitsevien maiden määrän.
select continent, count(*) from country group by continent;

![kuva](https://github.com/user-attachments/assets/ee605686-d55a-4402-9f82-7ab075a9f068)

7.3: Tulosta pelaajien nimimerkit ja pelaajien saavuttamien säätilatavoitteiden lukumäärät.
select screen_name, count(*) from game inner join goal_reached on game.id = game_id inner join goal on goal_id = goal.id group by screen_name;

![kuva](https://github.com/user-attachments/assets/d9db170c-0166-4bbc-9ab8-23423d5314c7)

7.4: Mikä nimimerkki on kuluttanut vähiten hiilijalanjälkeä?
select screen_name from game where co2_consumed in(select min(co2_consumed) from game);

![kuva](https://github.com/user-attachments/assets/5b75baea-b427-4156-8bc5-47d214c912b8)

7.5: Tulosta maan nimi ja lentokenttien lukumäärä kyseisessä maassa. Järjestä tulokset siten, että ylimpänä listassa ovat maat, joissa on eniten lentokenttiä. Ota mukaan vain 50 eniten lentokenttiä sisältävää maata.

![kuva](https://github.com/user-attachments/assets/8ab758ae-91ea-41c0-8293-d13ac21e565c)

7.6: Tulosta niiden maiden nimi, joissa on yli 1000 lentokenttää.
select country.name from airport, country where airport.iso_country = country.iso_country group by country.iso_country having count(*) >= 1000;

![kuva](https://github.com/user-attachments/assets/38d058de-db5b-4086-8149-a7edac6cd994)

7.7: Minkä niminen on maailman korkeimmalla sijaitseva lentokenttä?
select name from airport where elevation_ft in (select max(elevation_ft) from airport);

![kuva](https://github.com/user-attachments/assets/a8ef4ef2-36fc-4614-a929-2c4e8fd97797)

7.8.: Missä maassa sijaitsee maailman korkeimmalla oleva lentokenttä?
select name from country where iso_country in (select iso_country from airport where elevation_ft in (select max(elevation_ft) from airport));

![kuva](https://github.com/user-attachments/assets/72d26ff6-60dd-4a27-b13c-cee6b0fea778)

7.9.: Kuinka monta säätilatavoitetta Vesa on saavuttanut?
select count(*) from game, goal_reached where id = game_id and screen_name = "Vesa";

![kuva](https://github.com/user-attachments/assets/b0858e57-2eb8-4082-92da-4de232266115)

7.10: Mikä on lähimpänä napa-alueita olevan lentokentän nimi?
select airport.name from airport where latitude_deg in (select min(latitude_deg) from airport);

![kuva](https://github.com/user-attachments/assets/754c622a-40c0-4482-9e6e-f474c04baea7)


Osio 8 Päivityskyselyt harjoitukset

8.1:  Vesa lentää nykyiseltä sijainnilta Nottingham Airport:lle. Samalla Vesan hiilijalanjälki kasvaa 500:lla. Päivitä nämä tiedot tietokantaan.
update game set location =(select ident from airport where airport.name = "Nottingham Airport"), co2_consumed = co2_consumed + 500 where screen_name = "Vesa";

![kuva](https://github.com/user-attachments/assets/56438689-5e56-4ba7-816c-ee4a6615e762)

8.2: ![kuva](https://github.com/user-attachments/assets/4f4913c4-ef52-4106-84f2-4f1ad33b741b)

8.3: Poista data goal_reached-taulusta
delete from goal_reached;

![kuva](https://github.com/user-attachments/assets/75ad4489-cd6c-403a-8ca2-b48c68d0ee87)

8.4: Poista data game-taulusta
delete from game;

![kuva](https://github.com/user-attachments/assets/c8bb15d1-2cbb-4c6e-9575-026a198fe7c8)


**Osio Tietokannan suunnittelu harjoitukset**

![kuva](https://github.com/user-attachments/assets/1ae78315-b209-495b-a8be-57e51705d2da)




