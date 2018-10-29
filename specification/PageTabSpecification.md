## Page Tab Elements
Page tab has several elements that allow to represent a submission:
* Attribute
* Submission
* Section
* Subsection
* Sections Table
* Files
* Links

### Attribute
An attribute is the most basic element in page tab because any element defined in a submission, may have attributes. An
attribute has the following characteristics:
* It's defined by a name / value combination
* It may be used as a reference to another attribute
* Its name may have additional details. These are called _Name Attributes_
* Its value may have additional details. These are called _Value Attributes_

#### Syntax
```
Name	The Name
Value	The Value
(Name Attribute)	The name attribute value
[Value Attribute]	The value attribute value
```

#### Examples

##### Simple Attribute

**TSV**
```
Study Type	RNA-seq of non coding RNA
```

<details><summary>JSON</summary>
<p>

```json
{
  "attributes": [{
    "name": "Study Type",
    "value": "RNA-seq of non coding RNA"
  }]
}
```
</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<attributes>
  <attribute>
    <name>Study Type</name>
    <value>RNA-seq of non coding RNA</value>
  </attribute>
</attributes>
```
</p>
</details>


##### Detailed Attribute
**TSV**
```
Study Type	RNA-seq of non coding RNA
[Ontology]	EFO
(Seq Type)	RNA
```

<details><summary>JSON</summary>
<p>

```json
{
  "attributes": [{
    "name": "Study Type",
    "value": "RNA-seq of non coding RNA",
    "nmqual": [{
      "name": "Seq Type",
      "value": "RNA"
    }],
    "valqual": [{
      "name": "Ontlogy",
      "value": "EFO"
    }]
  }]
}
```
</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<attributes>
  <attribute>
    <name>Study Type</name>
    <value>RNA-seq of non coding RNA</value>
    <nmqual>
      <name>Seq Type</name>
      <value>RNA</value>
    </nmqual>
    <valqual>
      <name>Ontology</name>
      <value>EFO</value>
</valqual>
  </attribute>
</attributes>
```
</p>
</details>

##### Reference Attribute
For this example, let's assume there's already an attribute with value "Org1"

**TSV**
```
<affiliation>	Org1
```

<details><summary>JSON</summary>
<p>

```json
{
  "attributes": [{
    "name": "affiliation",
    "value": "Org1",
    "isReference": "true"
  }]
}
```
</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<attributes>
  <attribute reference="true">
    <name>affiliation</name>
    <value>Org1</value>
  </attribute>
</attributes>
```
</p>
</details>

### Submission
Root element of the submission. A submission element is created using the reserved word _Submission_. It's mandatory to have this element.

#### Syntax
```
Submission	AccNo
<Attributes>
```

#### Examples
**TSV**
```
Submission	E-MTAB-2950
Title	The first wave of the zygotic transcription is highly promiscuous
ReleaseDate	2018-09-28
RootPath	E-MTAB/E-MTAB-2950
```

<details><summary>JSON</summary>
<p>

```json
{
  "accno": "E-MTAB-2950",
  "attributes": [{
    "name": "Title",
    "value": "The first wave of the zygotic transcription is highly promiscuous"
  }, {
    "name": "ReleaseDate",
    "value": "2018-09-28"
  }, {
    "name": "RootPath",
    "value": "E-MTAB/E-MTAB-2950"
  }],
  "type": "submission"
}

```

</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<submission acc="E-MTAB-2950">
  <attributes>
    <attribute>
      <name>Title</name>
      <value>The first wave of the zygotic transcription is highly promiscuous</value>
    </attribute>
    <attribute>
      <name>ReleaseDate</name>
      <value>2018-09-28</value>
    </attribute>
    <attribute>
      <name>RootPath</name>
      <value>E-MTAB/E-MTAB-2950</value>
    </attribute>
  </attributes>
</submission>
```

</p>
</details>

### Section
A section is a part of the submission used to group other elements like files, links or even other sections. There're
some rules related to sections:
1. Sections can be of any type so, there's no reserved word for them
2. The first section of a submission definition will be the _Root Section_
3. Every submission should have at least a root section

#### Syntax
```
Type	AccNo
<Attributes>
```

#### Examples
**TSV**
```
Study	s-E-MTAB-2950
Title	The first wave of the zygotic transcription is highly promiscuous
Description	Initiation of zygotic transcription in mammals is poorly understood
```

<details><summary>JSON</summary>
<p>

```json
{
  ...

  "section": {
    "accno": "s-E-MTAB-2950",
    "attributes": [{
      "name": "Title",
      "value": "The first wave of the zygotic transcription is highly promiscuous"
    }, {
      "name": "Description",
      "value": "Initiation of zygotic transcription in mammals is poorly understood"
    }],
    "type": "Study"
  },

  ...
}
```

</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<submission>

  ...

  <section acc="s-E-MTAB-2950" type="Study">
    <attributes>
        <attribute>
          <name>Title</name>
          <value>The first wave of the zygotic transcription is highly promiscuous</value>
        </attribute>
        <attribute>
          <name>Description</name>
          <value>Initiation of zygotic transcription in mammals is poorly understood</value>
        </attribute>
      </attributes>
  </section>

  ...

</submission>
```

</p>
</details>

### Subsection
A subsection is a section contained inside another section. Any section may have several subsections.

#### Syntax
```
Type	AccNo	ParentAccNo
<Attributes>
```

#### Examples
**TSV**
```
Data	DT-1	s-E-MTAB-2950
Title	Transcription Data
Description	The data for zygotic transcription in mammals
```

<details><summary>JSON</summary>
<p>

```json
{
  ...

  "section": {
    "accno": "s-E-MTAB-2950",

    ...

    "subsections": [{
      "accno": "DT-1",
      "attributes": [{
        "name": "Title",
        "value": "Transcription Data"
      }, {
        "name": "Description",
        "value": "The data for zygotic transcription in mammals"
      }],
      "type": "Data"
    }],

   ...

  }

  ...
}
```

</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<submission>

  ...

  <section acc="s-E-MTAB-2950" type="Study">

    ...

    <subsections>
      <section acc="DT-1" type="Data">
        <attributes>
          <attribute>
            <name>Title</name>
            <value>Transcription Data</value>
          </attribute>
          <attribute>
            <name>Description</name>
            <value>The data for zygotic transcription in mammals</value>
          </attribute>
        </attributes>
      </section>
    </subsections>

  ...

  </section>

  ...

</submission>
```

</p>
</details>

### Sections Table
A sections table is an element that allows to group several sections that will be displayed as a table by the UI. Rules:
* You can place as many section as you want in a sections table
* The sections in the table can NOT contain files, links nor subsections
* All the sections in the table will have the same type and attributes
* The parent accNo is optional
* If a parent accNo is provided, all the sections in the table will become subsections of that section

#### Syntax
```
Type[Parent AccNo (optional)]	Attr1	Atrr2	AttrN
AccNo1	Attr1 Value	Attr2 Value	AttrN Value
AccNo2	Attr1 Value	Attr2 Value	AttrN Value
```

#### Examples
**TSV**
```
Data[s-E-MTAB-2950]	Title	Description
DT-1	Group 1 Transcription Data	The data for zygotic transcription in mammals group 1
DT-2	Group 2 Transcription Data	The data for zygotic transcription in mammals group 2
```

<details><summary>JSON</summary>
<p>

```json
{
  ...

  "section": {
    "accno": "s-E-MTAB-2950",

    ...

    "subsections": [[{
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

   ...

  }

  ...
}
```

</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<submission>

  ...

  <section acc="s-E-MTAB-2950" type="Study">

    ...

    <subsections>
      <table>
        <section acc="DT-1" type="Data">
          <attributes>
            <attribute>
              <name>Title</name>
              <value>Group 1 Transcription Data</value>
            </attribute>
            <attribute>
              <name>Description</name>
              <value>The data for zygotic transcription in mammals group 1</value>
            </attribute>
          </attributes>
        </section>
        <section acc="DT-2" type="Data">
          <attributes>
            <attribute>
              <name>Title</name>
              <value>Group 2 Transcription Data</value>
            </attribute>
            <attribute>
              <name>Description</name>
              <value>The data for zygotic transcription in mammals group 2</value>
            </attribute>
          </attributes>
        </section>
      </table>
    </subsections>

  ...

  </section>

  ...

</submission>
```

</p>
</details>

### Files
This element represents a file that is attached to a submission section. Whenever a file is defined, it'll be attached
to the immediately previously defined section or subsection. Files can be represented in two ways: single file or files
table.

#### Single File
Represents a single file attached to a section or subsection. The reserved word _File_ is used to define a single file.

##### Syntax
```
File	Path
<Attributes>
```

#### Examples
**TSV**
```
File	plates/J_Sero_plate_keys.xlsx
Description	Summary data
Type	XLSX File
```

<details><summary>JSON</summary>
<p>

```json
{
  ...

  "section": {

    ...

    "files": [{
      "path": "plates/J_Sero_plate_keys.xlsx",
      "attributes": [{
        "name": "Description",
        "value": "Summary data"
      }, {
        "name": "Type",
        "value": "XLSX File"
      }]
    }]

    ...

  },

  ...
}
```

</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<section acc="s-E-MTAB-2950" type="Study">
  ...

  <files>
    <file>
      <path>plates/J_Sero_plate_keys.xlsx</path>
      <attributes>
        <attribute>
          <name>Description</name>
          <value>Summary data</value>
        </attribute>
        <attribute>
          <name>Type</name>
          <value>XLSX File</value>
        </attribute>
      </attributes>
    </file>
  </files>

  ...

</section>
```

</p>
</details>

#### Files Table
Represents a group of files attached to a section or subsection. The reserved word _Files_ is used to define a files table

##### Syntax
```
Files	Attr1	Attr2	AttrN
File1 Path	Attr1 Value	Attr2 Value	AttrN Value
File2 Path	Attr1 Value	Attr2 Value	AttrN Value
File3 Path	Attr1 Value	Attr2 Value	AttrN Value
```

##### Examples
**TSV**
```
Files	Description	Type
plates/J_Sero_plate_keys.xlsx	Summary data	Library File
plates/Plate01.csv	Data for Plate 01	Plate Details File
```

<details><summary>JSON</summary>
<p>

```json
{
  ...

  "section": {

    ...

    "files": [[{
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
    }]]

    ...

  },

  ...
}
```

</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<section acc="s-E-MTAB-2950" type="Study">
  ...

  <files>
    <table>
      <file>
        <path>plates/J_Sero_plate_keys.xlsx</path>
        <attributes>
          <attribute>
            <name>Description</name>
            <value>Summary data</value>
          </attribute>
          <attribute>
            <name>Type</name>
            <value>Library File</value>
          </attribute>
        </attributes>
      </file>
      <file>
        <path>plates/Plate01.csv</path>
        <attributes>
          <attribute>
            <name>Description</name>
            <value>Data for Plate 01</value>
          </attribute>
          <attribute>
            <name>Type</name>
            <value>Plate Details File</value>
          </attribute>
        </attributes>
      </file>
    </table>
  </files>

  ...

</section>
```

</p>
</details>

### Links
Element used to represent links that are related to a submission section. A link doesn't necessarily means a web page
but it can also relate to other elements like genes, expressions, FTP locations, etc.

Whenever a link is defined, it'll be attached to the immediately previously defined section or subsection. Links can be
represented in two ways: single link or links table.

#### Single Link
Represents a single link related to a section or subsection. The reserved word _Link_ is used to define a single link.

##### Syntax
```
Link	URL
<Attributes>
```

#### Examples
**TSV**
```
Link	ftp://ftp.biostudies.ebi.ac.uk/pub/S-BSMS/S-BSMS0-99/S-BSMS6/raw_data
Type	Raw data
```

<details><summary>JSON</summary>
<p>

```json
{
  ...

  "section": {

    ...

    "links": [{
      "url": "ftp://ftp.biostudies.ebi.ac.uk/pub/S-BSMS/S-BSMS0-99/S-BSMS6/raw_data",
      "attributes": [{
        "name": "Type",
        "value": "Raw data"
      }]
    }]

    ...

  },

  ...
}
```

</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<section acc="s-E-MTAB-2950" type="Study">
  ...

  <links>
    <link>
      <url>ftp://ftp.biostudies.ebi.ac.uk/pub/S-BSMS/S-BSMS0-99/S-BSMS6/raw_data</url>
      <attributes>
        <attribute>
          <name>Type</name>
          <value>Raw data</value>
        </attribute>
      </attributes>
    </link>
  </links>

  ...

</section>
```

</p>
</details>

#### Links Table
Represents a group of links attached to a section or subsection. The reserved word _Links_ is used to define a links
table

##### Syntax
```
Links	Attr1	Attr2	AttrN
Link1 Url	Attr1 Value	Attr2 Value	AttrN Value
Link2 Url	Attr1 Value	Attr2 Value	AttrN Value
Link3 Url	Attr1 Value	Attr2 Value	AttrN Value
```

##### Examples
**TSV**
```
Links	Description	Type
ERP007058	ENA Project	ENA
ERR632210-ERR632217	ENA Runs	ENA
```

<details><summary>JSON</summary>
<p>

```json
{
  ...

  "section": {

    ...

    "links": [[{
      "url": "ERP007058",
      "attributes": [{
        "name": "Description",
        "value": "ENA Project"
      }, {
        "name": "Type",
        "value": "ENA"
      }]
    }, {
      "url": "ERR632210",
      "attributes": [{
        "name": "Description",
        "value": "ENA Runs"
      }, {
        "name": "Type",
        "value": "ENA"
      }]
    }]]

    ...

  },

  ...
}
```

</p>
</details>

<details><summary>XML</summary>
<p>

```xml
<section acc="s-E-MTAB-2950" type="Study">
  ...

  <links>
    <table>
      <link>
        <url>ERP007058</url>
        <attributes>
          <attribute>
            <name>Description</name>
            <value>ENA Project</value>
          </attribute>
          <attribute>
            <name>Type</name>
            <value>ENA</value>
          </attribute>
        </attributes>
      </link>
      <link>
        <url>ERR632210</url>
        <attributes>
          <attribute>
            <name>Description</name>
            <value>ENA Runs</value>
          </attribute>
          <attribute>
            <name>Type</name>
            <value>ENA</value>
          </attribute>
        </attributes>
      </link>
    </table>
  </links>

  ...

</section>
```

</p>
</details>
