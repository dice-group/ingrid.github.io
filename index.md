## INGRID-KG
Graffiti ist ein urbanes Phänomen, das zunehmend auch das Interesse der Wissenschaften auf sich zieht. Für eine systematische Erforschung fehlten bisher geeignete Datenkorpora. Das „Informationssystem Graffiti in Deutschland“ (INGRID) schließt diese Lücke: Graffiti-Bildbestände, die dem Projekt für die ausschließlich wissenschaftliche Nutzung zur Verfügung gestellt wurden, werden digitalisiert, annotiert und der wissenschaftlichen Forschung zugänglich gemacht. Der Aufbau des Informationssystems INGRID wurde von der Deutschen Forschungsgemeinschaft gefördert (01.04.2016–30.06.2019). Die zweite Projektphase, die ebenfalls von der Deutschen Forschungsgemeinschaft gefördert wird, ist zum 01.07.2020 gestartet.

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

