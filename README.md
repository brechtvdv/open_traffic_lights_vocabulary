# Vocabulary for MAP/SPAT messages

This RDFS vocabulary defines some basic concepts to publish traffic lights data as Linked Data.
Note: only a small part of the MAP/SPAT standard has been given global identifiers (URIs).
Please make a Github issue for questions.

Following MAP elements are described:
* lane (departure and arrival)
* width of the lane
* connection between lanes

Following SPAT elements are described:
* signalgroup
* signalstate
* signalphase of the signalstate
* minEndtime of the signalstate
* maxEndtime of the signalstate

Example output:
```text/turtle
@prefix dcterms: <http://purl.org/dc/terms/>.
@prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>.
@prefix rdfs: <http://www.w3.org/2000/01/rdf-schema#>.
@prefix skos: <http://www.w3.org/2004/02/skos/core#>.
@prefix skos-thes: <http://purl.org/iso25964/skos-thes#>.
@prefix prov: <http://www.w3.org/ns/prov#>.
@prefix void: <http://rdfs.org/ns/void#>.
@prefix xsd: <http://www.w3.org/2001/XMLSchema#>.
@prefix geo: <http://www.opengis.net/ont/geosparql#>.
@prefix dbpedia: <http://dbpedia.org/ontology/>.
@prefix otl: <https://w3id.org/opentrafficlights#>.

# MAP topology
# _:b0 are blank nodes
_:b0_lane6 a otl:Lane;
    geo:wktLiteral "LINESTRING (51.2118379 4.3970829, 51.2111054 4.3961904)";
    dbpedia:width "100";
    dcterms:description "Volkstraat".
_:b0_connection11 a otl:Connection;
    otl:departureLane _:b0_lane6;
    otl:arrivalLane _:b0_lane11;
    otl:signalGroup <https://opentrafficlights.org/id/signalgroup/K648/6>.
_:b0_lane11 a otl:Lane;
    geo:wktLiteral "LINESTRING (51.2122440 4.3973510, 51.2126980 4.3975804)";
    dbpedia:width "100";
    dcterms:description "Nationalestraat".

# SPAT update
<https://opentrafficlights.org/id/signalgroup/K648/6> a otl:Signalgroup.

# Observation for signalgroup <https://opentrafficlights.org/id/signalgroup/K648/6>
# Its signalstate has signalphase <https://w3id.org/opentrafficlights/thesauri/signalphase/0> which means it's unavailable
<https://opentrafficlights.org/spat/K648?time=2018-10-31T14:58:23.205Z> {
    _:b1_b4077 a otl:SignalState;
    otl:signalPhase <https://w3id.org/opentrafficlights/thesauri/signalphase/0>;
    otl:minEndTime "2018-10-31T14:58:37.605Z"^^<http://www.w3.org/2001/XMLSchema#date>;
    otl:maxEndTime "2018-10-31T14:59:40.605Z"^^<http://www.w3.org/2001/XMLSchema#date>.
    <https://opentrafficlights.org/id/signalgroup/K648/6> otl:signalState _:b1_b4077.
}
<https://opentrafficlights.org/spat/K648?time=2018-10-31T14:58:23.205Z> prov:generatedAtTime "2019-02-14T17:43:54.297Z"^^xsd:date.
```
