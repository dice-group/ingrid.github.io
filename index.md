## INGRID-KG
Graffiti ist ein urbanes Phänomen, das zunehmend auch das Interesse der Wissenschaften auf sich zieht. Für eine systematische Erforschung fehlten bisher geeignete Datenkorpora. Das „Informationssystem Graffiti in Deutschland“ (INGRID) schließt diese Lücke: Graffiti-Bildbestände, die dem Projekt für die ausschließlich wissenschaftliche Nutzung zur Verfügung gestellt wurden, werden digitalisiert, annotiert und der wissenschaftlichen Forschung zugänglich gemacht. Der Aufbau des Informationssystems INGRID wurde von der Deutschen Forschungsgemeinschaft gefördert (01.04.2016–30.06.2019). Die zweite Projektphase, die ebenfalls von der Deutschen Forschungsgemeinschaft gefördert wird, ist zum 01.07.2020 gestartet.

### We list some results we rtirieved from INGRID Sarql [endpoint](https://graffiti.data.dice-research.org/sparql/) to explore our INGRID-KG

The [number of triples](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+distinct+%3FConcept+where+%7B%5B%5D+a+%3FConcept%7D+LIMIT+100&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)
can be this query rtirieved using this query 

```
select count(*)
where
{
    ?s ?p ?o .
}
```
The [number of resources](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+count%28distinct%28%3Fs%29%29%0D%0Awhere%0D%0A%7B%0D%0A%3Fs+%3Fp+%3Fo+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

can be this query rtirieved using this query 

```
select count(distinct(?s))
where
{
?s ?p ?o .
}

```
The [numper of properties](https://graffiti.data.dice-research.org/sparql/?default-graph-uri=&query=select+count%28distinct%28%3Fp%29%29%0D%0Awhere%0D%0A%7B%0D%0A%3Fs+%3Fp+%3Fo+.%0D%0A%7D%0D%0A&format=text%2Fhtml&timeout=0&debug=on&run=+Run+Query+)

can be this query rtirieved using this query 

```
select count(distinct(?p))
where
{
?s ?p ?o .
}


```
