

    Skip to Content
    Skip to Search
    Home

Help Center
REST API for Documents

    CloudCloud PlatformOracle Content Management

REST API for Documents
Introduction
Expand All
Collapse All

    About the REST APIs
    All REST Endpoints

Get Started

    Quick Start
    Authorization
    Send Requests
    cURL Access
    REST API Features
    API Resources 

Tasks

    Applinks
    Catalog
    Client Applications
    Configuration
    Files
        Abort an Extraction Job
        Assign a Metadata Collection to a File
        Assign Values to a File Metadata Collection
        Copy File
        Create File Conversation
        Delete All File Tags
        Delete Custom Rendition
        Delete File
        Delete Values in File Metadata Collection
        Download File
        Edit File
        Edit File Tags
        Extract ZIP File into a Folder
        Generate File Renditions
        Get File Accesses
        Get File Assigned Metadata Collections
        Get File HTML5 Preview
        Get File Information
        Get File Metadata Collection
        Get File Tags
        Get File Versions
        Get Information on Multiple Files
        Get Rendition
        Get Rendition Page Count
        Get Responsive Large Image
        Get Responsive Medium Image
        Get Responsive Small Image
        Get Responsive Thumbnail Image
        Get Status of an Extraction Job
        Get Thumbnail
        List Renditions
        Move File
        Reserve File
        Set File Tags
        Unreserve File
        Upload Custom Rendition
        Upload File
        Upload File Version
    Folders
    Metadata Collection
    Publiclinks
    Shares
    Sites
    Templates
    Users

Edit File
put

/documents/api/1.2/files/{fileId}

Change the name of the specified file.

Request
Supported Media Types

    application/json
    application/xml

Path Parameters

    fileId: string

Header Parameters

    accessToken(optional): string
    appLinkID(optional): string
    dAccessCode(optional): string
    linkID(optional): string

Body (

    FileEditBody

)
The request body defines details of the edit file request. There are no required attributes.
Type: object

The request body defines details of the edit file request. There are no required attributes.

    name(optional): string

Example Request (application/json)

{
    "name":"filev4.txt"
}

Back to Top
Response
Supported Media Types

    application/json
    application/xml

200 Response

The request was fulfilled.
Body (

    FileResponse

)
Type: object
The response body includes information about the file.

    errorCode(optional): number

Match All
object

Example Response (application/json)

{
    "id":"D574378400573ED9D62B3195T0000000000100000001",
    "parentID":"FB4CD874EF94CD2CC1B60B72T0000000000100000001",
    "name":"filev4.txt",
    "type":"file",
    "size":"13",
    "version":"4",
    "createdTime":"2014-02-21T21:32:37Z",
    "modifiedTime":"2014-02-21T21:32:37Z",
    "createdBy":{
        "displayName":"User AA",
        "id":"U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName":"userAALoginName",
        "type":"user"
    },
    "ownedBy":{
        "displayName":"User AA",
        "id":"U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName":"userAALoginName",
        "type":"user"
    },
    "modifiedBy":{
        "displayName":"User AA",
        "id":"U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName":"userAALoginName",
        "type":"user"
    },
    "errorCode":"0"
}

400 Response

Request parameters are not formatted correctly.
403 Response

Forbidden if the user does not have read permission.
404 Response

File ID is not found.
Back to Top
Examples

The following example renames the specified file.

PUT .../files/D574378400573ED9D62B3195T0000000000100000001

Request Header

None.

Request Body

{
    "name": "filev4.txt"
}

HTTP Status Code

HTTP_STATUS = 200

JSON Response

{
    "createdBy": {
        "displayName": "User AA",
        "id": "U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName": "userAALoginName",
        "type": "user"
    },
    "createdTime": "2014-02-21T21:15:57Z",
    "errorCode": "0",
    "id": "D574378400573ED9D62B3195T0000000000100000001",
    "modifiedBy": {
        "displayName": "User AA",
        "id": "U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName": "userAALoginName",   
        "type": "user"
    },
    "modifiedTime": "2014-02-21T21:21:27Z",
    "name": "filev4.txt",
    "ownedBy": {
        "displayName": "User AA",
        "id": "U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName": "userAALoginName",        
        "type": "user"
    },
    "parentID": "FB4CD874EF94CD2CC1B60B72T0000000000100000001",
    "size": "13",
    "type": "file",
    "version": "4"
}

Example 2

The following example renames the specified file. The example uses a public link ID because this file is under a folder structure not owned by or shared with the current user.

PUT .../files/D574378400573ED9D62B3195T0000000000100000001

Request Header

LinkID: LF8D36FAFAB4388BECEAC4AEB5D17B95F47087F4E518

Request Body

{
    "name": "filev4.txt"
}

HTTP Status Code

HTTP_STATUS = 200

JSON Response

{
    "createdBy": {
        "displayName": "User AA",
        "id": "U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName": "userAALoginName",
        "type": "user"
    },
    "createdTime": "2014-02-21T21:15:57Z",
    "errorCode": "0",
    "id": "D574378400573ED9D62B3195T0000000000100000001",
    "modifiedBy": {
        "displayName": "User AA",
        "id": "U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName": "userAALoginName",
        "type": "user"
    },
    "modifiedTime": "2014-02-21T21:21:27Z",
    "name": "filev4.txt",
    "ownedBy": {
        "displayName": "User AA",
        "id": "U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName": "userAALoginName",
        "type": "user"
    },
    "parentID": "FB4CD874EF94CD2CC1B60B72T0000000000100000001",
    "size": "13",
    "type": "file",
    "version": "4"
}

Example 3

The following example renames the specified file. The example uses a public link ID protected by an access code because this file is under a folder structure not owned by or shared with the current user. An access code (test12345) is submitted as part of a Cookie in the request header.

PUT .../files/D574378400573ED9D62B3195T0000000000100000001

Request Header

LinkID: LF8D36FAFAB4388BECEAC4AEB5D17B95F47087F4E518
Cookie: dAccessCode-LF8D36FAFAB4388BECEAC4AEB5D17B95F47087F4E518=test12345

Request Body

{
    "name": "filev4.txt"
}

HTTP Status Code

HTTP_STATUS = 200

JSON Response

{
    "createdBy": {
        "displayName": "User AA",
        "id": "U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName": "userAALoginName",
        "type": "user"
    },
    "createdTime": "2014-02-21T21:15:57Z",
    "errorCode": "0",
    "id": "D574378400573ED9D62B3195T0000000000100000001",
    "modifiedBy": {
        "displayName": "User AA",
        "id": "U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName": "userAALoginName",
        "type": "user"
    },
    "modifiedTime": "2014-02-21T21:21:27Z",
    "name": "filev4.txt",
    "ownedBy": {
        "displayName": "User AA",
        "id": "U0EAA20910FAF3052ACB79E4T00000000001",
        "loginName": "userAALoginName",
        "type": "user"
    },
    "parentID": "FB4CD874EF94CD2CC1B60B72T0000000000100000001",
    "size": "13",
    "type": "file",
    "version": "4"
}

Example 4

The following example requests file renaming. Because this file is under a folder structure not owned by or shared with the current user, an access denied error message is returned.

PUT .../files/D574378400573ED9D62B3195T0000000000100000001

Request Header

None.

Request Body

{
    "name": "filev4.txt"
}

HTTP Status Code

HTTP_STATUS = 403

JSON Response

{
    "errorCode": "-20",
    "errorKey": "!csFldUnableToEditDocumentLink!csCloudItemInsufficientPrivileges,User BB,fFileGUID:D574378400573ED9D62B3195T0000000000100000001,FLD_EDIT_FILE",
    "errorMessage": "Unable to edit foldering information. User 'User BB' has insufficient privilege to access fFileGUID:D574378400573ED9D62B3195T0000000000100000001 with service FLD_EDIT_FILE.",
    "errorType": "file",
    "id": "D574378400573ED9D62B3195T0000000000100000001",
    "name": "filev4.txt",
    "title": "Unable to edit foldering information. User 'User BB' has insufficient privilege to access fFileGUID:D574378400573ED9D62B3195T0000000000100000001 with service FLD_EDIT_FILE.",
    "type": "https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html"
}

Example 5

The following example requests file renaming. This file is under a folder structure not owned by or shared with the current user, and only a public link protected by an access code is available. An error is returned because the access code was not submitted as part of the request.

PUT .../files/D574378400573ED9D62B3195T0000000000100000001

Request Header

LinkID: LF8D36FAFAB4388BECEAC4AEB5D17B95F47087F4E518

Request Body

{
    "name": "filev4.txt"
}

HTTP Status Code

HTTP_STATUS = 403

JSON Response

{
    "errorCode": "-18",
    "errorKey": "!csFldUnableToEditDocumentLink!csAccessCodeRequiredForLinkAccess",
    "errorMessage": "Unable to edit foldering information. The access code must be provided to access the link.",
    "errorType": "file",
    "id": "D574378400573ED9D62B3195T0000000000100000001",
    "name": "filev4.txt",
    "title": "Unable to edit foldering information. The access code must be provided to access the link.",
    "type": "https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html"
}

Example 6

The following example renames the specified file. The example uses an applink because this file is under a folder structure not owned by or shared with the current user. The applink ID and access token are submitted in the request header.

PUT .../files/DED694950C14AFF280419F9AB5D17B95F47087F4E518

Request Header

appLinkID: LF5Bxj4TPo_p4n4qWn0tbKTicR2cTUJKv7X_ng9E7ry93rRuDokPqS1d6-wKwhb_wtcGYFDsI_cNMxeKQ-HR-FXQhiVoGRTYM_MPZY8qpICfYU94mmnMjM_cvsRhKMzc0NJgvwEJfqqDwPsAVrhc8cmg==
accessToken: 352FpiMmW66PeYI1Gh5b83I9CXRwZhLfYAu4TXdqpzD8uNKUBMZVVJ3ZvivUW8kQ

Request Body

{
    "name": "fileViaApplink-renamed.txt"
}

HTTP Status Code

HTTP_STATUS = 200

JSON Response

{
    "createdBy": {
        "displayName": "User BB",
        "id": "U5083EA1954687218BA6C3D9B5D17B95F470",
        "loginName": "U5083EA1954687218BA6C3D9B5D17B95F470",
        "type": "user"
    },
    "createdTime": "2017-06-26T15:29:00Z",
    "errorCode": "0",
    "id": "DED694950C14AFF280419F9AB5D17B95F47087F4E518",
    "mimeType": "text/plain",
    "modifiedBy": {
        "displayName": "User BB",
        "id": "U5083EA1954687218BA6C3D9B5D17B95F470",
        "loginName": "U5083EA1954687218BA6C3D9B5D17B95F470",
        "type": "user"
    },
    "modifiedTime": "2017-06-26T20:27:23Z",
    "name": "fileViaApplink-renamed.txt",
    "ownedBy": {
        "displayName": "User AA",
        "id": "UEB6AD431E4357AE752CE3F2B5D17B95F470",
        "loginName": "userAALoginName",
        "type": "user"
    },
    "parentID": "FDC22B65E850730CAA60AF83B5D17B95F47087F4E518",
    "size": "29",
    "type": "file",
    "version": "2"
}

    © Oracle
    About Oracle
    Contact Us
    Products A-Z
    Terms of Use & Privacy
    Cookie Preferences
    Ad Choices

