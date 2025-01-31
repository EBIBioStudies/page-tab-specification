# All In One Example
Below you'll find an example of a basic submission that:
* Is attached to a collection named "blueprint"
* Has a root section with a single file, a files table and a single link attached to it
* Some of the attributes in the root section have name and value attributes
* Has a sections table
* Has a subsection with a links table

## TSV
```
Submission	S-IHECRE00000919.1
Title	venous blood, Monocyte
ReleaseDate	2016-06-07
RootPath	S-IHECRE00000919.1
DataSource	BLUEPRINT
AttachTo	blueprint

Study	SECT-001
Title	venous blood, Monocyte
Project	CEEHRC (McGill)
Status	Incomplete
Organism	Homo sapiens
Tissue type	venous blood
[Ontology]	UBERON
(Tissue)	Blood
Donor ID	McGill0139
Biomaterial Type	primary cells
Cell Type	Monocyte
[Ontology]	CL
Disease	Systemic Lupus Erythematosus
[Ontology]	EFO
Experiment type	Single donor

File	plates/J_Sero_plate_keys.xlsx
Description	Summary data
Type	XLSX File

Files	Description	Type
plates/J_Sero_plate_keys.xlsx	Summary data	Library File
plates/Plate01.csv	Data for Plate 01	Plate Details File

Link	IHECRE00000919.1
Type	EpiRR

Data[SECT-001]	Title	Description
DT-1	Group 1 Transcription Data	The data for zygotic transcription in mammals group 1
DT-2	Group 2 Transcription Data	The data for zygotic transcription in mammals group 2

Stranded Total RNA-Seq	SUBSECT-001	SECT-001

Links	Type	Assay type	Experiment type	Primary id
EGAD00001001282	EGA	RNA-Seq	Stranded Total RNA-Seq	EGAX00001273202
EGAD00001001283	EGA	RNA-Seq	Stranded Total RNA-Seq	EGAX00001273203
``` 

## JSON
```json
{
  "accno": "S-IHECRE00000919.1",
  "attributes": [{
    "name": "RootPath",
    "value": "S-IHECRE00000919.1"
  }, {
    "name": "Title",
    "value": "venous blood, Monocyte"
  }, {
    "name": "ReleaseDate",
    "value": "2016-06-07"
  }, {
    "name": "DataSource",
    "value": "BLUEPRINT"
  }, {
    "name": "AttachTo",
    "value": "blueprint"
  }],
  "section": {
    "accno": "SECT-001",
    "attributes": [{
      "name": "Title",
      "value": "venous blood, Monocyte"
    }, {
      "name": "Project",
      "value": "CEEHRC (McGill)"
    }, {
      "name": "Status",
      "value": "Incomplete"
    }, {
      "name": "Organism",
      "value": "Homo sapiens"
    }, {
      "name": "Tissue type",
      "value": "venous blood",
      "nmqual": [{
        "name": "Tissue",
        "value": "Blood"
      }],
      "valqual": [{
        "name": "Ontology",
        "value": "UBERON"
      }]
    }, {
      "name": "Donor ID",
      "value": "McGill0139"
    }, {
      "name": "Biomaterial Type",
      "value": "primary cells"
    }, {
      "name": "Cell Type",
      "value": "Monocyte",
      "valqual": [{
        "name": "Ontology",
        "value": "CL"
      }]
    }, {
      "name": "Disease",
      "value": "Systemic Lupus Erythematosus",
      "valqual": [{
       "name": "Ontology",
       "value": "EFO"
      }]
    }, {
      "name": "Experiment type",
      "value": "Single donor"
    }],
    "files": [{
      "path": "plates/J_Sero_plate_keys.xlsx",
      "attributes": [{
        "name": "Description",
        "value": "Summary data"
      }, {
        "name": "Type",
        "value": "XLSX File"
      }]
    }, [{
      "path": "plates/J_Sero_plate_keys.xlsx",
      "attributes": [{
        "name": "Description",
        "value": "Summary data"
      }, {
        "name": "Type",
        "value": "Library File"
      }]
    }, {
      "path": "plates/Plate01.csv",
      "attributes": [{
        "name": "Description",
        "value": "Data for Plate 01"
      }, {
        "name": "Type",
        "value": "Plate Details File"
      }]
    }]],
    "links": [{
      "url": "IHECRE00000919.1",
      "attributes": [{
        "name": "Type",
        "value": "EpiRR"
      }]
    }],
    "subsections": [{
      "accno": "SUBSECT-001",
      "links": [[{
        "url": "EGAD00001001282",
        "attributes": [{
          "name": "Type",
          "value": "EGA"
        }, {
          "name": "Assay type",
          "value": "RNA-Seq"
        }, {
          "name": "Experiment type",
          "value": "Stranded Total RNA-Seq"
        }, {
          "name": "Primary id",
          "value": "EGAX00001273202"
        }]
      }, {
        "url": "EGAD00001001283",
        "attributes": [{
          "name": "Type",
          "value": "EGA"
        }, {
          "name": "Assay type",
          "value": "RNA-Seq"
        }, {
          "name": "Experiment type",
          "value": "Stranded Total RNA-Seq"
        }, {
          "name": "Primary id",
          "value": "EGAX00001273203"
        }]
      }]],
      "type": "Stranded Total RNA-Seq"
    }, [{
      "accno": "DT-1",
      "attributes": [{
        "name": "Title",
        "value": "Group 1 Transcription Data"
      }, {
        "name": "Description",
        "value": "The data for zygotic transcription in mammals group 1"
      }],
      "type": "Data"
    }, {
      "accno": "DT-2",
      "attributes": [{
        "name": "Title",
        "value": "Group 2 Transcription Data"
      }, {
        "name": "Description",
        "value": "The data for zygotic transcription in mammals group 2"
      }],
      "type": "Data"
    }]],
    "type": "Study"
  },
  "type": "submission"
}
```
