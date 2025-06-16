:original_name: gaussdb_03_0001.html

.. _gaussdb_03_0001:

Authentication
==============

Token authentication must be performed to call APIs.

Authentication using tokens: General requests are authenticated using tokens.

Token-based Authentication
--------------------------

.. note::

   The validity period of a token is 24 hours. When using a token for authentication, cache it to prevent frequently calling the IAM API used to obtain a user token.

A token specifies temporary permissions in a computer system. During API authentication using a token, the token is added to requests to get permissions for calling the API.

.. code-block::

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
                    "name": "xxxxxxxx"
                }
            }
        }
    }

In :ref:`Making an API Request <gaussdb_03_0005>`, the process of calling the API used to `obtain a user token <https://docs.otc.t-systems.com/en-us/api/iam/en-us_topic_0057845583.html>`__ is described.

After a token is obtained, add the **X-Auth-Token** header field must be added to requests to specify the token when calling other APIs. For example, if the token is **ABCDEFJ....**, **X-Auth-Token: ABCDEFJ....** can be added to a request as follows:

::

   Content-Type: application/json
   X-Auth-Token: ABCDEFJ....
