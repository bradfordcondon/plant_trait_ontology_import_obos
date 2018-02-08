```
import: http://purl.obolibrary.org/obo/to/imports/chebi_import.owl
import: http://purl.obolibrary.org/obo/to/imports/go_import.owl
import: http://purl.obolibrary.org/obo/to/imports/pato_import.owl
import: http://purl.obolibrary.org/obo/to/imports/peco_import.owl
import: http://purl.obolibrary.org/obo/to/imports/ro_import.owl
```

The plant trait ontology uses 5 subontologies:

* CHEBI
* GO
* PATO
* PECO
* RO

I used the ROBOT ontology converter to convert these subontologies from OWL to OBO.


```
mkdir source_obo
mkdir source_owl

curl https://raw.githubusercontent.com/Planteome/plant-trait-ontology/master/to.obo > source_obo/pto.obo
curl https://raw.githubusercontent.com/Planteome/plant-trait-ontology/master/imports/go_import.owl > go_subset.owl
curl https://raw.githubusercontent.com/Planteome/plant-trait-ontology/master/imports/pato_import.owl > pato_subset.owl
curl https://raw.githubusercontent.com/Planteome/plant-trait-ontology/master/imports/peco_import.owl > peco_subset.owl
curl https://raw.githubusercontent.com/Planteome/plant-trait-ontology/master/imports/ro_import.owl > ro_subset.owl
curl https://raw.githubusercontent.com/Planteome/plant-trait-ontology/master/imports/chebi_import.owl > chebi_subset.owl

robot convert --input ro_subset.owl --output ro_subset.obo
robot convert --input peco_subset.owl --output peco_subset.obo
robot convert --input pato_subset.owl --output pato_subset.obo
robot convert --input go_subset.owl --output go_subset.obo
robot convert --input chebi_subset.owl --output chebi_subset.obo


```

warnings: ro several terms had masking errors:

```
ERROR MASKING ERROR «the axiom is not translated : DisjointClasses(<http://purl.obolibrary.org/obo/BFO_0000002> ObjectSomeValuesFrom(<http://purl.obolibrary.org/obo/BFO_0000050> <http://purl.obolibrary.org/obo/BFO_0000003>))»
```