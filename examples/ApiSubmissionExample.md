# API Submission Example

You can follow these steps to make a submission using the BioStudies API

## Get An Authorization Token
To use the BioStudies API you'll need to get an authorization token using your credentials:

```
curl --location 'https://www.ebi.ac.uk/biostudies/submissions/api/auth/login' \
--header 'Content-Type: application/json' \
--data-raw '{
    "login": "<E-mail registered in BioStudies>",
    "password": "<Password>"
}'
```
The value received in the `sessid` field of the response is your **Authentication Token**

## Upload Files
You can upload files using the BioStudies Submission Tool, FTP or Aspera as described in this
[help page](https://www.ebi.ac.uk/biostudies/submissions/help). In case you need to upload the files programatically,
you can use the correspoding API as follows:

```
curl --location 'https://www.ebi.ac.uk/biostudies/submissions/api/files/user/' \
--header 'X-SESSION-TOKEN: <authentication token>' \
--form 'files=@"<path to your file>"'
```

## Submit
Once you have the authentication token and files in place, it's time to submit:
```
curl --location 'https://www.ebi.ac.uk/biostudies/submissions/api/submissions/async/direct' \
--header 'X-SESSION-TOKEN: <authentication token>' \
--form 'submission=@"<path to your submission file>"'
```
The submission file should contain a valid page tab describing your study. Please refer to the
[PageTab Specification](https://ebibiostudies.github.io/page-tab-specification/) for more information.
