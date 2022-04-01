AIMS Basics
=====

In this section, we will focus on the absolute basics that you need to know about while running AIMS. This includes the :ref:`formatting` of the files used for the analysis, the :ref:`core` of the software, and the :ref:`bphysProp` that are the central pillars of the analysis. This information is key whether users are interested in working with the AIMS GUI or with the AIMS Jupyter Notebooks. The hope is that if there are any fundamental questions with the meaning of a given output, or necessary troubleshooting with inputs, the users can find them here.

.. _formatting:

Input Formatting
------------

At present, the AIMS software requires a specific input formatting to be read by the software. Future versions of the software will hopefully have more relaxed formatting requirements, assuming users request such functionality. Here we will go into specifics for each molecular species, but the general format maintained for all species involves a comma separated value (CSV) file with a header in the first row, and no associated metadata in the given file.

**Immunoglobulin (TCR/Ab) Formatting**

.. code-block:: python
    
    l1,l2,l3,h1,h2,h3
    QSISSY,DAS,QHRSTWPPN,GGTFSSRA,IIPIFNTP,AREMATIFGRMDV
    ESLLHSDGKTY,EVS,MQTIQLPGT,GGIMRRNG,IIAIFGTP,VASSGYHLHRETWGY
    QDIKNY,HVS,HQCYNLPYT,GFIFGHFA,ISGGGLNT,ARFDSSGYNYVRGMVV

**MHC/MHC-Like Formatting**

.. code-block:: python
    
    >3VJ6_A Chain A, H-2 Class I Histocompatibility Antigen, D-37 Alpha Chain [Mus musculus]
    ------------------------------------------------------------
    ------------------------------------------------------------
    -------------------------------------------------SPHSLRYFTTA
    VSRPGLGEPRFIIVGYVDDTQFVRFDSDAENPRMEPRARWIEQEGPEYWERETWKAR
    DMGRNFRVNLRTLLGYYNQSNDESHTLQWMYGCDVGPDGRLLRGYCQEAYDGQDYISLNE
    DLRSWTANDIASQISKHKSEAVDEAH-QQRAYLQGPCVEWLHRYLRLGNETLQRSDPPKA
    HVTHHPRSEDEVTLRCWALGFYPADITLTWQLNGEELTQDMELVETRPAGDGTFQKWAAV
    VVPLGKEQYYTCHVYHEGLPEPLTLRWEPP------------------------------
    -------------------------------------------------
    >5VCL_A Chain A, H2-t23 Protein [Mus musculus]
    ------------------------------------------------------------
    ------------------------------------------------------------
    ------------------------------------------------MSSHSLRYFHTA

**Immunopeptidomics Formatting**

.. code-block:: python
    
    pep_input
    APATPAVVL
    PSPEAAVAV
    VALGGPHDP
    PAALPVPSL
    PTAPVTPSI
    CPGASQPIL
    DRGSCGVTV
    .
    .
    .


**Multi-Sequence Alignment Formatting**

.. code-block:: python
    
    Dpr,Sequence
    Dpr1,DKDVSWIRKRDLHILTAGGTTYTSD-----QINTEPKMSLSYTFNVVEL
    Dpr2,DKSVSWIRKRDLHILTAGILTYTSD-----QVNTEPKISMAFRLNVIVT
    Dpr3,DKSVSWIRKRDLHILTVGTATYTSD-----QVNTEPKMSMAFQLNIIEI

**Common Error-Inducing Features**

.. _core:

Core Functionalities
------------

Go into the fundamentals of AIMS. What are the goals? How does it work? Maybe link out to other sections for deeper dives. Have a separate "the fundamentals" large section

.. _bphysProp:

Biophysical Properties
------------

Need to take the table from the eLife paper and put it here for easier reference.