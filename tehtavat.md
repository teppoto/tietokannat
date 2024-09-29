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



