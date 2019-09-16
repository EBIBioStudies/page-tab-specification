# File List Example
When a submission need to reference a lot of files, these can be referenced through a external file using the
 **File List** section attribute.
 
The referenced file should contain a valid page tab file list and must match the submissions format i.e. you can't send
a submission using *TSV* format and reference a file list in *JSON* format.

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

## XML

**Submission**

```xml
<submission accno="S-BIAD765">
  <attributes>
    <attribute>
      <name>Title</name>
      <value>A Submission With A Lot Of Images</value>
    </attribute>
    <attribute>
      <name>AttachTo</name>
      <value>BioImages</value>
    </attribute>
  </attributes>
  <section accno="SECT-001" type="Study">
    <attributes>
      <attribute>
        <name>Title</name>
        <value>Root Section</value>
      </attribute>
      <attribute>
        <name>File List</name>
        <value>Experiment.xml</value>
      </attribute>
    </attributes>
  </section>
</submission>
```

**File List (Experiment.xml)**
```xml
<files>
  <file>
    <path>Plate1/A01/cell01.tiff</path>
    <attributes>
      <attribute>
        <name>Plate</name>
        <value>Plate 1</value>
      </attribute>
      <attribute>
        <name>Well</name>
        <value>A01</value>
      </attribute>
    </attributes>
  </file>
  <file>
    <path>Plate1/A02/cell02.tiff</path>
    <attributes>
      <attribute>
        <name>Plate</name>
        <value>Plate 1</value>
      </attribute>
      <attribute>
        <name>Well</name>
        <value>A02</value>
      </attribute>
    </attributes>
  </file>
  <file>
    <path>Plate2/B01/cell03.tiff</path>
    <attributes>
      <attribute>
        <name>Plate</name>
        <value>Plate 2</value>
      </attribute>
      <attribute>
        <name>Well</name>
        <value>B01</value>
      </attribute>
    </attributes>
  </file>
  <file>
    <path>Plate3/C01/cell05.tiff</path>
    <attributes>
      <attribute>
        <name>Plate</name>
        <value>Plate 3</value>
      </attribute>
      <attribute>
        <name>Well</name>
        <value>C01</value>
      </attribute>
    </attributes>
  </file>
</files>
```
