:original_name: gaussdb_10_0004.html

.. _gaussdb_10_0004:

Obtaining a Project ID
======================

Scenarios
---------

When calling APIs, you need to specify the project ID in some URLs. To do so, you need to obtain the project ID first. Two methods are available:

-  :ref:`Obtaining the Project ID by Calling an API <gaussdb_10_0004__section85791974381>`
-  :ref:`Obtain a Project ID from the Console <gaussdb_10_0004__section196091152113715>`

.. _gaussdb_10_0004__section85791974381:

Obtaining the Project ID by Calling an API
------------------------------------------

The API used to obtain a project ID is **GET https://{Endpoint}/v3/projects**. **{Endpoint}** is the IAM endpoint and can be obtained from `Regions and Endpoints <https://docs.otc.t-systems.com/en-us/endpoint/index.html>`__. For details about API authentication, see :ref:`Authentication <gaussdb_03_0001>`.

The following is an example response. The value of **id** is the project ID.

.. code-block::

   {
       "projects": [
           {
               "domain_id": "65382450e8f64ac0870cd180d14e684b",
               "is_domain": false,
               "parent_id": "65382450e8f64ac0870cd180d14e684b",
               "name": "project_name",
               "description": "",
               "links": {
                   "next": null,
                   "previous": null,
                   "self": "https://www.example.com/v3/projects/a4a5d4098fb4474fa22cd05f897d6b99"
               },
               "id": "a4a5d4098fb4474fa22cd05f897d6b99",
               "enabled": true
           }
       ],
       "links": {
           "next": null,
           "previous": null,
           "self": "https://www.example.com/v3/projects"
       }
   }

.. _gaussdb_10_0004__section196091152113715:

Obtain a Project ID from the Console
------------------------------------

#. Register yourself on the management console and log in to it.

#. Move your pointer over the username and select My Credentials in the displayed drop-down list.

   On the **My Credentials** page, view project IDs in the project list.


   .. figure:: /_static/images/en-us_image_0000001828922089.png
      :alt: **Figure 1** Viewing project IDs

      **Figure 1** Viewing project IDs
