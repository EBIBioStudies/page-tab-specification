# File List Example
When a submission need to reference a lot of files, these can be referenced through a external file using the
 **File List** section attribute.

Below, you'll find an example of a submission that uses the **File List** mechanism.

## TSV

**Submission**

```
Submission	S-BIAD765
Title	A Submission With A Lot Of Images
AttachTo	BioImages

Study	SECT-001
Title	Root Section
File List	Experiment.tsv
```

**File List (Experiment.tsv)**
```
Files	Plate	Well
Plate1/A01/cell01.tiff	Plate 1	A01
Plate1/A02/cell02.tiff	Plate 1	A02
Plate2/B01/cell03.tiff	Plate 2	B01
Plate3/C01/cell05.tiff	Plate 3	C01
```

## JSON

**Submission**

```json
{
  "accno": "S-BIAD765",
  "attributes": [{
    "name": "Title",
    "value": "A Submission With A Lot Of Images"
  }, {
     "name": "AttachTo",
     "value": "BioImages"
  }],
  "section": {
    "accno": "SECT-001",
    "attributes": [{
      "name": "Title",
      "value": "Root Section"
    }, {
       "name": "File List",
       "value": "Experiment.json"
    }],
    "type": "Study"
  }
} 
```

**File List (Experiment.json)**
```json
[{
  "path": "Plate1/A01/cell01.tiff",
  "attributes": [{
    "name": "Plate",
    "value": "Plate 1"
  }, {
     "name": "Well",
     "value": "A01"
  }]
}, {
  "path": "Plate1/A02/cell02.tiff",
  "attributes": [{
    "name": "Plate",
    "value": "Plate 2"
  }, {
    "name": "Well",
    "value": "A02"
  }]
}, {
  "path": "Plate2/B01/cell03.tiff",
  "attributes": [{
    "name": "Plate",
    "value": "Plate 2"
  }, {
    "name": "Well",
    "value": "B01"
  }]
}, {
  "path": "Plate3/C01/cell05.tiff",
  "attributes": [{
    "name": "Plate",
    "value": "Plate 3"
  }, {
   "name": "Well",
   "value": "C01"
  }]
}]
```
