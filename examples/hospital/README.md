# Princeton–Plainsboro Teaching Hospital (PPTH)

The  Princeton–Plainsboro Teaching Hospital (PPTH) has a strict policy to prevent the diffusion of viral diseases inside the  buildings.
Doctors and nurses are equiped with a Smart Identification Tag (SIT).
Such a tag, besides displaing information abount the hospital operator, integrates a small Beacon that emits Bluetooth Low Energy signals.
Rooms, corridors and stairs are provided with antennas that, exploiting the signals sent by the SITs, allows for identification the positions of people inside the hospital.
Each antenna is responsible for triggering localization event whenever a person is in a room.
Such information is the processed to emit presence events whenever two or more people are in the same room.
An example of such presence events, easily represented with a property graph, is depicted in the figure below.

MISSING FIGURE

Each antenna expoits a private hospital Wi-Fi network to push such event into the Kafka Hospital Deployment (KOD).
As normally happens in hospitals, patients are tested for diseases.
Such tests are recorded into the KOD as disease test events.
An example of such an event is depicted in the figure below.

MISSING FIGURE

In order to reduce the spread of viral diseases throunght hospotal operators, Lisa, the hospital's head administrator wants to exploit the data available to detect possible infection across the hospital.
Indeed, there are diseases that can be easily trasmitted from pationt to doctors and nurses.

## Lisa's goal
The main goal is to indentify hospital operators that, in the last 24 hours, have been in the same room with a patient that tested positive for a specific disease.
Such operators are going to be tested for the desease.
Moreover, due to the high transmissibility of the disease, also the collegues that have been in contact with the potentially infected hospital operator have to be tested for the desease.
Lisa requires such information to be computed in real time, as soon as the data for the computation is available.

MISSING REQUIREMENTS:
- control output
- costs reduction that forces recuse of exinting infrastructure
- others?

## Solution design

The hospital administration delegates the realization of a solution able to archive such a goal to the Hospital Development Team.

Eric, the Lead Data Scientist, loaded a bunch of events into a Neo4j instance, obtaing the propery graph depicted in the figure below.

MISSING FIGURE

Eric, with the help of Dr. House that acts as domain experts, designed a Cypher query that retrieves the people to be tested for diseases.
Such a query is reported below.

MISSING QUERY

However, the hospital admin want to retrieve such information in real time, as soon as the data for computing the is available. 
Eric is far for designing a system that can satisty Lisa's goal.
However, he carefully listed the requirements that such a system should satisfy.
Eric tried to generalize the requirements, abracting domain specific aspects:

- Timeliness. Avoid data retention.
- Ease of specification. Declarative and intuitive formulation of the query.
- Reusability: Cypher queries must be compatible with seraph. 
- Generalization and specialization. The language should allow a sufficient level of generality so that it can be automatically applied for different data schemas, while allowing specialization on any given domain.

Moreover, the system should provide:
- Precise control on data ingestion from the event stream. (windows)
- Precise control on evaluation time instant.
- Precise control on output processing and emitting phase.

## Seraph (system, engine, language??)

The analysis of such requirements guided the design of Seraph.
The picture below depicts the architecture of Seraph.

Seraph is composed of several components:
- to be described??
- or we just have to focus on the language?

The Seraph language is provided with intuitive operators to control such settings.
In the remaining of this section we illunstrate how the seraph system can be used to sullfill the requirement of the hospital administration.

CONTINUO CON L'ESEMPIO VERO

## Aknowledgements
I really enjoyed the Dr. House TV series.
This use case is somehow inspired from such a TV series, and the names of the
characters in the use case are not random, they are taken from the original
TV series and in particular from the episode A Pox on Our House (Episode 7 
Season 7).

