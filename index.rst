:tocdepth: 1

.. sectnum::

.. Metadata such as the title, authors, and description are set in metadata.yaml

Abstract
========

This technote details the types of documentation that are available to SIT-Com personnel, and when they should be used.

Introduction
============

During the development, commissioning, and operations of the observatory, numerous types of documentation will be developed and/or received from vendors and ultimately archived for later use.
The SIT-Com team is tasked with performing system characterization and verification, which will result in numerous pieces of documentation being generated, such as: procedures, control code, data reductions and analyses, and numerous verification artifacts.
The type of documentation that is most appropriate to use is dependent upon the situation.
This document describes the different documentation options and when they may be applicable to your specific case.

.. Important::
   
   Questions that are not answered by this document can be asked in the ``#rubinobs-sitcom-docs`` Slack channel. 


Project Level Change Controlled Documentation
=============================================

SIT-Com follows the project standard in that all documentation requiring project-level change control requires an LSE document handle and all modifications to the document are handled through the project Change Control Board (CCB).
Specifically, this should includes procedures which may result in damage to equipment and/or injury to personnel (e.g. mirror handling) as well as formal ICDs.
It is anticipated that very few SIT-Com generated artifacts will fall into this category.

SIT-Com Level Change Control
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

In the case of documentation that is applicable to only SIT-Com personnel and is internal to the SIT-Com subsystem(s), the implementation of a SIT-Com change board has been discussed but is not currently in place.
Examples of documents that are SIT-Com specific but should be under change control include the documentation of workflows (like this one), management plans, and/or SIT-Com specific procedures that require sign-off by specific domain experts.
Until such a system is put in place, these types of documentation exist as `Technotes`_.

When required to be under stricter change controls, branch protection should be put in place.
The designation of specific names for the reviewers can also be manually specified.
In the event that adding non-default protections to a technote repository (discussed below), please consult the ``#rubinobs-sitcom-docs`` Slack channel for support.

.. note::

   Even when not explicitly required, the use of branches and pull requests are highly encouraged for all documentation content as it increases the quality, clarity, and accuracy of the content being communicated.

General Documentation Types
===========================

This section outlines the different types of documentation used by SIT-Com personel.

Jira Tickets
^^^^^^^^^^^^

SIT-Com related work should follow the `SIT-Com specific Jira workflow <https://sitcomtn-023.lsst.io/>`_.
Documentation in Jira tickets should be sufficiently detailed such that it addresses the description in the task.
It is not expected to be consulted in the future, especially on a regular occurrence. 
In many cases, specifically when characterization activities have taken place over a series of tickets, external documentation should be developed and linked to from the Jira ticket(s).
The type of document to be created is dependent upon the situation but will most likely be covered by `Technotes`_ and/or inclusion of a section in one of the `Webspaces`_.
The creation of the documentation can be performed under one of the already opened tickets, or a new ticket can be created that explicitly deals with the generation of documentation.


Verification Documentation and Artifacts
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Systems Engineering team uses a specific Jira project for its verification performance and tracking.
Personnel looking for verification documentation should consult `LSE-160 <https://ls.st/LSE-160>`_.

The verification and validation process also utilize a specific repository for the storing of their Jupyter notebooks that act as official artifacts.
This is further described in the `Verification And Validation Notebooks`_ subsection below.


Technotes
^^^^^^^^^^

Technotes are useful for documenting outcomes of specific tests  and/or findings, proposing new functionality or architectures, and/or documenting specific usages that augment user documentation.
They can also be used as logs and/or status of longer term analyses.
An example of this is the technote on `Building and fitting the pointing model for the AuxTel <https://tstn-014.lsst.io/>`_
In this case, there are chapters (seen on the left) showing the analysis from different runs and the results that were obtained.
This is an appropriate use of a technote.

Technotes should not be used in place of user-facing how-to documentation and/or procedures. 
This is better addressed as part of the `Obs-Ops Webspace`_ or even an addition to the collection of `Collaborative Notebooks`_.

Creation and Review of Technotes
--------------------------------

When creating a technote, a Jira ticket should first be opened following the `SIT-Com specific Jira workflow <https://sitcomtn-023.lsst.io/>`_.
The use of a ticket helps with tracking progress, linking to other applicable tickets, and to facilitate an easier review process.
In general, technote reviews should be performed by the intended customer of its content.
Collaborators on the work are also useful reviewers.

Technote are created by private messaging the ``sqrbot-jr`` bot on Slack and sending a ``create project`` message.
At this time, options will pop up and users can select the template they desire (AASTEX LaTeX, lsstdoc LaTeX or reStructuredText).
The choice is up to the user, however, reStructuredText will render as a webpage at ``sitcomtn-###.lsst.io``, whereas the others will render as PDF at the same URL.
Depending on how the document will be used and/or interacted with, there may be a preference for a specific format.

.. note::

   Adding a ``/v`` to the url will display the rendered versions of all branches in the repo (e.g. ``sitcomtn-###.lsst.io/v``).

When relevant, technotes should also link and/or include all supporting documentation and artifacts.
This includes any Jupyter notebooks and/or the tickets where work was performed, especially if there exists content in the ticket which may be applicable to the content.
Inside the technote repository is a ``_static`` directory where other files can be included, such as any analysis Jupyter Notebook referenced by the text, or supporting figures.

Technotes should *never be deleted*.
In the event that the content becomes stale, superseded, or even found to be incorrect, a new version of the technote should be committed that removes the content and has ``DEPRECATED`` in the title.
If applicable, the replacement document(s) should be linked.
This way the content is never entirely lost as it will remain in the git history of the repository.

The Data Management team uses technotes extensively, more information on their using of the tool(s) are found at `their dedicated webpage <https://developer.lsst.io/project-docs/technotes.html>`_.


Jupyter Notebooks
^^^^^^^^^^^^^^^^^

Jupyter notebooks (henceforth referred to as notebooks) are used routinely during commissioning exercises for both analysis and even for certain early observatory control sequences.
Although their use is not strictly required, they allow simultaneously controlling of observatory functionality, data reduction/analysis tasks and documentation, and are supported by the project at large. 
TFurthermore, they are a natural starting point for development of ideas and demonstrating proof of concept(s). 

.. Important::

   Notebooks are not to hold functional code over extended periods of time (~2 weeks) nor are they meant to augment observatory control and/or reduction software. 
   If a piece of code (e.g. a function) developed in a notebook and is useful then it must be moved into a function in the development repositories.
   In this case of control system code, this is further  discussed in `tstn-010 <https://tstn-010.lsst.io/>`_.

A general rule of thumb is that if one finds themselves copying/pasting code from a notebook to another, then that code should not be in a notebook! 
It is expected that if something is developed during a commissioning activity or observing run that this function be moved in short order. 
If one does not have the know-how to do this then ask for assistance from other observatory personnel.

*At no time should Rubin related notebooks be stored locally and/or in a personal git repository.*
The following sub-sections explain the two areas that have been developed to contain the various types of notebooks that will be created by users for their personal use, and for use by colleagues.

Personal Notebooks
------------------

Personal notebooks are intended for use by only the writer/author.
It is possible they may be shared on an individual level, but they are not meant to be a common reference and/or fit for public consumption (e.g. level of code documentation is left to the user).
One example of such a notebook is content that is created during diagnosis of a specific bug and/or a small one-off analysis.
Another example would be the modification of a generalized template notebook for a specific application.

To facilitate the use of notebooks, a method to create personal repos,that can still be seen by the team, has been created.
The repo also has a structure to help the organization and imports of user-developed methods that are imported to the notebooks.
To create a personal SIT-Com Notebook repository, send a private message to ``sqrbot-jr`` on Slack, then under the dropdown is a ``SIT-Com`` heading, below which is a ``Personal Notebooks`` option.
Select this and follow the instructions to have your own repository automatically created.
See the README file in the newly created repo for further information.

The content in the personal notebook repository, including the structure, workflow and folder organization, is up to the user and is not subject to any peer review.
However, if content in your personal repository is useful to others, then it should be made available via the repo of `Collaborative Notebooks`_.
If the notebook is used to analyze data or create figures that are presented in a technote, then it should be added to the ``_static`` directory of that technote's repo.
Lastly, if the code developed in the notebook needs to be migrated into scripts or methods of the control system, it should follow the workflow described in `tstn-010 <https://tstn-010.lsst.io/>`_.

Collaborative Notebooks
-----------------------

In many cases, users will develop notebooks that are broadly applicable to many people.
The notebooks themselves can serve a variety of purposes from startup/shutdown procedures to small data-analysis tasks.
Notebooks in this space are written at a level such that they can be used by project personnel, and therefore are expected to contain adequate explanation, comments, and a easily navigable layout.

Collaborative notebooks are stored in the `ts_notebooks <https://github.com/lsst-ts/ts_Notebooks>`_ repository.
This space is currently being modified to better support the usage described here, but examples can be found in the `AuxTel area <https://github.com/lsst-ts/ts_notebooks/tree/develop/procedures/auxtel>`_.

Notebooks moved into this area are subject to review prior to merging.
Once the architecture is available, the intention is also to provide units tests via a continuous integration framework when applicable.
This is used to prevent bit rot, which is especially prevalent during the early commissioning and operations stages of projects.

Verification And Validation Notebooks
-------------------------------------

Notebooks that are used as official artifacts for verification are stored in the `lsst-sitcom/notebooks_vandv <https://github.com/lsst-sitcom/notebooks_vandv>`_ repository.
To be stored in this area requires they have a Zephyr JIRA Test Case counterpart.
Details on how to use this area is found in the README file of the repository.

Review Criteria
"""""""""""""""

This section will be populated in future versions.
However, as mentioned previously, the expectation is that the notebooks closely resemble the examples found in the `AuxTel area <https://github.com/lsst-ts/ts_notebooks/tree/develop/procedures/auxtel>`_.

Webspaces
^^^^^^^^^

During early operations of the Auxiliary Telescope, there was a need to have the information required for operators assembled into a single area with a coherent, searchable structure.
Following from the examples used by DM, specifically the architecture used for `DM Pipelines <https://pipelines.lsst.io>`_ documentation, two webspaces have been created to support this purpose. 
These are described in the subsections below.

Webspaces are areas are best used for user-facing documentation.
This includes general information, how-to's and procedures that are not subject to change control, and therefore do not risk the safety of personnel or equipment.
Anything requiring strict reviews (e.g. glass lift plans) cannot be put into a webspace, but they can be linked!

Users are encouraged to populate these areas, which can be accomplished via a standard pull-request to github repos (details in the following sections).
If there is not an obvious space for your content then please ask in the ``#rubinobs-sitcom-docs`` Slack channel.
In the event that a large series of documentation is required that does not fit into the already created webspaces, it is possible to create new spaces with relative ease.

Eventually, it is anticipated that there will be a more structured high-level website that will serve as a standardized place to begin navigating to the desired document.
Until that infrastructure exists, which will also support reStructuredText (meaning all the content is easily movable), this area provides the space where content can be easily added, used immediately, and moved to it's final destination with ease at a later date.

Obs-Ops Webspace
----------------

The `Obs-Ops Webspace <https://obs-ops.lsst.io>`_ is being populated to assist with on-site commissioning and operations related activities.
The content largely comes from people performing the tests and/or nightly operations.
For the moment, the content being added is focused on observing procedures and/or required reference material, but the larger goal is for each of the areas to link to any other applicable documentation that could be stored in technotes, Docushare, or other areas.

Editing the `Obs-Ops Webspace <https://obs-ops.lsst.io>`_ is performed by making a branch from the `GitHub repo <https://github.com/lsst-ts/observatory-ops-docs>`_, making the desired changes and pushing them, making sure the build passes, then filing a pull request.
There are detailed instructions on how to complete these steps in the `Contributing to Observatory Operations Documentation <https://obs-ops.lsst.io/project/contributing.html#contributing-to-observatory-operations-documentation>`_ section of the webspace.



Obs-Controls Webspace
---------------------

The `Obs-Controls Webspace <https://obs-controls.lsst.io>`_ fulfils the same purpose as the `Obs-Ops Webspace`_, except it is focused on observatory control software.
This area is the first place to go when looking to learn more about the control system and how to use it.
SIT-Com users are encouraged to populate this page as well.
It is very common (and encouraged) to link content between this area and the `Obs-Ops Webspace`_.

The process to edit this webspace follows the same concept as the Obs-Ops Webspace.
The instructions are in the `Contributing to Observatory Controls Documentation <https://obs-controls.lsst.io/project/contributing.html#contributing-to-observatory-controls-documentation>`_

.. note::

   Details on writing and documenting control software code are found in the `TSSW Developer Guide <https://tssw-developer.lsst.io/>`_.
   For DM-centric code, follow the `DM Developer Guide <https://developer.lsst.io/>`_.
   Both guides are based upon the same principles and have significant overlap.



Docushare
^^^^^^^^^

Docushare is used heavily inside the project, particularly for vendor documentation, contract documents, and project level change controlled documentation.
SIT-Com has a `specific collection inside Docushare <https://docushare.lsst.org/docushare/dsweb/View/Collection-26>`_ that is available for use.
Note that as part of the project-wide documentation working group, the area will be re-structured.

.. Make in-text citations with: :cite:`bibkey`.
.. Uncomment to use citations
.. .. rubric:: References
.. 
.. .. bibliography:: local.bib lsstbib/books.bib lsstbib/lsst.bib lsstbib/lsst-dm.bib lsstbib/refs.bib lsstbib/refs_ads.bib
..    :style: lsst_aa
