AIMS GUI Walkthrough
=====

This section will provide a step-by-step walkthrough outlining how to use the AIMS GUI. The focus will be primarily on how to interface with the GUI, how files are saved when using the GUI, and tips and tricks for a smooth AIMS experience. Before starting the GUI, you may want to check out the :doc:`AIMS_basics` and review the :ref:`formatting` and :ref:`core`. 

.. figure:: screenshots/0launch.png
   :alt: immuneML usage overview

.. _AIMSig:

Immunoglobulin Analysis with AIMS
------------
The AIMS analysis pipeline has been used to analyze a wide range of molecular species, including TCRs, antibodies, MHC molecules, MHC-like molecules, MHC-presented peptides, viral protein alignments, and evolutionarily conserved neuronal proteins. The GUI is currently only capable of analyzing these first four molecular species, with more analysis options hopefully available in the future. This section is specifically for the analysis of T cell receptors and antibodies. If you'd like to analyze MHC and MHC-like molecules, skip down to the :ref:`AIMSmhc` section.

**Step 1: Loading in Data**

Load in data on this screen, and determine how many distinct datasets you want to compare.

.. note::
   See ab_testData/ flu_poly.csv for formatting example

Once you click one of those dark gray “load” buttons, you should get a screen that looks like this:

.. figure:: screenshots/1Ig_compile.png
   :alt: immuneML usage overview

If following along with this walkthrough, select the "ab_testData" directory and load in poly_flu.csv and mono_flu.csv

**Step 2: Define Names and Outputs**

On this page, we define the folder outputs are saved to. This is pretty key in AIMS, as by default files are overwritten if the analysis is run multiple times. As such, each new analysis should have a new output folder, ideally with descriptive titles.

.. figure:: screenshots/2IgID.png
   :alt: immuneML usage overview

Below, we can change label names for each file loaded. Lastly, you must specify how many loops are in the files loaded in step1.

**Step 3: Generate the Sequence Matrix**

In this window, you can just click “get matrix” to generate the matrix for this step. This matrix must be generated for subsequent steps to function properly

.. figure:: screenshots/3Ig_compile.png
   :alt: immuneML usage overview

Congrats! You’ve generated your first piece of data using this software. You might notice that your image quality is poor for figures shown in the app, this is because the software shows *png files. Don’t worry, both versions of the plot are saved in whichever directory you specified in Step 2

**Step 4: Calculate Biophysical Properties**

Again, we simply press the “get properties” button. If a matrix was not generated in the previous window, then this step will fail. Don’t worry if this step takes a little while, especially for bigger data. The code needs a little work, but is accurate

.. figure:: screenshots/4IgPost.png
   :alt: immuneML usage overview

Again, if you’re following along, you should see this exact plot once the calculation finishes. Plotted are average and standard deviations of these normalized biophysical properties. Each sequence has one value for each of these properties. i.e. flu_poly_sequence1 has charge = -0.01, hydrophobicity = 0.05, etc. (values made up)

**Step 5: Define Which Files to Group and Plot**

In this step, you can really take some freedoms and play around. What we are doing here is telling the software which groups we want to feed into the PCA analysis
Then, in the ”Plotted Group” section, we are letting the software know which groups will be shown on the resultant plot. Even if a group was used in the analysis, it doesn’t need to be plotted (and vice versa)

.. figure:: screenshots/5Ig_compile.png
   :alt: immuneML usage overview

.. note:: 
   No options are given if only comparing two datasets. See MHC example for possibilities when there are three or more datasets.

**Step 6: Run and Plot PCA**

On this screen, we take the properties form step 4 and run a PCA on them
If you choose to exclude certain data from the PCA, but still plot it, then you are simply projecting that data onto the calculated principal component.

.. figure:: screenshots/6Ig_compile.png
   :alt: immuneML usage overview

Along with a plot of the first 3 PCs, we also report the explained variance of these PCs, and the top 10 weights that make up PC1.
A 2D plot is also included in the saved figures.

**Step 7: Define Binary Classes**

Here, we separate our loaded data into binary classes for some machine-learning based analysis.

**Step 8: Generate Position Sensitive Biophysical Properties**

Whereas the biophysical properties of step 4 are averaged across entire molecules, we can instead average across our full molecular population. By doing so, we can look at average biophysical properties as a function of sequence space, part of our special “positional encoding”

.. figure:: screenshots/8IgF.png
   :alt: immuneML usage overview

We only show charge and hydrophobicity, but position sensitive data for all 62 properties are saved in the same directory as pdf figures.

.. note::
   Standard deviations are not shown, and ideally these would be calculated via bootstrapping 

**Step 9: Linear Discriminant Analysis**

Unlike PCA, linear discriminant analysis (LDA) is designed to split binary classes of data

.. figure:: screenshots/9IgF.png
   :alt: immuneML usage overview

Effectively, we can use it to find where the strongest differences in the data are

**Step 10: Information Theory**

Something else here

.. figure:: screenshots/10IgF.png
   :alt: immuneML usage overview

**Step 11: Honestly I forget**

Something else here

.. figure:: screenshots/11IgF.png
   :alt: immuneML usage overview

**Step 12: Honestly I forget**

Something else here

.. figure:: screenshots/12IgF.png
   :alt: immuneML usage overview

**Step 13: Honestly I forget**

Something else here

.. figure:: screenshots/13IgF.png
   :alt: immuneML usage overview

**Step 14: Honestly I forget**

Something else here

.. figure:: screenshots/14Ig_compile.png
   :alt: immuneML usage overview

.. warning::
   Care must be taken not to overfit. If the number of input vctors is greater than the size of one of your datasets, you will overfit the data

For this example data, if we use 50 input vectors, we obtain a decent splitting of the data. The LD1 “names” and “weights” refer to the top ten weights that most strongly split the data. In other words, LDA tells you where the biggest differences are, positionally, in your dataset

.. _AIMSmhc:

MHC and MHC-Like Analysis with AIMS
------------
While a niche application of the software, AIMS readily extends to the analysis of any evolutionarily conserved molecules with specific regions of variability. MHC and MHC-like molecules fit very well into this category, and in the first published usage of AIMS, these moleclules were analyzed using the same tools as the immunoglobulin analysis. This section highlights the unique portions of the MHC analysis, and points out to where the analysis breaks down to become identical to the :ref:`AIMSig`.

**Step 1: Loading in Data**

FASTA files should be aligned sequences, with a minimum of 2 sequences per file, and a minimum of 2 FASTA files per program run. For the MHCs, formatting should just be in normal FASTA format. For following along with the analysis, load in “mhc_testData/“cd1_seqs.fasta”. 

**Step 2: Locate Helices and Strands**

So this is my least favorite part of the software, but it turns out this is the most efficient way to do things. Here, we explicitly say where in the alignments the strands/helices start. In an attempt to make this slightly less annoying, I’ve made it possible to create pre-formatted matrices for repeated analysis

For this example, from mhc_testData load in ex_cd1d_hla_uda_uaa_ji.csv. So for FASTA1, Strand 1 starts (S1s) at position 124, Strand 1 ends (S1e) at pos 167, Helix 1 starts (H1s) at this same position. And so on... Lastly, ”new_folder” is where output figures will be saved. Change this to whatever you want your folder name to be. Each run overwrites the figures, so maybe change to ”run1”, ”run2”, etc.

How do we locate helices and strands? NOTE, for this tutorial, this step has been done already
We first align molecules of interest within a single group
We then take a representative molecule (here human CD1d) and put it through our favorite structure prediction (Phyre, PsiPred, etc.)
When then go back and find where in the alignments a structural feature roughly begins
Here S1 starts at ”FPL” which occurs at alignment position 127. We add 3 amino acids of buffer space (optional, you can change this if you want) and you can see on the previous slide S1s = 124

Already figured out locations of Helices/Strands (based on provided FASTA files):
For the ji_cartFish we have: 2,49,93,152,193
For the cd1d_seqs.fasta we have: 124,167,209,262,303
For the hlaA_seqs.fasta we have: 170,218,260,306,348
For cd1_ufa_genes.fasta: 22,66,105,158,199
For UAA or UDA fasta: 2,49,93,152,193
In the future, I hope to identify these helices and strands automatically within the software, but I haven’t found anything suitable yet for doing so

**Step 3: Generate the Sequence Matrix**

On this window, you can just click “get matrix” to generate the matrix for this step. This matrix must be generated for subsequent steps to function properly

Congrats! You’ve generated your first piece of data using this software. You might notice that your image quality is poor for figures shown in the app, this is because the software shows *png files. Don’t worry, both versions of the plot are saved in whichever directory you specified in Step 2

**Step 4: Calculate Biophysical Properties**

Again, we simply press the “get properties” button. If a matrix was not generated in the previous window, then this step will fail. Don’t worry if this step takes a little while, especially for bigger data. The code needs a little work, but is accurate

Again, if you’re following along, you should see this exact plot once the calculation finishes. Plotted are average and standard deviations of these normalized biophysical properties. Each sequence has one value for each of these properties. i.e. flu_poly_sequence1 has charge = -0.01, hydrophobicity = 0.05, etc. (values made up)

**Step 5: Define Which Files to Group and Plot**

In this step, you can really take some freedoms and play around. What we are doing here is telling the software which groups we want to feed into the PCA analysis
Then, in the ”Plotted Group” section, we are letting the software know which groups will be shown on the resultant plot. Even if a group was used in the analysis, it doesn’t need to be plotted (and vice versa)

.. note:: 
   No options are given if only comparing two datasets. See MHC example for possibilities when there are three or more datasets.

**Step 6: Run and Plot PCA**

On this screen, we take the properties form step 4 and run a PCA on them
If you choose to exclude certain data from the PCA, but still plot it, then you are simply projecting that data onto the calculated principal component.

Along with a plot of the first 3 PCs, we also report the explained variance of these PCs, and the top 10 weights that make up PC1.
A 2D plot is also included in the saved figures.

**Step 7: Define Binary Classes**

Here, we separate our loaded data into binary classes for some machine-learning based analysis.

**Step 8: Generate Position Sensitive Biophysical Properties**

Whereas the biophysical properties of step 4 are averaged across entire molecules, we can instead average across our full molecular population. By doing so, we can look at average biophysical properties as a function of sequence space, part of our special “positional encoding”

We only show charge and hydrophobicity, but position sensitive data for all 62 properties are saved in the same directory as pdf figures.
.. note::
   Standard deviations are not shown, and ideally these would be calculated via bootstrapping 

**Step 9: Linear Discriminant Analysis**

Unlike PCA, linear discriminant analysis (LDA) is designed to split binary classes of data
Effectively, we can use it to find where the strongest differences in the data are

.. warning::
   Care must be taken not to overfit. If the number of input vctors is greater than the size of one of your datasets, you will overfit the data

For this example data, if we use 50 input vectors, we obtain a decent splitting of the data. The LD1 “names” and “weights” refer to the top ten weights that most strongly split the data. In other words, LDA tells you where the biggest differences are, positionally, in your dataset