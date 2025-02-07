# ucsb-izc-config
[![SWH](https://archive.softwareheritage.org/badge/origin/https://github.com/seltmann/elton-config-for-gbif-bees/)](https://archive.softwareheritage.org/browse/origin/?origin_url=https://github.com/seltmann/elton-config-for-gbif-bees)

Prototype for re-usable globi config see https://github.com/Big-Bee-Network/bif/issues/11 .

This prototype was created using:

```
cat interaction_types_mapping_custom.csv\
 | preston track 
 ```
 
 Then add hash to globi.json file such as hash://sha256/f2b391961c36c4321fa6697e9a8ecdae8d2e86e928f03cf48b5fff1be7fbe96d
 
cat globi.json\
 | preston track

```
Use resulting hash in the configuration: hash://sha256/d3c2a1e6d3d021ce740ab428fccecfba237780bfcf794ec79bf7f9c0d7371a05

Register with software heritage library: https://archive.softwareheritage.org/save/

where globi.json was configured to point to the mapping by their content id. 

Example usage:

```
# track UCSB IZC dataset via their GBIF registration endpoint
preston track "https://api.gbif.org/v1/dataset/d6097f75-f99e-4c2a-b8a5-b0fc213ecbd0"\
 | elton stream\
 --data-dir data\
 --config hash://sha256/d3c2a1e6d3d021ce740ab428fccecfba237780bfcf794ec79bf7f9c0d7371a05\
 --remote https://softwareheritage.org\
 | head -2\
 | mlr --itsvlite --oxtab cat
```

to print the header and the first interaction record, resulting in:

```
argumentTypeId                         https://en.wiktionary.org/wiki/support
sourceOccurrenceId                     4a98a813-85bc-41fc-bca4-0c9937ba6966
sourceCatalogNumber                    UCSB-IZC 00000304
sourceCollectionCode                   IZC
sourceCollectionId                     b03a3f0c-bfa5-4e02-b5d3-56ff38626302
sourceInstitutionCode                  UCSB
sourceTaxonId                          82680
sourceTaxonName                        Hemiptera
sourceTaxonRank                        
sourceTaxonPathIds                     
sourceTaxonPath                        Animalia | Arthropoda | Insecta
sourceTaxonPathNames                   kingdom | phylum | class
sourceBodyPartId                       
sourceBodyPartName                     
sourceLifeStageId                      
sourceLifeStageName                    
sourceSexId                            
sourceSexName                          
interactionTypeId                      http://purl.obolibrary.org/obo/RO_0002437
interactionTypeName                    interactsWith
targetOccurrenceId                     
targetCatalogNumber                    
targetCollectionCode                   
targetCollectionId                     
targetInstitutionCode                  
targetTaxonId                          
targetTaxonName                        Calandrinia menziesii
targetTaxonRank                        
targetTaxonPathIds                     
targetTaxonPath                        
targetTaxonPathNames                   
targetBodyPartId                       
targetBodyPartName                     
targetLifeStageId                      
targetLifeStageName                    
targetSexId                            
targetSexName                          
basisOfRecordId                        
basisOfRecordName                      PreservedSpecimen
http://rs.tdwg.org/dwc/terms/eventDate 2017-03-17T00:00:00Z
decimalLatitude                        34.4095
decimalLongitude                       -119.8491
localityId                             
localityName                           UCSB Campus Lagoon Island
referenceDoi                           
referenceUrl                           https://ecdysis.org/collections/individual/index.php?occid=826935
referenceCitation                      UCSB-IZC 00000304 https://ecdysis.org/collections/individual/index.php?occid=826935
namespace                              local
citation                               University of California Santa Barbara Invertebrate Zoology Collection. 2025-02-03. Ecdysis Portal - 00efd88c-9458-4860-acfd-eaa043f77b7c.
archiveURI                             hash://sha256/14289a70968588a29f8e566053c4509e0784bded38b6ab7172569ac7ceb7cae7
lastSeenAt                             2025-02-07T01:05:33.554Z
contentHash                            
eltonVersion                           0.14.3-SNAPSHOT
```


