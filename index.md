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
 select distinct ?graffiti count( ?elem ) AS ?cnt WHERE
 { ?graffiti grfo:hasSyleElement ?elem }
}
```
And [avg number of colour per graffiti](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=%0D%0A+%0D%0APREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3Fcnt%29+AS+%3Favg%29%0D%0AWHERE+%7B%0D%0A+SELECT+DISTINCT+%3Fgraffiti+count%28+%3Felem+%29+AS+%3Fcnt+WHERE%0D%0A+%7B+%3Fgraffiti+grfo%3AhasColour+%3Felem+.%7D%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
 ```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>

select  (AVG(?cnt) AS ?avg)
WHERE {
 select distinct ?graffiti count(?elem) AS ?cnt WHERE
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
What is the average number of Colors for all fully annotated Pieces? (Results are with and without carrier medium Hall of Fame)

1. [With carrier medium Hall of Fame](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3Fcnt%29+AS+%3Favg%29%0D%0AWHERE+%7B%0D%0ASELECT+DISTINCT+%3Fgraffiti+count%28+%3Felem+%29+AS+%3Fcnt+WHERE%7B%0D%0A+%09%09%3Fgraffiti+grfo%3AhasColour+%3Felem+%3B%0D%0A+++++++%09%09%09grfo%3AhasType+%22Piece%2FWriting%2FStyle%22%3B%0D%0A+++++++%09%09%09grfo%3AhasCarrierMedium+%22Hall+of+Fame%22.%0D%0A+%09%7D%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select (AVG(?cnt) AS ?avg)
WHERE {
select distinct ?graffiti count( ?elem ) AS ?cnt WHERE{
 		?graffiti grfo:hasColour ?elem ;
       			grfo:hasType "Piece/Writing/Style" ;
       			grfo:hasCarrierMedium "Hall of Fame".
 	}
}
```
2. [Without carrier medium Hall of Fame](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3Fcnt%29+AS+%3Favg%29%0D%0AWHERE+%7B%0D%0ASELECT+DISTINCT+%3Fgraffiti+count%28+%3Felem+%29+AS+%3Fcnt+WHERE%7B%0D%0A+%09%09%3Fgraffiti+grfo%3AhasColour+%3Felem+%3B%0D%0A+++++++%09%09grfo%3AhasType+%22Piece%2FWriting%2FStyle%22.%0D%0AFILTER+NOT+EXISTS+%7B+%3Fgraffiti+grfo%3AhasCarrierMedium+%22Hall+of+Fame%22%7D+.%0D%0A+%7D%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```

PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select   (AVG(?cnt) AS ?avg)
WHERE {
select distinct  ?graffiti count( ?elem ) AS ?cnt WHERE{
 		?graffiti grfo:hasColour ?elem ;
       		grfo:hasType "Piece/Writing/Style".
FILTER NOT EXISTS { ?graffiti grfo:hasCarrierMedium "Hall of Fame"} .
 }
}
```

To [show every Graffiti with only one name in the field SPRÜHER that has an embedded signature](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3Fs+%28COUNT%28%3Fs%29+AS+%3Fcount%29%0D%0AWHERE+%7B%0D%0A%3Fs+grfo%3AhasGraffitiSprayerCrew+%3Fo+%3B%0D%0A+++++grfo%3AhasEmbeddedGraffiti+%22Signatur%2Fen%22.%0D%0A%7D%0D%0AGROUP+BY+%3Fs%0D%0AHAVING+%28COUNT%28%3Fs%29+%3D+1%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select ?s (COUNT(?s) AS ?count)
WHERE {
?s grfo:hasGraffitiSprayerCrew ?o ;
     grfo:hasEmbeddedGraffiti "Signatur/en".
}
GROUP BY ?s
HAVING (COUNT(?s) = 1)
```
And to [show every City or area (postal code) in which a sprayer painted a Graffiti (Gismo for example)](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fname+%28%3Fplz%29%0D%0AWHERE+%7B%0D%0A++%3Fg++grfo%3AhasPostalCode+%3Fplz+%3B%0D%0A++%09grfo%3AhasGraffitiSprayerCrew+%3Fcrow+.%0D%0A++%3Fcrow+rdfs%3Alabel+%3Fname%0D%0A%7D%0D%0AORDER+BY+%3Fcrow%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select distinct ?name (?plz)
WHERE {
  ?g  grfo:hasPostalCode ?plz ;
  	grfo:hasGraffitiSprayerCrew ?crow .
  ?crow rdfs:label ?name
}
ORDER BY ?crow
```

[Number of PLZ per crew](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3Fcrow+COUNT%28%3Fplz%29+AS+%3Fcount%0D%0AWHERE+%7B%0D%0A++%3Fg++grfo%3AhasPostalCode+%3Fplz+%3B%0D%0A++%09grfo%3AhasGraffitiSprayerCrew+%3Fcrow+.%0D%0A%7D%0D%0AORDER+BY+DESC+%28%3Fcount%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select ?crow COUNT(?plz) AS ?count
WHERE {
  ?g  grfo:hasPostalCode ?plz ;
  	grfo:hasGraffitiSprayerCrew ?crow .
}
ORDER BY DESC (?count)
```
[Number of graffiti per PLZ for the crew “GISMO”](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+COUNT%28%3Fg%29+%3Fplz%0D%0AWHERE+%7B%0D%0A++%3Fg++grfo%3AhasPostalCode+%3Fplz+%3B%0D%0A++%09grfo%3AhasGraffitiSprayerCrew+grfr%3AGISMO+.%0D%0A%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select COUNT(?g) ?plz
WHERE {
    ?g  grfo:postalCode ?plz ;
  	grfo:hasGraffitiSprayerCrew grfr:GISMO .
}
```
To show the period of time in which a sprayer painted Graffitis (use the recording date) with the longest period for a sprayer in the DB

1. [For the GISMO crew](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3FMinDate+%3FMaxDate+%3Fyears%0D%0AWHERE+%7B%0D%0A++%7B%0D%0A+++SELECT+DISTINCT+min%28%3Fdate%29+AS+%3FMinDate+max%28%3Fdate%29+AS+%3FMaxDate+WHERE%7B%0D%0A+%09%3Fg+grfo%3AhasRecordingDate+%3Fdate+%3B%0D%0A++++%09+++grfo%3AhasGraffitiSprayerCrew+grfr%3AGISMO+.%0D%0A+++%7D%0D%0A++%7D%0D%0A++bind%28+year%28%3FMaxDate%29+-+year%28%3FMinDate%29++-+if%28month%28%3FMaxDate%29%3Cmonth%28%3FMinDate%29+%7C%7C+%28month%28%3FMaxDate%29%3Dmonth%28%3FMinDate%29+%26%26+day%28%3FMaxDate%29%3Cday%28%3FMinDate%29%29%2C1%2C0%29+as+%3Fyears+%29%0D%0A+%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select ?MinDate ?MaxDate ?years
WHERE {
  {
   select distinct min(?date) AS ?MinDate max(?date) AS ?MaxDate WHERE{
 	?g grfo:hasRecordingDate ?date ;
    	   grfo:hasGraffitiSprayerCrew grfr:GISMO .
   }
  }
  bind( year(?MaxDate) - year(?MinDate)  - if(month(?MaxDate)<month(?MinDate) || (month(?MaxDate)=month(?MinDate) && day(?MaxDate)<day(?MinDate)),1,0) as ?years )
}
```
2. [For each crew](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3Fcrow+%3FMinDate+%3FMaxDate+%3FYears%0D%0AWHERE+%7B%0D%0A++%7B%0D%0A%09SELECT+DISTINCT+%3Fcrow+min%28%3Fdate%29+AS+%3FMinDate+max%28%3Fdate%29+AS+%3FMaxDate+WHERE%7B%0D%0A++%09%3Fg+grfo%3AhasRecordingDate+%3Fdate+%3B%0D%0A+++++%09+++grfo%3AhasGraffitiSprayerCrew+%3Fcrow+.%0D%0A%09%7D%0D%0A%0D%0A++%7D%0D%0A++bind%28+year%28%3FMaxDate%29+-+year%28%3FMinDate%29++-+if%28month%28%3FMaxDate%29%3Cmonth%28%3FMinDate%29+%7C%7C+%28month%28%3FMaxDate%29%3D+month%28%3FMinDate%29+%26%26+day%28%3FMaxDate%29%3Cday%28%3FMinDate%29%29%2C1%2C0%29+as+%3FYears+%29%0D%0A%7D%0D%0AORDER+BY+DESC%28%3FYears%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select ?crow ?MinDate ?MaxDate ?Years
WHERE {
  {
	select distinct ?crow min(?date) AS ?MinDate max(?date) AS ?MaxDate WHERE{
  	?g grfo:hasRecordingDate ?date ;
     	   grfo:hasGraffitiSprayerCrew ?crow .
	}
  }
  bind( year(?MaxDate) - year(?MinDate)  - if(month(?MaxDate)<month(?MinDate) || (month(?MaxDate)= month(?MinDate) && day(?MaxDate)<day(?MinDate)),1,0) as ?Years )
}
ORDER BY DESC(?Years)
```

[What is the most frequent sprayer in the DB?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT++%3Fcrow+count%28DISTINCT+%3Fg%29+AS+%3FGrPerCrow+WHERE%7B%0D%0A%09%3Fg+grfo%3AhasGraffitiSprayerCrew+%3Fcrow+.%0D%0A%7D%0D%0AORDER+BY+DESC+%28count%28%3Fg%29%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) can be answered by this query:
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select  ?crow count(DISTINCT ?g) AS ?GrPerCrow WHERE{
	?g grfo:hasGraffitiSprayerCrew ?crow .
}
ORDER BY DESC (count(?g))
```
[How many pieces (category Typ) have more than five Stilelemente and are not painted at a Hall of Fame (category Trägermedium)?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+%3Ftyp+%3Fcnt+WHERE+%7B%0D%0A%7B%0D%0ASELECT+%3Ftyp+%28count%28DISTINCT+%3Felem%29+as+%3Fcnt%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasType+%3Ftyp+%3B%0D%0Agrfo%3AhasSyleElement+%3Felem+.%0D%0AFILTER+NOT+EXISTS+%7B+%3Fgraffiti+grfo%3AhasCarrierMedium+%22Hall+of+Fame%22%7D+.%0D%0A%7D%0D%0A%7D%0D%0AFILTER%28%3Fcnt+%3E+5%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) can be answered by this query:
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select ?typ ?cnt WHERE {
{
select ?typ (count(DISTINCT ?elem) as ?cnt) WHERE
{
?graffiti grfo:hasType ?typ ;
grfo:hasSyleElement ?elem .
FILTER NOT EXISTS { ?graffiti grfo:hasCarrierMedium "Hall of Fame"} .
}
}
FILTER(?cnt > 5)
}
```

[How many graffities per category Typ have more than five Stilelemente and are not painted at a Hall of Fame (category Trägermedium)?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3Ftyp+count%28DISTINCT+%3Fgraffiti%29+as+%3FcntGraffities+WHERE+%7B%0D%0A%7B%0D%0ASELECT+%3Fgraffiti+%3Ftyp+%28count%28DISTINCT+%3Felem%29+as+%3Fcnt%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasType+%3Ftyp+%3B%0D%0A++++++%09grfo%3AhasSyleElement+%3Felem+.%0D%0AFILTER+NOT+EXISTS+%7B+%3Fgraffiti+grfo%3AhasCarrierMedium+%22Hall+of+Fame%22%5E%5Exsd%3Astring%7D+.%0D%0A%7D%0D%0A%7D%0D%0AFILTER%28%3Fcnt+%3E+5%29%0D%0A%7D%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select ?typ count(DISTINCT ?graffiti) as ?cntGraffities WHERE {
{
select ?graffiti ?typ (count(DISTINCT ?elem) as ?cnt) WHERE
{
?graffiti grfo:hasType ?typ ;
      	grfo:hasSyleElement ?elem .
FILTER NOT EXISTS { ?graffiti grfo:hasCarrierMedium "Hall of Fame"^^xsd:string} .
}
}
FILTER(?cnt > 5)
}
```
[For showing every Graffiti  with more than 3 Sprayer Names](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3Fgraffiti%2C+%3Fcnt+WHERE+%7B%0D%0A%7B%0D%0ASELECT+%3Fgraffiti+%28count%28%3FgraffitiCrew%29+as+%3Fcnt%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasGraffitiSprayerCrew+%3FgraffitiCrew+.%0D%0A%7D%0D%0A%7D%0D%0AFILTER%28%3Fcnt+%3E+3%29%0D%0A%7D%0D%0AGROUP+BY+%3Fgraffiti%0D%0AORDER+BY+desc%28%3Fcnt%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+), we can write this query:

```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select ?graffiti, ?cnt WHERE {
{
select ?graffiti (count(?graffitiCrew) as ?cnt) WHERE
{
?graffiti grfo:hasGraffitiSprayerCrew ?graffitiCrew .
}
}
FILTER(?cnt > 3)
}
GROUP BY ?graffiti
ORDER BY desc(?cnt)
```
And the [number of graffiti per PLZ with the topic „Politik“ in Mannheim](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+%28COUNT%28%3Fg%29+as+%3FnumberOfGraffiti%29+%3Fplz%0D%0AWHERE+%7B%0D%0A++%3Fg++grfo%3AhasPostalCode+%3Fplz+%3B%0D%0A++%09grfo%3AhasLocation+grfr%3AMannheim+%3B%0D%0A++%09grfo%3AhasTheme+%22Politik%22.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select (COUNT(?g) as ?numberOfGraffiti) ?plz
WHERE {
  ?g  grfo:hasPostalCode ?plz ;
  	grfo:hasLocation grfr:Mannheim ;
  	grfo:hasTheme "Politik".
}
```
[What is the average number of letters in the Item field for the typ “Spruch/ Konzeptaufruf”? with showing results without spaces betwenn letters](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3FitemLen%29+AS+%3Favg%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasType+%22Spruch%2FKonzeptaufruf%22%3B%0D%0A++++++%09grfo%3AhasItem+%3Fitem+.%0D%0ABIND%28replace%28%3Fitem%2C+%22+%22%2C+%22%22%29+as+%3FwithoutSpace%29%0D%0ABIND+%28strlen%28%3FwithoutSpace%29+AS+%3FitemLen%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select (AVG(?itemLen) AS ?avg) WHERE
{
?graffiti grfo:hasType "Spruch/Konzeptaufruf";
      	grfo:hasItem ?item .
BIND(replace(?item, " ", "") as ?withoutSpace)
BIND (strlen(?withoutSpace) AS ?itemLen)
}
```
And the [number of letters for the item "RIOT RADIO" without spaces example](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+%3FitemLen+WHERE%0D%0A%7B%0D%0A%3Fs+grfo%3AhasItem+%22RIOT+RADIO%22%40en.%0D%0A%3Fs+grfo%3AhasItem+%3Fitem.%0D%0Abind%28replace%28%3Fitem%2C+%22+%22%2C+%22%22%29+as+%3FwithoutSpace%29%0D%0A++bind%28strlen%28%3FwithoutSpace%29+as+%3FitemLen%29.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select ?itemLen WHERE
{
?s grfo:hasItem "RIOT RADIO"@en.
?s grfo:hasItem ?item.
bind(replace(?item, " ", "") as ?withoutSpace)
  bind(strlen(?withoutSpace) as ?itemLen).
}
```
The answer of this question [what is the average number of letters in the Itemfield for the typ “Spruch/ Konzeptaufruf” + the topic “Politik”](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3FitemLen%29+AS+%3Favg%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasType+%22Spruch%2FKonzeptaufruf%22%3B%0D%0A++++++++++%09grfo%3AhasTheme+%22Politik%22%3B%0D%0A++++++++++%09grfo%3AhasItem+%3Fitem+.%0D%0ABIND+%28strlen%28%3Fitem%29+AS+%3FitemLen%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) is retrieved by this query:

```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select (AVG(?itemLen) AS ?avg) WHERE
{
?graffiti grfo:hasType "Spruch/Konzeptaufruf";
          	grfo:hasTheme "Politik";
          	grfo:hasItem ?item .
BIND (strlen(?item) AS ?itemLen)
}
```
The query below can retrieve the [Graffities with more than one sprayer name](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0ASELECT+%3Fgraffiti%2C+%3Ftext%2C+%3Fcnt+WHERE+%7B%0D%0A%7B%0D%0ASELECT+%3Fgraffiti+%3Ftext+%28count%28%3FgraffitiCrew%29+as+%3Fcnt%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasGraffitiSprayerCrew+%3FgraffitiCrew+.%0D%0A%3Fgraffiti+grfo%3AhasItem+%3Ftext+.%0D%0A%3Fgraffiti+grfo%3AhasType+%22Piece%2FWriting%2FStyle%22.%0D%0A%3FgraffitiCrew+rdfs%3Alabel+%3FcrewName+.%0D%0A%0D%0A%7D%0D%0A%7D%0D%0AFILTER%28%3Fcnt+%3E+1%29%0D%0A%7D%0D%0AGROUP+BY+%3Fgraffiti%0D%0AORDER+BY+desc%28%3Fcnt%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select ?graffiti, ?text, ?cnt WHERE {
{
select ?graffiti ?text (count(?graffitiCrew) as ?cnt) WHERE
{
?graffiti grfo:hasGraffitiSprayerCrew ?graffitiCrew .
?graffiti grfo:hasItem ?text .
?graffiti grfo:hasType "Piece/Writing/Style".
?graffitiCrew rdfs:label ?crewName .
}
}
FILTER(?cnt > 1)
}
GROUP BY ?graffiti
ORDER BY desc(?cnt)
```
[What is the most frequent language in the category Typ/Spruch/Konzeptaufruf ?  Comparison for the results depending on the period of time (1980-1989, 1990-1999 and so on..](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT++%3Flang+count%28DISTINCT+%3Fg%29+AS+%3FGrPerLang+WHERE%7B%0D%0A%09%3Fg+grfo%3AhasType+%22Spruch%2FKonzeptaufruf%22.%0D%0A%09%3Fg+grfo%3AhasLanguage+%3Flang%0D%0A%7D%0D%0AORDER+BY+DESC+%28count%28%3Fg%29%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) can be answered by this query:

```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select  ?lang count(DISTINCT ?g) AS ?GrPerLang WHERE{
	?g grfo:hasType "Spruch/Konzeptaufruf".
	?g grfo:hasLanguage ?lang
}
ORDER BY DESC (count(?g))
```
Here is [a comparison for the results depending on the period of time (1990-1999)](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT++%3Flang+count%28DISTINCT+%3Fg%29+AS+%3FGrPerLang+WHERE%7B%0D%0A%09%3Fg+grfo%3AhasType+%22Spruch%2FKonzeptaufruf%22.%0D%0A%09%3Fg+grfo%3AhasLanguage+%3Flang.%0D%0A%09%3Fg+grfo%3AhasRecordingDate+%3Fdate+.%0D%0AFILTER%28%221990-01-01%22%5E%5Exsd%3Adate+%3C%3D+%3Fdate+%26%26+%3Fdate+%3C+%221999-12-31%22%5E%5Exsd%3Adate%29.%0D%0A%0D%0A%7D%0D%0AORDER+BY+DESC+%28count%28%3Fg%29%29+%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select  ?lang count(DISTINCT ?g) AS ?GrPerLang WHERE{
	?g grfo:hasType "Spruch/Konzeptaufruf".
	?g grfo:hasLanguage ?lang.
	?g grfo:hasRecordingDate ?date .
FILTER("1990-01-01"^^xsd:date <= ?date && ?date < "1999-12-31"^^xsd:date).

}
ORDER BY DESC (count(?g)) 
```
In addtion, we can retrieve the [number of used color per crew](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+%3FgraffitiCrew+%3Fcolour++%28count%28%3Fcolour%29+as+%3Fcount%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasGraffitiSprayerCrew+%3FgraffitiCrew+.%0D%0A%3FgraffitiCrew+a+grfo%3AGraffitiSprayerCrew+.%0D%0A%3Fgraffiti+grfo%3AhasColour+%3Fcolour+.%0D%0A%7D%0D%0AGROUP+BY+%3FgraffitiCrew+%3Fcolour%0D%0AORDER+BY+DESC%28%3Fcount%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select disntict ?graffitiCrew ?colour  (count(?colour) as ?count) WHERE
{
?graffiti grfo:hasGraffitiSprayerCrew ?graffitiCrew .
?graffitiCrew a grfo:GraffitiSprayerCrew .
?graffiti grfo:hasColour ?colour .
}
GROUP BY ?graffitiCrew ?colour
ORDER BY DESC(?count)
```


and [find all sub-graffities with comment](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+count%28DISTINCT+*%29+WHERE%0D%0A%7B%0D%0A%3Fg+a+grfo%3AGraffiti+.%0D%0A%3Fg+grfo%3AhasType+%22Comment%22+.%0D%0A%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

```
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select count(DISTINCT *) WHERE
{
?g a grfo:Graffiti .
?g grfo:hasType "Comment" .

}
```
