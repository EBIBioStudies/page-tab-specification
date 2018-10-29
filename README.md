# Page Tab
Page tab is an specification language used to describe a submission in BioStudies. Page tab can be used in three formats:
* TSV (Tab separated)
* XML
* JSON

In order to define a submission, these rules must be followed:
1. Always there must be a _Submission_ element
2. The first _Section_ after the _Submission_ element will be the root section
3. _Files_/_Links_ will be assigned to the immediately previous section
4. Any element may have attributes but it's not mandatory
5. Any element different than _Submission_, _Files_ or _Links_ will be threaded as a section

## Elements
Page tab has several elements that allow to represent a submission:
* Attribute
* Submission
* Section
* Subsection
* Sections Table
* Files
* Links

Please refer to the resources below to find more information.
* [Page Tab Elements Specification](specification/PageTabElementsSpecification.md)
* [All In One Example](examples/AllInOneExample.md)
