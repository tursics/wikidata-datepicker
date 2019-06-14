# wikidata-datepicker

Todo: write this readme file

# notes

* HTML sample code: http://johanbroddfelt.se/javascript_date_picker_from_scratch-31
* Home of wikidata samples: https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples
* sample query List of actors with pictures with year of birth and/or death: https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples#List_of_actors_with_pictures_with_year_of_birth_and/or_death
* sample query Calendar of birth dates of women who studied at the University of Oxford: https://www.wikidata.org/wiki/Wikidata:SPARQL_query_service/queries/examples#Calendar_of_birth_dates_of_women_who_studied_at_the_University_of_Oxford

# used query

#added before 2016-10

#defaultView:ImageGrid
SELECT ?humanLabel ?dob ?dod ?picture
WHERE
{
?human wdt:P31 wd:Q5
; wdt:P106 wd:Q33999 .
?human wdt:P18 ?picture .
    ?human p:P569/psv:P569 ?date_of_birth. # birth date
OPTIONAL { ?human p:P570/psv:P570 ?date_of_death. ?date_of_death wikibase:timeValue ?dod .}.
    ?date_of_birth wikibase:timeValue ?dob .
SERVICE wikibase:label {
bd:serviceParam wikibase:language "en" .
}
}
LIMIT 366
