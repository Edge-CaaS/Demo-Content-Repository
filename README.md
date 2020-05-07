# Edge CaaS Demo Content Repository


https://developer.ibm.com/edge/caas


- CaaS provides a set of microservices for reading and caching the content from repository
- it uses memory cache for very fast response times
- attachments are uploaded to Cloud Object Storage
- CaaS provides documents search and filter services
- more info can be found here: https://developer.ibm.com/edge/caas


## Content Repository

- content have to respect a set of rules and conventions
- content is organized in:
  - catalogs = branches (e.g. preview, staging, live)
  - documents = folders inside each branch (e.g. explorer-cloud en)
  - public attachments = folders starting with underscore (e.g. _files, _attachments)
  - private attachments = folders starting with two underscores (e.g. __files, __quiz)
  - metadata = document.json file in the document folder or documents.json file in the branch root folder
- content can be maintained using GitHub UI or any tool available on your laptop
- avoid illegal characters in Windows file names: 
  - leading and trailing spaces
  - `/ \ | < > ? * % : " ^`


## Catalogs

- a catalog is a collection of documents
- a catalog is linked to one branch from repository (e.g. preview, staging, live)
- catalog metadata is defined in the file catalog.json
- catalog can keep info about the documents, defined at the catalog level, in the field documentsInfo


## Documents

- are defined as folders in a branch
- folder naming convention is: documentid language (e.g. blockchain-fundamentals en, explorer-cloud ar, explorer-cloud en)
- a document contains metadata, content and attachments
- metadata is defined in document.json file
- public attachments are defined in any folder starting with underscore (e.g. _files, _attachments)
- private attachments are defined in any folder starting with two underscores (e.g. __files, __quiz)
- files starting with dot (.) are ignored
- any other file is considered part of the document contents


## Attachments

- folders starting with _ (underscore) are considered public attachments folders
- all files found in the public attachments folders are uploaded to Cloud Object Storage
- The uploaded files path will be:
  - Catalog attachments: https://developer.ibm.com/caas-storage/{gitorg}/{gitrepo}/{gitbranch}/{attachmentsfolder}/{filename}
  - Document attachments: https://developer.ibm.com/caas-storage/{gitorg}/{gitrepo}/{gitbranch}/{documentid}/{lang}/{attachmentsfolder}/{filename}
- Examples:
  - https://developer.ibm.com/caas-storage/skillscollection/demo/preview/_attachments/nature_compressed.jpg
  - https://developer.ibm.com/caas-storage/skillscollection/demo/preview/devops/en/_attachments/nature.jpg
- folders starting with __ (two underscores) are considered private attachments folders
- all files found in the private attachments folders can be downloaded with authorized API requests


## Metadata

- metadata is provided in .json files
- there are two levels of metadata: 
  - document metadata at the document level
  - document info metadata at the catalog level
- document metadata
  - are defined in a file named document.json inside the document folder
  - can contain any metadata in json format (e.g. {"title":"Artificial Intelligence", "language":"en", "status":"Approved"} )
- document info metadata
  - are defined in catalog.json
  - can contain any metadata in json format associated with a documentId (e.g. {"explorer-cloud": {"topic": "cloud", "journey": "explorer"} )


## CaaS synchronization with repository
- in order to keep CaaS in sync with repository some hooks have to be defined in the repository
- for each catalog in the repository there have to be a corresponding hook added on push event
- the hook path will be: https://developer.ibm.com/edge/caas/catalogs/sync/{catalogId} (e.g. https://developer.ibm.com/edge/caas/catalogs/sync/30398e579a6353f604c862b946de6300)
- the sync API is optimized to detect changes and sync only updated content, making the changes available in only few seconds


## Naming conventions
- catalog public attachments folder - any folder starting with _ (underscore) in the branch root
- catalog private attachments folder - any folder starting with __ (two underscores) in the branch root
- documents info, at the catalog level - documents.json file in the branch root
- document - folder in the branch root named as {documentid}[space]{language}
- document metadata - document.json file in the document folder
- document public attachments folder - any folder starting with _ (underscore) in the document folder
- document private attachments folder - any folder starting with __ (two underscores) in the document folder
- files and folders starting with . (dot) are ignored


