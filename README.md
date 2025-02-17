# Défi OB1  

_Elie Arnaud, Yvan Le Bras, Oussama Chaib, Juliette Silhol, Laura Leroi, Clément Grandidier, Dorian Cazau_  

Git de l'équipe OB1 de l'Ocean Hackathon 2019 - Brest.  

## Description du défi

De plus en plus de données scientifiques sont aujourd'hui accessibles en accès ouvert. Cette mise à disposition est un premier pas essentiel vers un meilleur partage des connaissances et une réutilisation massives des données. Malheureusement, le partage du "matériel brut" ne suffit pas, et aujourd'hui plus que jamais se pose la question de la structuration de ces données. Comment faire en sorte que les données soient suffisamment bien décrites pour pouvoir être compréhensibles et réutilisées le plus largement possible ? Dans le cadre du projet "Pôle national de données de biodiversité", des actions en cours propose l'utilisation d'un standard de metadonnees, l'EML (Ecological Metadata Language), comme standard pivot d'outils et services qui faciliteraient cette structuration des données écologique et leur réutilisation. Des questionnements particuliers ont émergé concernant les données marines et ocean hackathon représente une initiative parfaite pour avancer sur certains aspects et laisser de potentiels hackers proposer d'améliorer ou/et créer des produits d'intérêt.  

**Objectifs**

En termes d'outils, nous travaillons sur le développement d'une application interactive R Shiny nommée [MetaSHARK](https://github.com/earnaud/MetaShARK). Nous aimerions développer des “modules” en R ou autre langage permettant d’automatiser les traitements de données marines hétérogènes pour par exemple parcourir des données d'écologie (séquences d'ADN ou données de présence d'espèces) et environnementales (données satellitaires ou autres données décrivant les conditions physico-chimiques du milieu) pour remplir de manière automatique et/ou assistée les champs de métadonnées pouvant l’être (étendues taxonomique, géographique et temporelle de l’étude ...).  

## Pistes envisagées
- Blockchain & Peer to Peer. Pour distribuer
  - A1 les données et/ou métadonnées (MTD)
  - A2 logiciels notamment ceux développés en B1 et B2
- Deux modules R Shiny
  - B1 "Inférence" automatique de MTD, notamment basé sur utilisation d'expression régulière (RegEx)
  - B2 "Sémantique" sur attributs (aussi nommés variables) : faire un lien entre les attributs et des ressoruces terminologiques exitantes notamment ontologies du domaine
- Récupérer des données hétérogènes proposées au Océan hackathon + extérieures avec leurs MTD et proposer 
  - C1 d'y ajouter des MTD -> structuration / qualification des MTD
  - C2 Faire remonter aux entrepôts des données d'origine les améliorations de MTD
- "Mapping" manuel de standards entre
  - D1 ISO19139 / EML / Darwin-Core / Tethys
  - Tethys
- Business Model
  - Indicateurs / métriques autour de la "complétude" des données en MTD
  - Indicateurs / métriques autour des données stockées inutilement car non rétuilisable notamment car MTD pas assez détaillées

### Gestion métadonnées
- datapackage https://github.com/frictionlessdata/datapackage-r notamment fonction dataPackage$infer 
- metadatar https://github.com/annakrystalli/metadatar 
- taxonomyCleanr (A workflow and set of functions to clean your taxonomy data using R) https://github.com/EDIorg/taxonomyCleanr 
- dataspice https://github.com/ropenscilabs/dataspice dont déjà des choses côté EML : https://github.com/ropenscilabs/dataspice/blob/master/R/eml_to_spice.R
- dataCleanR (A collection of user friendly data cleaning functions - EDIorg/dataCleanr) https://github.com/EDIorg/dataCleanr/blob/master/README.md
- taxize " The EML R package can leverage existing functions in the R package taxize to automatically generate the rank classification metadata" / rOpenSci | taxize tutorial / taxa - taxonomic classes for R
  - https://ropensci.org/tutorials/taxize_tutorial/
- ritis - Integrated Taxonomic Information Service (ITIS) R client
  - https://github.com/ropensci/ritis
- binomen - taxonomic name classes and parsing methods
  - https://github.com/ropensci/binomen

- https://github.com/ropensci/phylocomr
  - ecovolve/ph_ecovolve - interface to ecovolve executable, and a higher level interface
  - phylomatic/ph_phylomatic - interface to phylomatic executable, and a higher level interface
  - phylocom - interface to phylocom executable
  - ph_aot - higher level interface to aot
  - ph_bladj - higher level interface to bladj
  - ph_comdist/ph_comdistnt - higher level interface to comdist
  - ph_comstruct - higher level interface to comstruct
  - ph_comtrait - higher level interface to comtrait
  - ph_pd - higher level interface to Faith's phylogenetic diversity

- Données accoustiques
  - https://cran.r-project.org/web/packages/bioacoustics/bioacoustics.pdf

Helper for making maps of species occurrence data
- https://github.com/ropensci/mapr

Petit site sympa pour tester expressions régulières (merci Laura ;) )
- https://regexr.com/

### Visualization
vis_dat helps you visualise a dataframe and “get a look at the data” by displaying the variable classes in a dataframe as a plot with vis_dat, and getting a brief look into missing data patterns using vis_miss.
- https://github.com/ropensci/visdat/blob/master/README.md
Count number of points within polygons / Average value of a field for a set of points within a set of polygons .... /
- https://github.com/ropensci/lawn
Utilities / visualization / themes
- https://github.com/ropensci/landscapetools

#### Création de sites par fiche métadonnées EML
- https://github.com/ropenscilabs/emldown

### Récupération de données :
- Données du hackathon:
  - http://oceanhackathon.indigeo.fr/geocms/maps/oceanhackathon-wpjdbpbc#project
  - http://data.ifremer.fr/pdmi/portalssearch/main
  - http://donnees-campagnes.flotteoceanographique.fr/
  - https://data.shom.fr/donnees#001=eyJjIjpbLTY2MjgwNyw1ODIyOTI3XSwieiI6NiwiciI6MCwibCI6W3sidHlwZSI6IklOVEVSTkFMX0xBWUVSIiwiaWRlbnRpZmllciI6IkZEQ19HRUJDT19QWVItUE5HXzM4NTdfV01UUyIsIm9wYWNpdHkiOjEsInZpc2liaWxpdHkiOnRydWV9XX0=
  - AFB espèces et habitats -> anniebirolo[@]afbiodiversité.fr
- Génomique / Barcode of life : https://github.com/ropensci/bold/blob/master/README.md
- couches environnementales : http://www.ccafs-climate.org/data/

### Standards de métadonnées / Mapping / Spécifications
- EML (https://knb.ecoinformatics.org/#external//emlparser/docs/eml-2.1.1/index.html)
- TETHYS (Passive Accoustic Monitoring) https://tethys.sdsu.edu/
  - "Where possible, we use concepts from ISO 19115 or OpenGIS SensorML3, but our emphasis is on meeting the needs of the marine mammal community in the most user-friendly way possible. As a consequence, we deviate from these standards. In addition, there are many concepts that are not covered in these standards such as recording detection effort."
- Darwin-core https://dwc.tdwg.org/
- ISO19139
  - http://www.geosource.fr/docs/appendix/glossary/iso19139/index.html 
  - https://inspire.ec.europa.eu/id/document/tg/metadata-iso19139
- convertisseurs existants
  - https://github.com/gbif/eml-profile/blob/master/eml2iso19139.xsl
  - https://github.com/NCEAS/iso2eml
  - https://github.com/eblondel/geometa


### Ontologies et liens avec module semantics
#### Sources d'ontologies d'intérêt
- https://bioportal.bioontology.org/
- http://vocabs.lter-europe.net/edg/tbl/EnvThes.editor#http%3A%2F%2Fvocabs.lter-europe.net%2FEnvThes%2F21439
- http://semandiv.agroportal.lirmm.fr/
- http://agroportal.lirmm.fr/annotator
- https://www.rdocumentation.org/packages/AtlasRDF/versions/1.8.0/topics/getOntologyMappings

#### Annotation de données/métadonnées par ontologies :
- annotateur d'ontologies : https://www.bioontology.org/wiki/Annotator_R_Client
- Get mappings for a given class URI from an ontology other than EFO : https://www.rdocumentation.org/packages/AtlasRDF/versions/1.8.0/topics/getOntologyMappings
- ontoCAT: an R package for ontology traversal and search https://academic.oup.com/bioinformatics/article/27/17/2468/223268

### Notion de liens avec provenance via ontologie :
- ontologie provenance : https://www.w3.org/TR/prov-o/ -> voir lien avec notion de provenance dans EML

