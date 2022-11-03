## INGRID-KG
INGRID- KG is an RDF knowledge graph of annotated graffiti, abides by the Linked Data and FAIR principles. Graffiti is an urban phenomenon that is increasingly attracting the interest of the sciences.

### We list some results we retrieved from INGRID Sarql [endpoint](https://graffiti.data.dice-research.org/sparql/) to explore our INGRID-KG.
The [number of triples](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+distinct+%3FConcept+where+%7B%5B%5D+a+%3FConcept%7D+LIMIT+100&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
can be retrieved
using this query: 

```
select count(*)
where
{
    ?s ?p ?o .
}
```
The [number of resources](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+count%28distinct%28%3Fs%29%29%0D%0Awhere%0D%0A%7B%0D%0A%3Fs+%3Fp+%3Fo+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
can be retrieved using this query: 
```
select count(distinct(?s))
where
{
?s ?p ?o .
}
```
The [numper of properties](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+count%28distinct%28%3Fp%29%29%0D%0Awhere%0D%0A%7B%0D%0A%3Fs+%3Fp+%3Fo+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
can be retrieved using this query: 
```
select count(distinct(?p))
where
{
?s ?p ?o .
}
```
And the [number of objects](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+count%28distinct%28%3Fo%29%29%0D%0Awhere%0D%0A%7B%0D%0A%3Fs+%3Fp+%3Fo+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
can be retrieved using this query:
```
select count(distinct(?o))
where
{
?s ?p ?o .
}
```
[Some label values](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+%3Fs+%3Fo%0D%0Awhere%0D%0A%7B%0D%0A++++%3Fs+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23label%3E+%3Fo+.%0D%0A%7D%0D%0ALimit+10%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
can be retrieved using this query:
```
select ?s ?o
where
{
    ?s rdfs:label ?o .
}
Limit 10
```
[Some data types](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+%3Fs+%3Fo%0D%0Awhere%0D%0A%7B%0D%0A++++%3Fs+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23type%3E+%3Fo+.%0D%0A%7D%0D%0ALimit+20%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
can be retrieved using this query:
```
select ?s ?o
where
{
    ?s rdf:type ?o .
}
Limit 10
```
### We retrieved more advanced queries to answer specific questions as you can see in the next ones 

For example, retrieving [Graffiti that were painted by the same crew "AC"](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=%0D%0Aselect+distinct+*+where%0D%0A%7B%3Fs+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2FhasGraffitiSprayerCrew%3E+%0D%0A%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2FAC%3E+.%0D%0A%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2FAC%3E+%0D%0A%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2FhasLongForm%3E+%3Fo.%0D%0A%0D%0A%7D+LIMIT+100%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
can be retrieved using this query:
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct * where
{
  ?s grfo:hasGraffitiSprayerCrew grfr:AC .
  grfr:AC grfo:hasLongForm ?o.
} 
LIMIT 100
```
[Graffiti Sprayer Crew](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+distinct+*+where%0D%0A%7B%0D%0A%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2FAC%3E+%3Fp+%3Fo+.%0D%0A%7D+LIMIT+100%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
can be retrieved using this query:
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
select distinct * where
{
grfr:AC ?p ?o .
} 
LIMIT 100
```
This one can [show all objects: Sprüher/ Crew: EURO; Typ: Tag; Item](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0Aselect+distinct+*+where%0D%0A%7B%3Fs+grfo%3AhasGraffitiSprayerCrew+%3Fcrew+.%0D%0A%3Fcrew+a+grfo%3AGraffitiSprayerCrew+.%0D%0A%3Fcrew+rdfs%3Alabel+%22EURO%22%5E%5Exsd%3Astring+.%0D%0A%3Fs+grfo%3AhasItem+%3Fitem+.%0D%0AFILTER%28+REGEX%28+%3Fitem%2C+%22%21%22+%29+%29+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) 
and it can be retrieved using this query:
```
PREFIX grfp: <https://graffiti.data.dice-research.org/graffiti#>
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct * where
{?s grfo:hasGraffitiSprayerCrew ?crew .
?crew a grfo:GraffitiSprayerCrew .
?crew rdfs:label "EURO"^^xsd:string .
?s grfo:hasItem ?item .
FILTER( REGEX( ?item, "!" ) ) .
}

or

PREFIX grfp: <https://graffiti.data.dice-research.org/graffiti#>
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct * where
{?s grfo:hasGraffitiSprayerCrew ?crew .
?crew a grfo:GraffitiSprayerCrew .
?crew rdfs:label "EURO"^^xsd:string .
?s grfo:hasItem ?item .
FILTER( contains(?item, "!") ) .
} LIMIT 100
```
This [shows all objects: Sprüher/ Crew: EURO; Typ: Tag; Item: _?_ , Stadt: Fundort: Mannheim; Typ: Tag](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0Aselect+distinct+*+where%0D%0A%7B%3Fs+grfo%3AhasGraffitiSprayerCrew+%3Fcrew+.%0D%0A%3Fs+grfo%3AhasItem+%3Fitem+.%0D%0AFILTER%28+contains%28%3Fitem%2C+%22%3F%22%29+%29+.%0D%0A%7D+LIMIT+100%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
and it can be retrieved using this query:
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct * where
{?s grfo:hasGraffitiSprayerCrew ?crew .
?s grfo:hasItem ?item .
FILTER( contains(?item, "?") ) .
} LIMIT 100
```
To answer this question [How many graffities have "a" in their sprayercrew name?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0Aselect+distinct+count%28+%3Fs+%29+as+%3Fcnt+where%0D%0A%7B%3Fs+grfo%3AhasGraffitiSprayerCrew+%3Fcrew+.%0D%0A%3Fcrew+a+grfo%3AGraffitiSprayerCrew+.%0D%0A%3Fcrew+rdfs%3Alabel+%3FcrewName+.%0D%0AFILTER%28+contains%28%3FcrewName%2C+%22a%22%29%29+.%0D%0A%7D+%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+), we can werite this query:
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct count( ?s ) as ?cnt where
{?s grfo:hasGraffitiSprayerCrew ?crew .
?crew a grfo:GraffitiSprayerCrew .
?crew rdfs:label ?crewName .
FILTER( contains(?crewName, "a")) .
} 
```

We can also retrieve the answer of this question [How many crew members in a crew?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0ASELECT+DISTINCT+%3Fcrew%2C+count%28+%3FcrewMember+%29+as+%3Fcnt+WHERE%0D%0A%7B%0D%0A%3Fcrew+a+grfo%3ACrewMember+.%0D%0A%3Fcrew+grfo%3AhasCrewMember+%3FcrewMember+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) by writing this query:
```
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct ?crew, count( ?crewMember ) as ?cnt WHERE
{
?crew a grfo:CrewMember .
?crew grfo:hasCrewMember ?crewMember .
}
```
This question [In how many crews does the crewMember work?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0ASELECT+DISTINCT+%3FcrewMember+count%28%3Fcrew%29+as+%3Fcnt+WHERE%0D%0A%7B%0D%0A%3Fcrew+a+grfo%3ACrewMember+.%0D%0A%3Fcrew+grfo%3AhasCrewMember+%3FcrewMember+.%0D%0A%0D%0A%3FcrewMember+a+grfo%3ACrewMember+.%0D%0A%3FcrewMember+rdfs%3Alabel+%3FcrewMemberLabel.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) can be answered by this query:
```
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct ?crewMember count(?crew) as ?cnt WHERE
{
?crew a grfo:CrewMember .
?crew grfo:hasCrewMember ?crewMember .
?crewMember a grfo:CrewMember .
?crewMember rdfs:label ?crewMemberLabel.
}
```
We can answer [Which crew members work more than in one crew?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+DISTINCT+%3FcrewMemberLabel+%28count%28%3Fcrew%29+as+%3Fcnt%29+WHERE%0D%0A%7B%0D%0A%3Fcrew+a+grfo%3ACrewMember+.%0D%0A%3Fcrew+grfo%3AhasCrewMember+%3FcrewMember+.%0D%0A%3FcrewMember+rdfs%3Alabel+%3FcrewMemberLabel.%0D%0A%0D%0A%7D%0D%0AGROUP+BY+%3FcrewMemberLabel%0D%0AORDER+BY+desc%28%3Fcnt%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) by this query:
```
PREFIX grfp: <https://graffiti.data.dice-research.org/graffiti#>
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>

select distinct ?crewMemberLabel (count(?crew) as ?cnt) WHERE
{
?crew a grfo:Crew .
?crew grfo:hasCrewMember ?crewMember .
?crewMember rdfs:label ?crewMemberLabel.
}
GROUP BY ?crewMemberLabel
ORDER BY desc(?cnt)
or
select  ?crewMemberLabel, ?cnt WHERE {
{
select distinct ?crewMemberLabel, count(?crew) as ?cnt WHERE
{
?crew a grfo:CrewMember .
?crew grfo:hasCrewMember ?crewMember .
?crewMember rdfs:label ?crewMemberLabel.
}
}
FILTER(?cnt > 1)
}
GROUP BY ?crewMemberLabel
ORDER BY desc(?cnt)
```
This query answers [In which crews does the crew member "REAL" work?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+*+WHERE%0D%0A%7B%0D%0A%3Fcrew+a+grfo%3ACrewMember+.%0D%0A%3Fcrew+grfo%3AhasCrewMember+grfr%3AREAL+.%0D%0Agrfr%3AREAL+grfo%3AhasLongForm+%3FcrewMemberLabel+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct* WHERE
{
?crew a grfo:CrewMember .
?crew grfo:hasCrewMember grfr:REAL .
grfr:REAL grfo:hasLngForm ?crewMemberLabel .
}
```
[How many graffities are painted by the crew](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+%3FcrewName+%28count%28%3FgraffitiCrew%29+as+%3Fcnt%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasGraffitiSprayerCrew+%3FgraffitiCrew+.%0D%0A%3FgraffitiCrew+rdfs%3Alabel+%3FcrewName+.%0D%0A%0D%0A%7D%0D%0AGROUP+BY+%3FcrewName%0D%0AORDER+BY+desc%28%3Fcnt%29%0D%0Alimit+100%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) can be answered by this query:
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct ?crewName (count(?graffitiCrew) as ?cnt) WHERE
{
?graffiti grfo:hasGraffitiSprayerCrew ?graffitiCrew .
?graffitiCrew rdfs:label ?crewName .
}
GROUP BY ?crewName
ORDER BY desc(?cnt)
LIMIT 100
```
We answer [How many crews painted graffities?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0ASELECT+%3Ftext+%28count%28%3FgraffitiCrew%29+as+%3Fcnt%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasGraffitiSprayerCrew+%3FgraffitiCrew+.%0D%0A%3Fgraffiti+grfo%3AhasItem+%3Ftext+.%0D%0A%3FgraffitiCrew+rdfs%3Alabel+%3FcrewName+.%0D%0A%0D%0A%7D%0D%0Alimit+100%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) by this query:
```
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select ?text (count(?graffitiCrew) as ?cnt) WHERE
{
?graffiti grfo:hasGraffitiSprayerCrew ?graffitiCrew .
?graffiti grfo:hasItem ?text .
?graffitiCrew rdfs:label ?crewName .
}
LIMIT 100
```
Here is [avg number of styleElements per graffiti(piece)](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3Fcnt%29+AS+%3Favg%29%0D%0AWHERE+%7B%0D%0A+SELECT+DISTINCT+%3Fgraffiti+count%28+%3Felem+%29+AS+%3Fcnt+WHERE%0D%0A+%7B+%3Fgraffiti+grfo%3AhasSyleElement+%3Felem+%7D%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>

select  (AVG(?cnt) AS ?avg)
WHERE {
 SELECT DISTINCT ?graffiti count( ?elem ) AS ?cnt WHERE
 { ?graffiti grfo:hasSyleElement ?elem }
}
```
And [avg number of colour per graffiti](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=%0D%0A+%0D%0APREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3Fcnt%29+AS+%3Favg%29%0D%0AWHERE+%7B%0D%0A+SELECT+DISTINCT+%3Fgraffiti+count%28+%3Felem+%29+AS+%3Fcnt+WHERE%0D%0A+%7B+%3Fgraffiti+grfo%3AhasColour+%3Felem+.%7D%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
 ```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>

select  (AVG(?cnt) AS ?avg)
WHERE {
 SELECT DISTINCT ?graffiti count(?elem) AS ?cnt WHERE
 { ?graffiti grfo:hasColour ?elem }
}
```
[How many graffities has Spanish language](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+DISTINCT+count%28+%3Fgraffiti+%29+AS+%3Fcnt+WHERE%0D%0A%7B+%3Fgraffiti+grfo%3AhasLanguage+%22es+-+Spanisch%22%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) can be answered by this query:
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct count( ?graffiti ) AS ?cnt WHERE
{ ?graffiti grfo:hasLanguage "es - Spanisch"}
```

We also can retrieve [Graffiti in a specific period of time (how many graffities were recorded between 1998 and 2000 years)](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+DISTINCT+count%28+%3Fgraffiti+%29+AS+%3Fcnt+WHERE%0D%0A%7B+%3Fgraffiti+grfo%3AhasRecordingDate+%3Fdate+.%0D%0AFILTER%28%221998-01-01%22%5E%5Exsd%3Adate+%3C%3D+%3Fdate+%26%26+%3Fdate+%3C+%222000-01-01%22%5E%5Exsd%3Adate%29.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) by writing this query:
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct count( ?graffiti ) AS ?cnt WHERE
{ ?graffiti grfo:hasRecordingDate ?date .
FILTER("1998-01-01"^^xsd:date <= ?date && ?date < "2000-01-01"^^xsd:date).
}
```
And the [Graffities filtered by location (city "Essen") and date (between 1998 and 2000 years)](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+count%28+%3Fgraffiti+%29+AS+%3Fcnt+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasLocation+%3Fcity+.%0D%0A%3Fcity+a+grfo%3ACity+.%0D%0A%3Fcity+rdfs%3Alabel+%22Essen%22+.%0D%0A%3Fgraffiti+grfo%3AhasRecordingDate+%3Fdate+.%0D%0AFILTER%28%221998-01-01%22%5E%5Exsd%3Adate+%3C%3D+%3Fdate+%26%26+%3Fdate+%3C+%222000-01-01%22%5E%5Exsd%3Adate%29.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct count( ?graffiti ) AS ?cnt WHERE
{
?graffiti grfo:hasLocation ?city .
?city a grfo:City .
?city rdfs:label "Essen" .
?graffiti grfo:hasRecordingDate ?date .
FILTER("1998-01-01"^^xsd:date <= ?date && ?date < "2000-01-01"^^xsd:date).
}
```
