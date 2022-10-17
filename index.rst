:tocdepth: 2

.. sectnum::

.. Metadata such as the title, authors, and description are set in metadata.yaml

Abstract
========

This technote details the types of documentation that are available to System Integration Test & Commissioning (SIT-Com) personnel, and when they should be used.


Introduction
============

The Vera C. Rubin Observatory SIT-Com team is tasked with performing system characterization and verification, which will result in numerous pieces of documentation being generated, such as: procedures, control code, data reductions and analyses, and a variety of verification artifacts.
During the development, commissioning, and operations of the observatory, numerous types of documentation will be developed, including documentation from vendors.

All documentation will be stored and/or archived for later use.
The type of documentation that is most appropriate to use is dependent upon the situation.
This document describes the different documentation options and when they may be applicable to your specific case.

.. Important::

   Questions that are not answered by this document can be asked in the ``#rubinobs-sitcom-docs`` Slack channel.


Project-level change controlled documentation
=============================================

SIT-Com follows the project standard in that all documentation requiring project-level change control requires an LSE document handle and all modifications to the document are handled through the project Change Control Board (CCB).
Specifically, this should includes procedures which may result in damage to equipment and/or injury to personnel (e.g., mirror handling) and formal documentation such Interface Control Documents (ICDs).
It is anticipated that very few SIT-Com generated artifacts will fall into this category.

SIT-Com-level change control
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Documentation that is applicable to only SIT-Com personnel and/or internal to SIT-Com subsystems, the implementation of a SIT-Com change control board has been discussed, but is not currently in place.
Examples of documents that are SIT-Com specific and should be under change control include documentation of workflows (like this one), management plans, and SIT-Com specific procedures that require sign-off by specific domain experts.
Until a SIT-Com change control system is enacted, these types of documentation exist as `Technotes`_.

When required to be under stricter change control, GitHub repository branch protection should be put in place.
The designation of specific names for the reviewers can also be manually specified.
In the event that adding non-default protections to a technote's repository (discussed below), please consult the ``#rubinobs-sitcom-docs`` Slack channel for support and guidance.

.. note::

   Even when not explicitly required, the use of branches and pull requests are highly encouraged for all documentation content, as it increases the quality, clarity, and accuracy of the content being communicated.


General documentation types
===========================

This section outlines the different types of documentation used by SIT-Com personnel.

Jira tickets
^^^^^^^^^^^^

SIT-Com related work should follow the `SIT-Com specific Jira workflow <https://sitcomtn-023.lsst.io/>`_.
Documentation in Jira tickets should be sufficiently detailed such that it addresses the description in the task.
It is not expected to be consulted in the future, especially on a regular occurrence.
In many cases, specifically when characterization activities have taken place over a series of tickets, external documentation should be developed and linked to the Jira ticket(s).
This documentation should also refer to the Jira ticket(s).
The type of document to be created is dependent upon the situation, but will most likely be covered by `Technotes`_ and/or inclusion of a section in one of the `Webspaces`_.
The creation of the documentation can be performed under one of the already opened tickets, or a new ticket can be created that is dedicated to the generation of documentation.


Verification documentation and artifacts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Systems Engineering team uses a specific Jira project for its verification performance and tracking.
Personnel looking for verification documentation should consult `LSE-160 <https://ls.st/LSE-160>`_.

The verification and validation process also utilize a specific repository for storing of Jupyter notebooks that act as official artifacts.
This is further described in the `Verification And Validation Notebooks`_ subsection below.


Technotes
^^^^^^^^^

Technotes are useful for documenting information that is static and/or temporary in nature, such as specific tests and/or findings, proposals of new functionality or architectures, and documenting specific usages that augment user documentation.
They can also be used as logs and/or take status of longer term analyses.

Technotes should not be used in place of procedures or other user-facing how-to documentation.
This is better addressed as part of the `Obs-Ops Webspace`_ or even an addition to the collection of `Collaborative Notebooks`_.

An example of this is the technote on `Building and Fitting the Pointing Model for the Auxiliary Telescope <https://tstn-014.lsst.io/>`_.
This technote has chapters (outlined and linked on the left sidebar) showing the analysis from different runs and the results that were obtained.
This is an appropriate use of a technote --
the purpose is to capture a specific process within a point in time;
the information will likely never require major modification;
and, information that is generally applicable (e.g., the pointAddData command) is incorporated into other documentation that users are expected to access.

Creation and review of technotes
--------------------------------

Before creating a technote, a Jira ticket should be opened following the `SIT-Com work management Jira workflow <https://sitcomtn-023.lsst.io/>`_.
The use of a ticket helps with tracking progress, linking to other applicable tickets, and to facilitate an easier review process.
In general, technote reviews should be performed by the intended customer of its content.
Collaborators and subject matter experts are also useful reviewers.

Technote are created by private messaging the ``sqrbot-jr`` bot on Slack by sending the message ``create project``.
At this time, options will pop up and the user selects the template they desire (AASTEX LaTeX, lsstdoc LaTeX or reStructuredText).
The document will be created with an associated GitHub repository and webpage to view the document, with the URL form ``sitcomtn-###.lsst.io``.
The choice of template is up to the user; however, using reStructuredText will render as a webpage at ``sitcomtn-###.lsst.io``, whereas the other options will render as PDF at the same URL.
Depending on how the document will be used and/or interacted with, there may be a preference for a specific format.

.. note::

   Adding a ``/v`` to the URL will display the rendered versions of all branches in the repository (e.g., `<sitcomtn-048.lsst.io/v>`_).

When relevant, technotes should also link and/or include all supporting documentation and artifacts.
This includes any Jupyter notebooks and Jira tickets where work was performed, especially if there exists content in the external source which may be applicable to the technote.
Inside the technote's repository is a ``_static`` directory where other files (i.e., static objects) can be included, such as any analysis Jupyter Notebook referenced by the text or supporting figures.

**Technotes should never be deleted.**
In the event that the content becomes stale, superseded, or even found to be incorrect, a revision to the technote should be committed removing or correcting the content.
As appropriate, include ``DEPRECATED`` in the title and link any documents that replace the technote.
This way the content is never entirely lost, as it will remain in the git history of the repository.

The Data Management team uses technotes extensively and ensures these tools are well maintained.
More information on using the tool(s) can be found at `their dedicated webpage <https://developer.lsst.io/project-docs/technotes.html>`__.


Jupyter notebooks
^^^^^^^^^^^^^^^^^

Jupyter notebooks (henceforth referred to as notebooks) are used routinely during commissioning exercises for both analysis and even for certain early observatory control sequences.
Although their use is not strictly required, they allow simultaneously controlling of observatory functionality, data reduction/analysis tasks and documentation, and are supported by the project at large.
Furthermore, they are a natural starting point for development of ideas and demonstrating proof of concept(s).

.. Important::

   Notebooks are not to hold functional code over extended periods of time (~2 weeks), nor are they meant to augment observatory control and/or reduction software.

   If a piece of code (e.g., a function) developed in a notebook is useful, then it must be moved into a function in the development repositories.
   In the case of control system code, this workflow is discussed in `TSTN-010 <https://tstn-010.lsst.io/>`_.

An easy indication is that if one finds themselves copying/pasting code from a notebook to another, then that code should not be in a notebook!
It is expected that if something is developed during a commissioning activity or observing run that the code is moved in short order.
If one does not have the knowledge or ability to do this, then ask for assistance from other observatory personnel (e.g., the ``#rubinobs-sitcom-docs`` Slack channel).

.. Important::

   At no time should observatory-related notebooks be stored locally and/or in a personal git repository.

The following subsections explain the two areas that have been developed to contain the various types of notebooks that will be created by users for their personal use, and for use by colleagues.

Personal notebooks
------------------

Personal notebooks are intended for use by only the writer/author.
It is possible they may be shared on an individual level, but they are not meant to be a common reference and/or fit for public consumption (e.g., level of code documentation is left to the user).
One example of such a notebook is content that is created during diagnosis of a specific bug and/or a small one-off analysis.
Another example would be the modification of a generalized template notebook for a specific application.

To facilitate the use of notebooks, a method to create personal repositories, that can still be seen by the team, has been created using the ``sqrbot-jr`` bot in Slack.
To create a personal SIT-Com Notebook GitHub repository, send a private message to ``sqrbot-jr``, then under the dropdown is a ``SIT-Com`` heading, below which is a ``Personal Notebooks`` option.
Select this and follow the instructions to have your own repository automatically created.
The repository has a structure to help the organization and imports of user-developed methods that are imported to the notebooks.
See the README file in the newly created repository for further information.

The content in the personal notebook repository, including the structure, workflow and folder organization, is up to the user and is not subject to any peer review.
However, if content in your personal repository is useful to others, then it should be made available via the repository of `Collaborative Notebooks`_.
If the notebook is used to analyze data or create figures that are presented in a technote, then the notebook and associated files should be added to the ``_static`` directory of that technote's repository.
Lastly, if the code developed in the notebook needs to be migrated into scripts or methods of the control system, it should follow the workflow described in `TSTN-010 <https://tstn-010.lsst.io/>`_.

Collaborative notebooks
-----------------------

In many cases, users will develop notebooks that are broadly applicable to many people.
The notebooks themselves can serve a variety of purposes from start-up/shut-down procedures to small data-analysis tasks.
Notebooks like this are written at a level such that they can be used by project personnel, and therefore are expected to contain adequate explanation, comments, and an easily navigable layout.

Collaborative notebooks are stored in the `ts_notebooks repository <https://github.com/lsst-ts/ts_Notebooks>`_.
Notebooks moved into this area are subject to review prior to merging.
Message the ``#rubinobs-sitcom-docs`` Slack channel for guidance.

This space is currently being modified to better support the usage described here, but examples can be found in the `AuxTel area in lsst-ts/ts_notebook <https://github.com/lsst-ts/ts_notebooks/tree/develop/procedures/auxtel>`_.
Once the architecture is available, the intention is also to provide test assertions such as units tests via a continuous integration framework when applicable.
This is used to prevent bit rot, which is especially prevalent during the early commissioning and operations stages of projects.

Verification And Validation Notebooks
-------------------------------------

Notebooks that are used as official artifacts for verification are stored in the `lsst-sitcom/notebooks_vandv repository <https://github.com/lsst-sitcom/notebooks_vandv>`_.
To store in this area requires a Zephyr Jira Test Case counterpart.
Details on how to use this area is found in the README file of the repository.

Review Criteria
"""""""""""""""

Official artifacts for verification require specified review criteria.
This section will be populated in a future revision of this document by the verification coordinators.
As mentioned previously, the expectation is that the notebooks closely resemble the `AuxTel area in lsst-ts/ts_notebook <https://github.com/lsst-ts/ts_notebooks/tree/develop/procedures/auxtel>`_ example.

Webspaces
^^^^^^^^^

During early operations of the Auxiliary Telescope, there was a need to have the information required for operators be assembled into a single area with a coherent, searchable structure.
The architecture, sometimes referred to as *user guides* or *webspaces*, for `The LSST Science Pipelines documentation <https://pipelines.lsst.io>`_ was extensively used and readily available.
To an end user, webspaces are very similar to technotes -- with the name space of the requstor's choice, it will be created with an associated GitHub repository and website with the name space, with the URL form ``namespace.lsst.io``.
Two webspaces have been created to support efforts with the Auxiliary Telescope, and they are described in the subsections below.

.. note::

   Adding a ``/v`` to a webspace URL will display the rendered versions of all branches in the repository.

Webspaces are areas are best used for user-facing documentation.
This includes general information, how-to documentation and procedures that are not subject to change control (therefore, these procedures are restricted to ones that do not risk the safety of personnel or equipment).
Anything requiring strict reviews (e.g., glass lift plans) cannot be put into a webspace, but the official location can be linked, for example, a DocuShare document.

Users are encouraged to populate these areas, which can be accomplished via a standard pull request to GitHub repositories (details in the following sections).
If there is not an obvious space for your content, then please ask in the ``#rubinobs-sitcom-docs`` Slack channel.
In the event that a large series of documentation is required that does not fit into the already created webspaces, it is possible to create new areas with relative ease by request to the respective Rubin Observatory personnel.
However, it's beneficial to limit the number of webspaces, while still keeping the webspaces focused and easy to use.

Eventually, it is anticipated that there will be a more structured, high-level website that will serve as a standardized place to begin navigating existing documentation.
Until that infrastructure exists, which will also support reStructuredText (meaning all the content is easily movable), webspaces provide functionality where content can be easily added, used immediately, and moved to it's final destination with ease at a later date.

Obs-Ops webspace
----------------

The `Rubin Observatory Operations (Obs-Ops) Documentation webspace <https://obs-ops.lsst.io>`__ is being populated to assist with on-site commissioning and operations related activities.
The content largely comes from people performing the tests and/or nightly operations.
For the moment, the content being added is focused on observing procedures and collecting required reference material, but the larger goal is for each of the areas to link to any other applicable documentation including technotes, DocuShare, or other areas.

Editing the `Obs-Ops webspace <https://obs-ops.lsst.io>`_ is performed by creating a branch, committing changes in the `Observatory-Ops-Docs repository <https://github.com/lsst-ts/observatory-ops-docs>`_, verifying the build passes, then filing a pull request.
There are detailed instructions on how to complete these steps in the `Contributing to Observatory Operations Documentation section <https://obs-ops.lsst.io/project/contributing.html#contributing-to-observatory-operations-documentation>`_ of the webspace.
Message the ``#rubinobs-sitcom-docs`` Slack channel for guidance on content, suggestions, or reviews and pull requests.

Obs-Controls webspace
---------------------

The `Rubin Observatory Controls (Obs-Controls) Documentation webspace <https://obs-controls.lsst.io>`__ fulfills the same purpose as the `Obs-Ops webspace`_, except it is focused on observatory control software.
This area is the first place to go when looking to learn more about the control system and how to use it.
SIT-Com personnel are encouraged to populate and contribute to this webspace, as well.
It is very common (and encouraged) to link content between this area and the `Obs-Ops webspace`_.

The process to edit the `Obs-Control webspace <https://obs-controls.lsst.io>`_ follows the same concept as the `Obs-Ops webspace`_.
The instructions are in the `Contributing to Observatory Controls Documentation  section <https://obs-controls.lsst.io/project/contributing.html#contributing-to-observatory-controls-documentation>`_ of the webspace.

.. note::

   Details on writing and documenting control software code are found in the `TSSW Developer Guide <https://tssw-developer.lsst.io/>`_.
   For Data Management centric code, follow the `LSST DM Developer Guide <https://developer.lsst.io/>`_.
   Both guides are based upon the same principles and have significant overlap.


DocuShare
^^^^^^^^^

DocuShare is used heavily inside the project, particularly for vendor documentation, contract documents, and project-level change controlled documentation -- `<https://docushare.lsstcorp.org/docushare/dsweb/HomePage>`_.
Its use is required in certain situations.
Files and documents are stored by handles (e.g., DOCUMENT-XXXXX, LSE-XXX) and handles can be associated with various *collections*.

SIT-Com has a specific collection that is available for use: `Systems Engineering & Commissioning DocuShare collection <https://docushare.lsst.org/docushare/dsweb/View/Collection-26>`_.
Note that as part of the project-wide Documentation Working Group, the collections and application of DocuShare will be restructured.
Message the ``#rubinobs-sitcom-docs`` Slack channel for guidance before creating or editing files or collections in DocuShare.

.. Make in-text citations with: :cite:`bibkey`.
.. Uncomment to use citations
.. .. rubric:: References
..
.. .. bibliography:: local.bib lsstbib/books.bib lsstbib/lsst.bib lsstbib/lsst-dm.bib lsstbib/refs.bib lsstbib/refs_ads.bib
..    :style: lsst_aa
