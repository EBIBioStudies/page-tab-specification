# Page Tab
Page tab is an specification language used to describe a submission in BioStudies. Page tab can be used in three formats:
* TSV (Tab separated)
* XML
* JSON

In order to define a submission, these rules must be followed:
1. Always there must be a *Submission* element
2. The first *Section* after the *Submission* element will be the root section
3. *Files*/*Links* will be assigned to the immediately previous section
4. Any element may have attributes but it's not mandatory
5. Any element different than *Submission*, *Files* or *Links* will be threaded as a section

Please refer to the resources below to find more information.
* [Page Tab Specification](specification/PageTabSpecification.md)
* [All In One Example](examples/AllInOneExample.md)
* [File List Example](examples/FileListExample.md)
