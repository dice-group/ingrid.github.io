## INGRID-KG
Graffiti is an urban phenomenon that is increasingly attracting the interest of the sciences.
To the best of our knowledge, no suitable data corpora are available for systematic research until now.
The Information System Graffiti in Germany project (INGRID) closes this gap by dealing with graffiti image collections that have been made available to the project for public use.
Within INGRID, the graffiti images are collected, digitized and annotated.

INGRID-KG aims to support the rapid access to a comprehensive data source on INGRID targeted especially by researchers.
In particular, INGRID-KG is an RDF knowledge graph of annotated graffiti, abides by the Linked Data and FAIR principles.
We weekly updating INGRID-KG by augmenting the new annotated graffiti to our knowledge graph.  
Our generation pipeline applies RDF data conversion, link discovery and data fusion approaches to the original data.
INGRID-KG is publicly available under the **Creative Commons Attribution 4.0 International** license. 
## Annotation Manual in [German](https://github.com/dice-group/ingrid.github.io/blob/main/INGRID_Manual_German.pdf)
## Annotation Manual in [English](https://github.com/dice-group/ingrid.github.io/blob/main/INGRID_Manual_Oktober_2019%20en.pdf)

### A list of SPARQL queries from the [INGRID-KG endpoint](https://graffiti.data.dice-research.org/sparql/).



[Count the number of resources?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+count%28distinct%28%3Fs%29%29%0D%0Awhere%0D%0A%7B%0D%0A%3Fs+%3Fp+%3Fo+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

```sparql
SELECT count(distinct(?s)) WHERE{
	?s ?p ?o .
}
```

[Count the number of triples?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+distinct+%3FConcept+where+%7B%5B%5D+a+%3FConcept%7D+LIMIT+100&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

```sparql
SELECT count(*) WHERE {
	?s ?p ?o .
}
```

[Count the number of properties?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+count%28distinct%28%3Fp%29%29%0D%0Awhere%0D%0A%7B%0D%0A%3Fs+%3Fp+%3Fo+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
SELECT count(distinct(?p)) WHERE{
	?s ?p ?o .
}
```
[Count the number of objects?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+count%28distinct%28%3Fo%29%29%0D%0Awhere%0D%0A%7B%0D%0A%3Fs+%3Fp+%3Fo+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

```sparql
SELECT count(distinct(?o)) WHERE{
	?s ?p ?o .
}

```

[Retrieve a set of 100 random graffiti that were painted by the same crew _"AC"_](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=%0D%0Aselect+distinct+*+where%0D%0A%7B%3Fs+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2FhasGraffitiSprayerCrew%3E+%0D%0A%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2FAC%3E+.%0D%0A%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2FAC%3E+%0D%0A%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2FhasLongForm%3E+%3Fo.%0D%0A%0D%0A%7D+LIMIT+100%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct * WHERE{
	?s grfo:hasGraffitiSprayerCrew grfr:AC .
	grfr:AC grfo:hasLongForm ?o.
} 
LIMIT 100
```

[Show all graffiti created by the sprayer crew _"EURO"_ containing _"!"_](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0Aselect+distinct+*+where%0D%0A%7B%3Fs+grfo%3AhasGraffitiSprayerCrew+%3Fcrew+.%0D%0A%3Fcrew+a+grfo%3AGraffitiSprayerCrew+.%0D%0A%3Fcrew+rdfs%3Alabel+%22EURO%22%5E%5Exsd%3Astring+.%0D%0A%3Fs+grfo%3AhasItem+%3Fitem+.%0D%0AFILTER%28+REGEX%28+%3Fitem%2C+%22%21%22+%29+%29+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) 

```sparql
PREFIX grfp: <https://graffiti.data.dice-research.org/graffiti#>
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct * where{
	?s grfo:hasGraffitiSprayerCrew ?crew .
	?crew a grfo:GraffitiSprayerCrew .
	?crew rdfs:label "EURO" .
	?s grfo:hasItem ?item .
	FILTER( REGEX( ?item, "!" ) ) .
}
```

[Show all graffiti created by the sprayer crew _"EURO"_ containing _"?"_](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0Aselect+distinct+*+where%0D%0A%7B%3Fs+grfo%3AhasGraffitiSprayerCrew+%3Fcrew+.%0D%0A%3Fs+grfo%3AhasItem+%3Fitem+.%0D%0AFILTER%28+contains%28%3Fitem%2C+%22%3F%22%29+%29+.%0D%0A%7D+LIMIT+100%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct * where{
	?s grfo:hasGraffitiSprayerCrew ?crew .
	?s grfo:hasItem ?item .
	FILTER( contains(?item, "?") ) .
} 
LIMIT 100
```
[How many graffities have "a" in their sprayercrew name?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0Aselect+distinct+count%28+%3Fs+%29+as+%3Fcnt+where%0D%0A%7B%3Fs+grfo%3AhasGraffitiSprayerCrew+%3Fcrew+.%0D%0A%3Fcrew+a+grfo%3AGraffitiSprayerCrew+.%0D%0A%3Fcrew+rdfs%3Alabel+%3FcrewName+.%0D%0AFILTER%28+contains%28%3FcrewName%2C+%22a%22%29%29+.%0D%0A%7D+%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct count( ?s ) as ?cnt where{
	?s grfo:hasGraffitiSprayerCrew ?crew .
	?crew a grfo:GraffitiSprayerCrew .
	?crew rdfs:label ?crewName .
	FILTER( contains(?crewName, "a")) .
} 
```

[How many crew members in each crew?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0ASELECT+DISTINCT+%3Fcrew%2C+count%28+%3FcrewMember+%29+as+%3Fcnt+WHERE%0D%0A%7B%0D%0A%3Fcrew+a+grfo%3ACrewMember+.%0D%0A%3Fcrew+grfo%3AhasCrewMember+%3FcrewMember+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct ?crew, count( ?crewMember ) as ?cnt WHERE{
	?crew a grfo:CrewMember .
	?crew grfo:hasCrewMember ?crewMember .
}
```
[To how many crews does a crew member belong?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0ASELECT+DISTINCT+%3FcrewMember+count%28%3Fcrew%29+as+%3Fcnt+WHERE%0D%0A%7B%0D%0A%3Fcrew+a+grfo%3ACrewMember+.%0D%0A%3Fcrew+grfo%3AhasCrewMember+%3FcrewMember+.%0D%0A%0D%0A%3FcrewMember+a+grfo%3ACrewMember+.%0D%0A%3FcrewMember+rdfs%3Alabel+%3FcrewMemberLabel.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) 

```sparql
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct ?crewMember count(?crew) as ?cnt WHERE{
	?crew a grfo:CrewMember .
	?crew grfo:hasCrewMember ?crewMember .
	?crewMember a grfo:CrewMember .
	?crewMember rdfs:label ?crewMemberLabel.
}
```

[Which crew members work in more than one crew?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+DISTINCT+%3FcrewMemberLabel+%28count%28%3Fcrew%29+as+%3Fcnt%29+WHERE%0D%0A%7B%0D%0A%3Fcrew+a+grfo%3ACrewMember+.%0D%0A%3Fcrew+grfo%3AhasCrewMember+%3FcrewMember+.%0D%0A%3FcrewMember+rdfs%3Alabel+%3FcrewMemberLabel.%0D%0A%0D%0A%7D%0D%0AGROUP+BY+%3FcrewMemberLabel%0D%0AORDER+BY+desc%28%3Fcnt%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) 
```sparql
PREFIX grfp: <https://graffiti.data.dice-research.org/graffiti#>
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>

SELECT distinct ?crewMemberLabel (count(?crew) as ?cnt) WHERE{
	?crew a grfo:Crew .
	?crew grfo:hasCrewMember ?crewMember .
	?crewMember rdfs:label ?crewMemberLabel.
}
GROUP BY ?crewMemberLabel
ORDER BY desc(?cnt)
```

[In which crews does the crew member "REAL" work?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+*+WHERE%0D%0A%7B%0D%0A%3Fcrew+a+grfo%3ACrewMember+.%0D%0A%3Fcrew+grfo%3AhasCrewMember+grfr%3AREAL+.%0D%0Agrfr%3AREAL+grfo%3AhasLongForm+%3FcrewMemberLabel+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct* WHERE{
	?crew a grfo:CrewMember .
	?crew grfo:hasCrewMember grfr:REAL .
	grfr:REAL grfo:hasLngForm ?crewMemberLabel .
}
```

[How many graffities were painted by each crew?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0Aselect+distinct+%3FcrewName+%28count%28%3FgraffitiCrew%29+as+%3Fcnt%29+WHERE%7B%0D%0A%09%3Fgraffiti+grfo%3AhasGraffitiSprayerCrew+%3FgraffitiCrew+.%0D%0A%09%3FgraffitiCrew+rdfs%3Alabel+%3FcrewName+.%0D%0A%7D%0D%0AGROUP+BY+%3FcrewName%0D%0AORDER+BY+desc%28%3Fcnt%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) 
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct ?crewName (count(?graffitiCrew) as ?cnt) WHERE{
	?graffiti grfo:hasGraffitiSprayerCrew ?graffitiCrew .
	?graffitiCrew rdfs:label ?crewName .
}
GROUP BY ?crewName
ORDER BY desc(?cnt)
```
[What is the average number of colours per graffiti?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=%0D%0A+%0D%0APREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3Fcnt%29+AS+%3Favg%29%0D%0AWHERE+%7B%0D%0A+SELECT+DISTINCT+%3Fgraffiti+count%28+%3Felem+%29+AS+%3Fcnt+WHERE%0D%0A+%7B+%3Fgraffiti+grfo%3AhasColour+%3Felem+.%7D%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
 ```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>

SELECT  (AVG(?cnt) AS ?avg) WHERE {
	SELECT distinct ?graffiti count(?elem) AS ?cnt WHERE{
		?graffiti grfo:hasColour ?elem 
	}
}
```

[How many graffities contain some_Spanish?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+DISTINCT+count%28+%3Fgraffiti+%29+AS+%3Fcnt+WHERE%0D%0A%7B+%3Fgraffiti+grfo%3AhasLanguage+%22es+-+Spanisch%22%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct count( ?graffiti ) AS ?cnt WHERE{ 
	?graffiti grfo:hasLanguage "es - Spanisch"
}
```

[How many graffities were recorded between the years 1998 and 2000?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+DISTINCT+count%28+%3Fgraffiti+%29+AS+%3Fcnt+WHERE%0D%0A%7B+%3Fgraffiti+grfo%3AhasRecordingDate+%3Fdate+.%0D%0AFILTER%28%221998-01-01%22%5E%5Exsd%3Adate+%3C%3D+%3Fdate+%26%26+%3Fdate+%3C+%222000-01-01%22%5E%5Exsd%3Adate%29.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct count( ?graffiti ) AS ?cnt WHERE{ 
	?graffiti grfo:hasRecordingDate ?date .
	FILTER("1998-01-01"^^xsd:date <= ?date && ?date < "2000-01-01"^^xsd:date).
}
```

[Graffities filtered by location (city "Essen") and date (between the years 1998 and 2000)](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+count%28+%3Fgraffiti+%29+AS+%3Fcnt+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasLocation+%3Fcity+.%0D%0A%3Fcity+a+grfo%3ACity+.%0D%0A%3Fcity+rdfs%3Alabel+%22Essen%22+.%0D%0A%3Fgraffiti+grfo%3AhasRecordingDate+%3Fdate+.%0D%0AFILTER%28%221998-01-01%22%5E%5Exsd%3Adate+%3C%3D+%3Fdate+%26%26+%3Fdate+%3C+%222000-01-01%22%5E%5Exsd%3Adate%29.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct count( ?graffiti ) AS ?cnt WHERE{
	?graffiti grfo:hasLocation ?city .
	?city a grfo:City .
	?city rdfs:label "Essen" .
	?graffiti grfo:hasRecordingDate ?date .
	FILTER("1998-01-01"^^xsd:date <= ?date && ?date < "2000-01-01"^^xsd:date).
}
```

[What is the average number of Colors for all fully annotated Pieces_(with carrier medium Hall of Fame)_?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3Fcnt%29+AS+%3Favg%29%0D%0AWHERE+%7B%0D%0ASELECT+DISTINCT+%3Fgraffiti+count%28+%3Felem+%29+AS+%3Fcnt+WHERE%7B%0D%0A+%09%09%3Fgraffiti+grfo%3AhasColour+%3Felem+%3B%0D%0A+++++++%09%09%09grfo%3AhasType+%22Piece%2FWriting%2FStyle%22%3B%0D%0A+++++++%09%09%09grfo%3AhasCarrierMedium+%22Hall+of+Fame%22.%0D%0A+%09%7D%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select (AVG(?cnt) AS ?avg)
WHERE {
SELECT distinct ?graffiti count( ?elem ) AS ?cnt WHERE{
 		?graffiti grfo:hasColour ?elem ;
       			grfo:hasType "Piece/Writing/Style" ;
       			grfo:hasCarrierMedium "Hall of Fame".
 	}
}
```

[What is the average number of Colors for all fully annotated Pieces _(without carrier medium Hall of Fame)_?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3Fcnt%29+AS+%3Favg%29%0D%0AWHERE+%7B%0D%0ASELECT+DISTINCT+%3Fgraffiti+count%28+%3Felem+%29+AS+%3Fcnt+WHERE%7B%0D%0A+%09%09%3Fgraffiti+grfo%3AhasColour+%3Felem+%3B%0D%0A+++++++%09%09grfo%3AhasType+%22Piece%2FWriting%2FStyle%22.%0D%0AFILTER+NOT+EXISTS+%7B+%3Fgraffiti+grfo%3AhasCarrierMedium+%22Hall+of+Fame%22%7D+.%0D%0A+%7D%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select   (AVG(?cnt) AS ?avg)
WHERE {
SELECT distinct  ?graffiti count( ?elem ) AS ?cnt WHERE{
 		?graffiti grfo:hasColour ?elem ;
       		grfo:hasType "Piece/Writing/Style".
FILTER NOT EXISTS { ?graffiti grfo:hasCarrierMedium "Hall of Fame"} .
 }
}
```

[Show every Graffiti with only one name in the field SPRÜHER that has an embedded signature](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3Fs+%28COUNT%28%3Fs%29+AS+%3Fcount%29%0D%0AWHERE+%7B%0D%0A%3Fs+grfo%3AhasGraffitiSprayerCrew+%3Fo+%3B%0D%0A+++++grfo%3AhasEmbeddedGraffiti+%22Signatur%2Fen%22.%0D%0A%7D%0D%0AGROUP+BY+%3Fs%0D%0AHAVING+%28COUNT%28%3Fs%29+%3D+1%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT ?crow (COUNT(?s) AS ?count) WHERE {
	?crow grfo:hasGraffitiSprayerCrew ?o ;
	grfo:hasEmbeddedGraffiti "Signatur/en".
}
GROUP BY ?crow
HAVING (COUNT(?s) = 1)
```

[Show every postal code in which a sprayer painted a graffiti?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+%3Fname+%28%3Fplz%29%0D%0AWHERE+%7B%0D%0A++%3Fg++grfo%3AhasPostalCode+%3Fplz+%3B%0D%0A++%09grfo%3AhasGraffitiSprayerCrew+%3Fcrow+.%0D%0A++%3Fcrow+rdfs%3Alabel+%3Fname%0D%0A%7D%0D%0AORDER+BY+%3Fcrow%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT distinct ?name (?plz) WHERE {
	?g  grfo:hasPostalCode ?plz ;
  	grfo:hasGraffitiSprayerCrew ?crow .
  	?crow rdfs:label ?name
}
ORDER BY ?crow
```

[Count the number of postal code areas per crew?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3Fcrow+COUNT%28%3Fplz%29+AS+%3Fcount%0D%0AWHERE+%7B%0D%0A++%3Fg++grfo%3AhasPostalCode+%3Fplz+%3B%0D%0A++%09grfo%3AhasGraffitiSprayerCrew+%3Fcrow+.%0D%0A%7D%0D%0AORDER+BY+DESC+%28%3Fcount%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT ?crow COUNT(?plz) AS ?count WHERE {
  	?g  grfo:hasPostalCode ?plz ;
	grfo:hasGraffitiSprayerCrew ?crow .
}
ORDER BY DESC (?count)
```

[Count the number of graffiti per postal code for the crew _“GISMO”_?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+COUNT%28%3Fg%29+%3Fplz%0D%0AWHERE+%7B%0D%0A++%3Fg++grfo%3AhasPostalCode+%3Fplz+%3B%0D%0A++%09grfo%3AhasGraffitiSprayerCrew+grfr%3AGISMO+.%0D%0A%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT COUNT(?g) ?plz WHERE {
	?g  grfo:postalCode ?plz ;
    	    grfo:hasGraffitiSprayerCrew grfr:GISMO .
}
```
[Show the period of time in which a sprayer painted each graffitis (useing the recording date) with the longest period for a sprayer in the knowledge graph for the _GISMO_ crew?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3FMinDate+%3FMaxDate+%3Fyears%0D%0AWHERE+%7B%0D%0A++%7B%0D%0A+++SELECT+DISTINCT+min%28%3Fdate%29+AS+%3FMinDate+max%28%3Fdate%29+AS+%3FMaxDate+WHERE%7B%0D%0A+%09%3Fg+grfo%3AhasRecordingDate+%3Fdate+%3B%0D%0A++++%09+++grfo%3AhasGraffitiSprayerCrew+grfr%3AGISMO+.%0D%0A+++%7D%0D%0A++%7D%0D%0A++bind%28+year%28%3FMaxDate%29+-+year%28%3FMinDate%29++-+if%28month%28%3FMaxDate%29%3Cmonth%28%3FMinDate%29+%7C%7C+%28month%28%3FMaxDate%29%3Dmonth%28%3FMinDate%29+%26%26+day%28%3FMaxDate%29%3Cday%28%3FMinDate%29%29%2C1%2C0%29+as+%3Fyears+%29%0D%0A+%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT ?MinDate ?MaxDate ?years WHERE {
   	SELECT distinct min(?date) AS ?MinDate max(?date) AS ?MaxDate WHERE{
 		?g grfo:hasRecordingDate ?date ;
    	  	 grfo:hasGraffitiSprayerCrew grfr:GISMO .
   	}
  	bind( year(?MaxDate) - year(?MinDate)  - if(month(?MaxDate)<month(?MinDate) || (month(?MaxDate)=month(?MinDate) && day(?MaxDate)<day(?MinDate)),1,0) as ?years )
}
```

[Show the period of time in which a sprayer painted each graffitis (useing the recording date) with the longest period for a sprayer in the knowledge graph for _each_ crew?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3Fcrow+%3FMinDate+%3FMaxDate+%3FYears%0D%0AWHERE+%7B%0D%0A++%7B%0D%0A%09SELECT+DISTINCT+%3Fcrow+min%28%3Fdate%29+AS+%3FMinDate+max%28%3Fdate%29+AS+%3FMaxDate+WHERE%7B%0D%0A++%09%3Fg+grfo%3AhasRecordingDate+%3Fdate+%3B%0D%0A+++++%09+++grfo%3AhasGraffitiSprayerCrew+%3Fcrow+.%0D%0A%09%7D%0D%0A%0D%0A++%7D%0D%0A++bind%28+year%28%3FMaxDate%29+-+year%28%3FMinDate%29++-+if%28month%28%3FMaxDate%29%3Cmonth%28%3FMinDate%29+%7C%7C+%28month%28%3FMaxDate%29%3D+month%28%3FMinDate%29+%26%26+day%28%3FMaxDate%29%3Cday%28%3FMinDate%29%29%2C1%2C0%29+as+%3FYears+%29%0D%0A%7D%0D%0AORDER+BY+DESC%28%3FYears%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT ?crow ?MinDate ?MaxDate ?Years WHERE{
	SELECT distinct ?crow min(?date) AS ?MinDate max(?date) AS ?MaxDate WHERE{
  		?g grfo:hasRecordingDate ?date ;
		grfo:hasGraffitiSprayerCrew ?crow .
	}
	bind( year(?MaxDate) - year(?MinDate)  - if(month(?MaxDate)<month(?MinDate) || (month(?MaxDate)= month(?MinDate) && day(?MaxDate)<day(?MinDate)),1,0) as ?Years )
}
ORDER BY DESC(?Years)
```

[What is the most frequent sprayer in the DB?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT++%3Fcrow+count%28DISTINCT+%3Fg%29+AS+%3FGrPerCrow+WHERE%7B%0D%0A%09%3Fg+grfo%3AhasGraffitiSprayerCrew+%3Fcrow+.%0D%0A%7D%0D%0AORDER+BY+DESC+%28count%28%3Fg%29%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) can be answered by this query:
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT  ?crow count(DISTINCT ?g) AS ?GrPerCrow WHERE{
	?g grfo:hasGraffitiSprayerCrew ?crow .
}
ORDER BY DESC (count(?g))
```

[How many pieces (category Type) have more than five Stilelemente and are not painted at a Hall of Fame (category Trägermedium)?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+%3Ftyp+%3Fcnt+WHERE+%7B%0D%0A%7B%0D%0ASELECT+%3Ftyp+%28count%28DISTINCT+%3Felem%29+as+%3Fcnt%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasType+%3Ftyp+%3B%0D%0Agrfo%3AhasSyleElement+%3Felem+.%0D%0AFILTER+NOT+EXISTS+%7B+%3Fgraffiti+grfo%3AhasCarrierMedium+%22Hall+of+Fame%22%7D+.%0D%0A%7D%0D%0A%7D%0D%0AFILTER%28%3Fcnt+%3E+5%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) 
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT ?typ ?cnt WHERE {
	SELECT ?typ (count(DISTINCT ?elem) as ?cnt) WHERE{
		?graffiti grfo:hasType ?typ ;
		grfo:hasSyleElement ?elem .
		FILTER NOT EXISTS { ?graffiti grfo:hasCarrierMedium "Hall of Fame"} .
	}
	FILTER(?cnt > 5)
}
```

[How many graffities per category Type have more than five Stilelemente and are not painted at a Hall of Fame (category Trägermedium)?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%3Ftyp+count%28DISTINCT+%3Fgraffiti%29+as+%3FcntGraffities+WHERE+%7B%0D%0A%7B%0D%0ASELECT+%3Fgraffiti+%3Ftyp+%28count%28DISTINCT+%3Felem%29+as+%3Fcnt%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasType+%3Ftyp+%3B%0D%0A++++++%09grfo%3AhasSyleElement+%3Felem+.%0D%0AFILTER+NOT+EXISTS+%7B+%3Fgraffiti+grfo%3AhasCarrierMedium+%22Hall+of+Fame%22%5E%5Exsd%3Astring%7D+.%0D%0A%7D%0D%0A%7D%0D%0AFILTER%28%3Fcnt+%3E+5%29%0D%0A%7D%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT ?typ count(DISTINCT ?graffiti) as ?cntGraffities WHERE {
	SELECT ?graffiti ?typ (count(DISTINCT ?elem) as ?cnt) WHERE{
		?graffiti grfo:hasType ?typ ;
      		grfo:hasSyleElement ?elem .
		FILTER NOT EXISTS { ?graffiti grfo:hasCarrierMedium "Hall of Fame"} .
	}
	FILTER(?cnt > 5)
}
```

```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT ?graffiti, ?cnt WHERE {
	SELECT ?graffiti (count(?graffitiCrew) as ?cnt) WHERE{
		?graffiti grfo:hasGraffitiSprayerCrew ?graffitiCrew .
	}
	FILTER(?cnt > 3)
}
GROUP BY ?graffiti
ORDER BY desc(?cnt)
```

[Count the number of graffiti per postal code with the topic _„Politik“_ in _Mannheim_](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+%28COUNT%28%3Fg%29+as+%3FnumberOfGraffiti%29+%3Fplz%0D%0AWHERE+%7B%0D%0A++%3Fg++grfo%3AhasPostalCode+%3Fplz+%3B%0D%0A++%09grfo%3AhasLocation+grfr%3AMannheim+%3B%0D%0A++%09grfo%3AhasTheme+%22Politik%22.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT (COUNT(?g) as ?numberOfGraffiti) ?plz WHERE{
	?g  grfo:hasPostalCode ?plz ;
  	grfo:hasLocation grfr:Mannheim ;
  	grfo:hasTheme "Politik".
}
```

[What is the average number of letters in the Item field for the typ “Spruch/ Konzeptaufruf”? with showing results without spaces betwenn letters](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3FitemLen%29+AS+%3Favg%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasType+%22Spruch%2FKonzeptaufruf%22%3B%0D%0A++++++%09grfo%3AhasItem+%3Fitem+.%0D%0ABIND%28replace%28%3Fitem%2C+%22+%22%2C+%22%22%29+as+%3FwithoutSpace%29%0D%0ABIND+%28strlen%28%3FwithoutSpace%29+AS+%3FitemLen%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
select (AVG(?itemLen) AS ?avg) WHERE{
	?graffiti grfo:hasType "Spruch/Konzeptaufruf";
      		  grfo:hasItem ?item .
	BIND(replace(?item, " ", "") as ?withoutSpace)
	BIND (strlen(?withoutSpace) AS ?itemLen)
}
```

[Count the number of letters for the item _"RIOT RADIO"_ without spaces?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0A%0D%0ASELECT+%3FitemLen+WHERE%0D%0A%7B%0D%0A%3Fs+grfo%3AhasItem+%22RIOT+RADIO%22%40en.%0D%0A%3Fs+grfo%3AhasItem+%3Fitem.%0D%0Abind%28replace%28%3Fitem%2C+%22+%22%2C+%22%22%29+as+%3FwithoutSpace%29%0D%0A++bind%28strlen%28%3FwithoutSpace%29+as+%3FitemLen%29.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT ?itemLen WHERE{
	?s grfo:hasItem "RIOT RADIO"@en.
	?s grfo:hasItem ?item.
	bind(replace(?item, " ", "") as ?withoutSpace)
  	bind(strlen(?withoutSpace) as ?itemLen).
}
```

[What is the average number of letters within graffiti of type “Spruch/ Konzeptaufruf” and topic “Politik”](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+%28AVG%28%3FitemLen%29+AS+%3Favg%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasType+%22Spruch%2FKonzeptaufruf%22%3B%0D%0A++++++++++%09grfo%3AhasTheme+%22Politik%22%3B%0D%0A++++++++++%09grfo%3AhasItem+%3Fitem+.%0D%0ABIND+%28strlen%28%3Fitem%29+AS+%3FitemLen%29%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+) 
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT (AVG(?itemLen) AS ?avg) WHERE{
	?graffiti grfo:hasType "Spruch/Konzeptaufruf";
	grfo:hasTheme "Politik";
	grfo:hasItem ?item .
	BIND (strlen(?item) AS ?itemLen)
}
```

[Find the graffities created by more than one sprayer crew.](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0ASELECT+%3Fgraffiti+%3Fcnt%0D%0A%7B%7B%0D%0ASELECT+%3Fgraffiti+count%28%3FgraffitiCrew%29+as+%3Fcnt+WHERE+%7B%0D%0A%09%09%3Fgraffiti+grfo%3AhasGraffitiSprayerCrew+%3FgraffitiCrew+.%0D%0A%09%09%3Fgraffiti+grfo%3AhasType+%22Piece%2FWriting%2FStyle%22.%0D%0A%09%09%3FgraffitiCrew+rdfs%3Alabel+%3FcrewName+.%0D%0A%7D%0D%0AGROUP+BY+%3Fgraffiti%0D%0A%7D%0D%0AFILTER+%28%3Fcnt+%3E+1%29%0D%0A%7D%0D%0AORDER+BY+DESC%28%3Fcnt%29%0D%0A%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT ?graffiti ?cnt
{{
SELECT ?graffiti count(?graffitiCrew) as ?cnt WHERE {
		?graffiti grfo:hasGraffitiSprayerCrew ?graffitiCrew .
		?graffiti grfo:hasType "Piece/Writing/Style".
		?graffitiCrew rdfs:label ?crewName .
}
GROUP BY ?graffiti
}
FILTER (?cnt > 1)
}
ORDER BY DESC(?cnt)
```
[What is the most frequent languages of grafitti of Type "Spruch/Konzeptaufruf"?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT++%3Flang+count%28DISTINCT+%3Fg%29+AS+%3FGrPerLang+WHERE%7B%0D%0A%09%3Fg+grfo%3AhasType+%22Spruch%2FKonzeptaufruf%22.%0D%0A%09%3Fg+grfo%3AhasLanguage+%3Flang%0D%0A%7D%0D%0AORDER+BY+DESC+%28count%28%3Fg%29%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT  ?lang count(DISTINCT ?g) AS ?GrPerLang WHERE{
	?g grfo:hasType "Spruch/Konzeptaufruf".
	?g grfo:hasLanguage ?lang
}
ORDER BY DESC (count(?g))
```
[What is the most frequent languages of grafitti of Type _"Spruch/Konzeptaufruf"_ within the time slot (1990-1999)?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfp%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fgraffiti%23%3E%0D%0APREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT++%3Flang+count%28DISTINCT+%3Fg%29+AS+%3FGrPerLang+WHERE%7B%0D%0A%09%3Fg+grfo%3AhasType+%22Spruch%2FKonzeptaufruf%22.%0D%0A%09%3Fg+grfo%3AhasLanguage+%3Flang.%0D%0A%09%3Fg+grfo%3AhasRecordingDate+%3Fdate+.%0D%0AFILTER%28%221990-01-01%22%5E%5Exsd%3Adate+%3C%3D+%3Fdate+%26%26+%3Fdate+%3C+%221999-12-31%22%5E%5Exsd%3Adate%29.%0D%0A%0D%0A%7D%0D%0AORDER+BY+DESC+%28count%28%3Fg%29%29+%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT  ?lang count(DISTINCT ?g) AS ?GrPerLang WHERE{
	?g grfo:hasType "Spruch/Konzeptaufruf".
	?g grfo:hasLanguage ?lang.
	?g grfo:hasRecordingDate ?date .
FILTER("1990-01-01"^^xsd:date <= ?date && ?date < "1999-12-31"^^xsd:date).

}
ORDER BY DESC (count(?g)) 
```

[Retrieve the number of used colors per crew?](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+DISTINCT+%3FgraffitiCrew+%3Fcolour++%28count%28%3Fcolour%29+as+%3Fcount%29+WHERE%0D%0A%7B%0D%0A%3Fgraffiti+grfo%3AhasGraffitiSprayerCrew+%3FgraffitiCrew+.%0D%0A%3FgraffitiCrew+a+grfo%3AGraffitiSprayerCrew+.%0D%0A%3Fgraffiti+grfo%3AhasColour+%3Fcolour+.%0D%0A%7D%0D%0AGROUP+BY+%3FgraffitiCrew+%3Fcolour%0D%0AORDER+BY+DESC%28%3Fcount%29%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT disntict ?graffitiCrew ?colour  (count(?colour) as ?count) WHERE
{
	?graffiti grfo:hasGraffitiSprayerCrew ?graffitiCrew .
	?graffitiCrew a grfo:GraffitiSprayerCrew .
	?graffiti grfo:hasColour ?colour .
}
GROUP BY ?graffitiCrew ?colour
ORDER BY DESC(?count)
```

[Find all sub-graffiti with comments](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=PREFIX+grfr%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fresource%2F%3E%0D%0APREFIX+grfo%3A+%3Chttps%3A%2F%2Fgraffiti.data.dice-research.org%2Fontology%2F%3E%0D%0A%0D%0ASELECT+count%28DISTINCT+*%29+WHERE%0D%0A%7B%0D%0A%3Fg+a+grfo%3AGraffiti+.%0D%0A%3Fg+grfo%3AhasType+%22Comment%22+.%0D%0A%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
```sparql
PREFIX grfr: <https://graffiti.data.dice-research.org/resource/>
PREFIX grfo: <https://graffiti.data.dice-research.org/ontology/>
SELECT count(DISTINCT *) WHERE
{
	?g a grfo:Graffiti .
	?g grfo:hasType "Comment" .
}
```
