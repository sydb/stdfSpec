stdfSpec
===========

A proposal for a stand-off element for the [TEI Guidelines](http://www.tei-c.org/Guidelines/). This version is intended for Council to play with before we actually make a branch of the _Guidelines_ for the new element (currently called `&lt;standoff>`).

Basic idea
----------
Add a new stand-off element to `model.resourceLike` which can record
information/annotations about the present document or about external
documents. Also remove `&lt;teiCorpus>` and allow `&lt;TEI>` to nest.


Most important files
--------------------
The following is @laurentromary's original list — I have not yet updated (—@sydb).

* [`Specification/standoff-proposal.xml`](https://github.com/laurentromary/stdfSpec/blob/master/Specification/standoff-proposal.xml): 	The current proposal as ODD file. 
* [`Schemas/standoff-proposal.rnc`](https://github.com/laurentromary/stdfSpec/blob/master/Schemas/standoff-proposal.rnc):	The derived RelaxNG schema for testing with your TEI files 
* [`Samples/Test-stdf.xml`](https://github.com/laurentromary/stdfSpec/blob/master/Samples/Test-stdf.xml): A very basic example which should give you an idea of the proposed new elements
* [`Samples/SampleMAFstdf.xml`](https://github.com/laurentromary/stdfSpec/blob/master/Samples/SampleMAFstdf.xml): A test file with morphosyntactic annotations
* [`Samples/TEISpeech-stdf/HelgeSchneider_ISO_TEI_TCF_WebLichtResult_MERGED_2.tei`](https://github.com/laurentromary/stdfSpec/blob/master/Samples/TEISpeech-stdf/HelgeSchneider_ISO_TEI_TCF_WebLichtResult_MERGED_2.tei): An elaborate 'real world' example taken and transformed from the [EXMARaLDA-Demokorpus](http://exmaralda.org/en/exmaralda-demo-corpus/)
* [`Samples/WeGA-A040296.xml`](https://github.com/laurentromary/stdfSpec/blob/master/Samples/WeGA-A040296.xml): Not truly standoff, but a possible use case for externalizing all sorts of lists that are currently to be found within sourceDesc or profileDesc


License
-------

This work is available under dual license: [BSD 2-Clause](http://opensource.org/licenses/BSD-2-Clause) and [Creative Commons Attribution 3.0 Unported License (CC BY 3.0)](http://creativecommons.org/licenses/by/3.0/)
