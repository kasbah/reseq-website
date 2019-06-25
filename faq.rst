.. -*- coding: utf-8 -*-

.. this is meant to be reStructuredText. I’m just copying
   http://docutils.sourceforge.net/FAQ.txt


===========================================
 ReSeq FAQ (Frequently Asked Questions)
===========================================


.. contents::
.. sectnum::

About/Funding
=============


Who is involved and where will the money go?
---------------------------------------------

We are open source hardware and software developers from a variety of backgrounds. Some of us are actively involved in related organisations such as Hackteria and GOSH (see below) while others work in the research sector. Our motivation for doing this project are along the lines of those described by `this author`_.

The money will pay for some software developer time plus a small amount for travel and materials.

UPDATE 25th June: You can track `our spending here`_.

.. _this author: https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.3000014
.. _our spending here: https://github.com/kasbah/reseq-website/blob/master/balance.csv

What is Hackteria?
------------------

`Hackteria`_ is a global network of people practicing DIY (do-it-yourself) biology with an interest in art, design and interdisciplinary cooperation. As a community platform hackteria.org tries to encourage the collaboration of scientists, hackers and artists to combine their expertise, write critical and theoretical reflections, share simple instructions to work with life-science technologies and cooperate on the organization of workshops, temporary labs, hack-sprints and meetings.


.. _Hackteria: https://www.hackteria.org/


What is GOSH?
-------------

`GOSH`_ is a global open science hardware movement. The GOSH Gathering for Open Science Hardware serves the needs of the global Open Science Hardware community through convening meetings, publications, activities and providing a forum for the community.


.. _GOSH: http://openhardware.science/


Why are you using wemakeit?
---------------------------

Both the project and wemakeit.com are based in Switzerland. Furthermore, by using wemakeit.com we are eligible for the `Science Booster`_ scheme which matches our target amount dollar-for-dollar if we are successful.

.. _Science Booster: https://wemakeit.com/pages/science

Aside from donating money, how can I help?
------------------------------------------

Any involvement would be appreciated, whether that be donating time to work on the code and documentation or joining the mailing list and sharing left-over reagents and old flow cells, knowledge, hiseqs, parts, space, ideas… The idea is to build some community around the project to make it as easy as possible for those who are interested to obtain instruments and re-use them in new and interesting ways.

Is it legal to reverse engineer and hack proprietary hardware?
--------------------------------------------------------------

I have found nothing to indicate that tear downs are illegal and by my reading of `this FAQ`_ the reversing is not illegal either. Specifically, we haven’t needed to dig inside or disassemble any firmware or proprietary software. It was sufficient just to monitor the serial ports. The documentation for all the API’s and hardware that we relied on were freely available for download from the individual component manufacturers.

.. _this FAQ: https://www.eff.org/issues/coders/reverse-engineering-faq

Hardware
========

I have been offered a HiSeq but it looks very big. How do I move it?
--------------------------------------------------------------------

This is the dimensions and weight of a later model HiSeq:
W×D×H: 118.6 cm × 76.0 cm × 94.0 cm (46.7 in × 30.0 in × 37.0 in)
Weight: 221.4 kg (488 lbs)

Putting it on a pallet and using a palette trolley is probably the easiest way. Most of the outer panels come of easily and doing so will reduce the dimensions and weight slightly. If you are using 6 people to lift it then it also exposes some useful places for them to hold it.


I have a HiSeq, but I think X might be broken. How can I test it?
-----------------------------------------------------------------

Time permitting, we will write MM a test script to report on all the hardware. The Illumina software also reports some diagnostics.


Is it possible to split them in half to make them more manageable?
------------------------------------------------------------------

If you’re just after the microscope then yes, although in order to do away with the water cooling you need to fit air-cooled heat sinks to the cameras. Otherwise the large number of connections make it fiddly.


Will this software damage my machine?
--------------------------------------

It's very unlikely. We will be thoroughly testing our software on real machines before making any release but, as with all open source software, we include a disclaimer that we are not liable for any damage caused by people making use of it.

Installing our software will leave the existing Illumina installation untouched so that you can still run either software at your leisure.


Software
========

Will I have to change anything to run your software?
----------------------------------------------------

No. You will just need to install Micro-Manager and then copy the DLLs for the DeviceAdapters, Plugins and scripts to the appropriate directories.

Do you require any of the original Illumina installation?
---------------------------------------------------------

No, the camera and frame grabber drivers (a.k.a DCAM API) do need to be present but these can also be obtained `from the Hamamatsu website`_.

.. _`from the Hamamatsu website`: https://dcam-api.com/downloads/


Do you have drivers/documentation for X?
----------------------------------------

We have pretty much all the publicly-available drivers and documentation and can probably point you in the right direction. One notable exception are the Linux drivers for the camera and frame grabber. We have contacted several people in Hamamatsu without success. If you can help us out, please get in touch, we would love to hear from you! This is all that is preventing us from compiling and releasing a Linux version.

Will your software support this assay that I have in mind?
----------------------------------------------------------

Depending on what it is, it will require a plugin or script to be written. Having said that, we are open to offers.


Biology
=======

Will my HiSeq still work with Illumina reagents?
------------------------------------------------

Yes, if you can get them. Illumina say `here`_ that they will support the HiSeq 2500 System until 2/2023.
“The HiSeq 2500 System has been obsolesced. We intend to continue to provide full support of the instrument and supply the reagents through February 28th, 2023.”

.. _here: https://sapac.illumina.com/systems/sequencing-platforms/hiseq-2500/specifications.html


Will you be supporting DIY reagents and flow cells?
---------------------------------------------------

At this point our focus is on creating open software underpinnings that will enable the instruments to be re-used. Reading `this`_ makes me think that it should, in theory, be possible to recondition and re-use the flow cells but that is beyond our scope and expertise.

.. _this: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5975494/


What are these other assays that you speak of?
----------------------------------------------

People have already implemented assays to look at binding affinity to double-stranded DNA. `This paper`_ used the clusters on a previously-sequenced flow cell to characterise dCas9 off-target binding to sequences similar to the target. Another possible use would be to use the flow cell to implement an assay measure molecule abundance similar to how `this instrument measures RNA expression`.

Here are some other papers:

* Boyle, E. A. et al. Proc. Natl Acad. Sci. USA 114, 5461-5466 (2017). High-throughput biochemical profiling reveals sequence determinants of dCas9 off-target binding and unbinding. PMID: `28495970`_
* Buenrostro, J. D., Giresi, P. G., Zaba, L.C., Chang H. Y. & Greenleaf, W. J. Nature Meth. 10, 1213-1218 (2013). Transposition of native chromatin for fast and sensitive epigenomic profiling of open chromatin, DNA-binding proteins and nucleosome position. PMCID: `3959825`_
* Buenrostro, J. et al. Nature Biotechnol. 32, 562-568 (2014). Quantitative analysis of RNA-protein interactions on a massively parallel array reveals Biophysical and evolutionary landscapes. PMID: `24727714`_
* Jung, C. et al. Cell 170, 35-47 (2017). Massively Parallel Biophysical Analysis of CRISPR-Cas Complexes on Next Generation Sequencing Chips. PMID:`28666121`_
* Layton, C. J., McMahon, P. L. & Greenleaf, W. J. Preprint at bioRxiv https://doi.org/10.1101/342808 (2018). Large-scale, quantitative protein assays on a high-throughput DNA sequencing chip. biorxiv: `342808v4`_
* Nutiu, R. et al. Nature Biotechnol. 29, 659-664 (2011). Direct measurement of DNA affinity landscapes on a high-throughput sequencing instrument. PMID: `21706015`_
* Subtelny, A. O., Eichhorn, S. W., Chen, G. R., Sive, H. & Bartel, D. P. Nature 508, 66-71 (2014). Poly(A)-tail profiling reveals an embryonic switch in translational control. PMID: `24476825`_
* Svensen, N., Peersen, O. B. & Jaffrey, S. R. ChemBioChem 17, 1628-1635 (2016). Peptide Synthesis on a Next-Generation DNA Sequencing Platform. PMID: `27385640`_
* Sweeney, T. E., Braviak, L., Tato, C. M. & Khatri, P. Lancet Respir. Med. 4, 213-224 (2016). Genome-wide expression for diagnosis of pulmonary tuberculosis: a multicohort analysis. PMID: `26907218`_

.. _28495970: https://www.ncbi.nlm.nih.gov/pubmed/28495970
.. _3959825: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3959825
.. _24727714: https://www.ncbi.nlm.nih.gov/pubmed/24727714
.. _28666121: https://www.ncbi.nlm.nih.gov/pubmed/28666121
.. _342808v4: https://www.biorxiv.org/content/10.1101/342808v4
.. _21706015: https://www.ncbi.nlm.nih.gov/pubmed/21706015
.. _24476825: https://www.ncbi.nlm.nih.gov/pubmed/24476825
.. _27385640: https://www.ncbi.nlm.nih.gov/pubmed/27385640
.. _26907218: https://www.ncbi.nlm.nih.gov/pubmed/26907218



.. _This paper: https://www.pnas.org/content/114/21/5461

.. _this instrument measures rna expression: https://www.nanostring.com/scientific-content/technology-overview/ncounter-technology
