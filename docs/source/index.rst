Using AIMS to Analyze Immune Repertoires
===================================


.. note::

   Unsure how others found this website, but it isn't ready just yet! Come back soon for a complete documentation of AIMS!

AIMS, an Automated Immune Molecule Separator, was originally developed to identify differences between two distinct immune repertoires, but has since expanded to become a multi-purpose repertoire analysis tool. Currently the AIMS analytical tools can be applied to immunoglobulin (Ig) molecules such as T cell receptors and antibodies, major histocompatibility complex (MHC) and MHC-like molecules, and immunopeptidomic data. This documentation will teach users how to use AIMS to:

- **Get started** following the :doc:`Installation` intstructions. If you're coming here from the GitHub page, hopefully you already done this.


- **Analyze repertoires with no programming experience required** in a user-friendly format with the :doc:`AIMS_GUI`.


- **Characterize the key features of immune repertoires** using the AIMS biophysical characterization tools through the :doc:`AIMS_basics` section. This biophysical characterization is the central feature of AIMS, taking :ref:`formatting` files and applying :ref:`core` for downstream manipulation.


- **Identify biophysically distinct repertoire clusters** within single repertoires or comparing across multiple repertoires using the :doc:`AIMS_cluster`.


- **Build off the AIMS analysis with your own custom features** by taking advantage of the :doc:`AIMS_notebooks`.

AIMS is a python package distributed in both a notebook and GUI format. Those wishing to use the GUI, particularly those relatively new to programming, can follow the installation instructions below. Example data is provided in AIMS/app/ab_testData and AIMS/app/mhc_testData, and an example of an application of AIMS can be seen in this peer-reviewed article: https://elifesciences.org/articles/61393
   
.. note::
   When publishing analysis from this software, please cite:

   Boughter CT, Borowska MT, Guthmiller JJ, Bendelac A, Wilson PC, Roux B, Adams EJ. Biochemical Patterns of Antibody Polyreactivity Revealed Through a Bioinformatics-Based Analysis of CDR Loops. eLife. 2020. DOI: 10.7554/eLife.61393

Contents
--------

.. toctree::

   AIMS_GUI
   AIMS_basics
   AIMS_cluster
   AIMS_notebooks
   
