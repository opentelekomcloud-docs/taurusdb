:original_name: gaussdb_03_0005.html

.. _gaussdb_03_0005:

Making an API Request
=====================

This section describes the structure of a REST API, and uses the IAM API for `obtaining a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__ as an example to describe how to call an API. The obtained token is used to authenticate the calling of other APIs.

Request URI
-----------

A request URI consists of the following:

**{URI-scheme}://{Endpoint}/{resource-path}?{query-string}**

Although a request URI is included in a request header, most programming languages or frameworks require the request URI to be separately transmitted, rather than being conveyed in a request message.

.. table:: **Table 1** Parameters in a URI

   +---------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Description                                                                                                                                                                                                                                                       |
   +===============+===================================================================================================================================================================================================================================================================+
   | URI-scheme    | Protocol used to transmit requests. All APIs use HTTPS.                                                                                                                                                                                                           |
   +---------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Endpoint      | Domain name or IP address of the server bearing the REST service. The endpoint varies between services in different regions. It can be obtained from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.                        |
   +---------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resource-path | Access path of an API for performing a specified operation. Obtain the path from the URI of an API. For example, the **resource-path** of the API used to obtain a user token is **/v3/auth/tokens**.                                                             |
   +---------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | query-string  | Query parameter, which is optional. Ensure that a question mark (?) is included before each query parameter that is in the format of "Parameter name=Parameter value". For example, **? limit=10** indicates that a maximum of 10 data records will be displayed. |
   +---------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   To simplify the URI display in this document, each API is provided only with a resource-path and a request method. The **URI-scheme** of all APIs is **HTTPS**, and the endpoints of all APIs in the same region are identical.

Request Methods
---------------

The HTTP protocol defines the following request methods that can be used to send a request to the server:

.. table:: **Table 2** HTTP methods

   +--------+---------------------------------------------------------------------+
   | Method | Description                                                         |
   +========+=====================================================================+
   | GET    | Requests the server to return specified resources.                  |
   +--------+---------------------------------------------------------------------+
   | PUT    | Requests the server to update specified resources.                  |
   +--------+---------------------------------------------------------------------+
   | POST   | Requests the server to add resources or perform special operations. |
   +--------+---------------------------------------------------------------------+

For example, in the case of the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__, the request method is POST. The request is as follows:

Request Header
--------------

You can also add additional fields to a request, such as the fields required by a specified URI or an HTTP method. For example, to request for the authentication information, add **Content-Type**, which specifies the request body type.

:ref:`Table 3 <gaussdb_03_0005__table1986821153312>` lists common request header fields.

.. _gaussdb_03_0005__table1986821153312:

.. table:: **Table 3** Common request headers

   +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+--------------------------------------------+
   | Name            | Description                                                                                                                                                                                                                                                       | Mandatory                                             | Example                                    |
   +=================+===================================================================================================================================================================================================================================================================+=======================================================+============================================+
   | Host            | Specifies the requested server information, which can be obtained from the URL of the service API. The value is in the *hostname[:port]* format. If the port number is not specified, the default port is used. The default port number for **https** is **443**. | No                                                    | code.test.com                              |
   |                 |                                                                                                                                                                                                                                                                   |                                                       |                                            |
   |                 |                                                                                                                                                                                                                                                                   | This parameter is mandatory for AK/SK authentication. | or                                         |
   |                 |                                                                                                                                                                                                                                                                   |                                                       |                                            |
   |                 |                                                                                                                                                                                                                                                                   |                                                       | code.test.com:443                          |
   +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+--------------------------------------------+
   | Content-Type    | Specifies the MIME type of the request body. You are advised to use the default value **application/json**. For APIs used to upload objects or images, the value can vary depending on the flow type.                                                             | Yes                                                   | application/json                           |
   +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+--------------------------------------------+
   | Content-Length  | Specifies the length of the request body. The unit is byte.                                                                                                                                                                                                       | No                                                    | 3495                                       |
   +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+--------------------------------------------+
   | X-Project-Id    | Specifies the project ID. Obtain the project ID by following the instructions in :ref:`Obtaining a Project ID <gaussdb_10_0004>`.                                                                                                                                 | No                                                    | e9993fc787d94b6c886cbaa340f9c0f4           |
   +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+--------------------------------------------+
   | X-Auth-Token    | Specifies the user token.                                                                                                                                                                                                                                         | No                                                    | The following is part of an example token: |
   |                 |                                                                                                                                                                                                                                                                   |                                                       |                                            |
   |                 | The user token is a response to the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__. This API is the only one that does not require authentication.                                                | This parameter is mandatory for token authentication. | MIIPAgYJKoZIhvcNAQcCo...ggg1BBIINPXsidG9rZ |
   |                 |                                                                                                                                                                                                                                                                   |                                                       |                                            |
   |                 | After the request is processed, the value of **X-Subject-Token** in the message header is the token value.                                                                                                                                                        |                                                       |                                            |
   +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+--------------------------------------------+

The API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__ does not require authentication. Therefore, only the **Content-Type** field needs to be added to requests for calling the API. An example of such requests is as follows:

(Optional) Request Body
-----------------------

This part is optional. The body of a request is often sent in a structured format (for example, JSON or XML) as specified in the **Content-Type** header field. If the request body contains full-width characters, these characters must be coded in UTF-8.

The request body varies between APIs. Some APIs do not require the request body, such as the APIs requested using the GET and DELETE methods.

In the case of the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__, the request parameters and parameter description can be obtained from the API request. The following provides an example request with a body included. Replace **username**, **domainname**, **\*******\*** (login password), and **xxxxxxxxxxxxxxxxxx** (project name) with actual values. It can be obtained from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__.

.. note::

   The **scope** parameter specifies where a token takes effect. You can set **scope** to an account or a project under an account. In the following example, the token takes effect only for the resources in a specified project. For more information about this API, see `Obtaining a User Token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__.

.. code-block::

   Content-Type: application/json

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",
                       "password": "********",
                       "domain": {
                           "name": "domainname"
                       }
                   }
               }
           },
           "scope": {
               "project": {
                   "name": "xxxxxxxxxxxxxxxxxx"
               }
           }
       }
   }

If all data required for the API request is available, you can send the request to call the API through `curl <https://curl.haxx.se/>`__, `Postman <https://www.getpostman.com/>`__, or coding. In the response to the API used to obtain a user token, **x-subject-token** is the desired user token. This token can then be used to authenticate the calling of other APIs.
