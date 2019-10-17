# stdfSpec ODD specification and outputs thereof

This directory contains the actual ODD customization for the stand-off specification proposal. It also contains some of the derived outputs thereof, and the TEI customization schema just to make it easier to write the ODD itself. (An invalidity of the ODD against tei_customiztion is not necessarily an error.)

### Default Text Structure

Current structure of a TEI document is:

~~~~~
  start = TEI | teiCorpus
  TEI = teiHeader, model.resourceLike+
  teiCorpus = teiHeader, ( model.resourceLike*, ( TEI | teiCorpus )* )  [1]
  model.resourceLike = \text | facsimile | fsdDecl | sourceDoc
~~~~~

What @laurentromary asked for is exactly the same, except 1 change:
  * add `<standOff>` to model.resourceLike

HOWEVER, he also asked that the `<standOff>` element have `<teiHeader>` as a child:

~~~~~
  standOff = teiHeader?, model.resourceLike*, listAnnotation*
~~~~~  

This is because he wants the document used for stand off annotations to also stand on its own. We (Council) really really did not like the idea of allowing `<teiHeader>` (and other model.resourceLike elements) as a child (or children) of `<standOff>`. Thus my proposed new structure for a TEI document is:

~~~~~
  start = TEI
  TEI = teiHeader, ( model.resourceLike*, TEI* )  [2]
  model.resourceLike = \text | facsimile | fsdDecl | standoff | sourceDoc
~~~~~
This allows an `<standoff>` to be associated very closely with a `<teiHeader>` (by being wrapped in a `<TEI>`) whether it is a document of its own or a child of another `<TEI>` document.

That said, I could understand the argument that “a `<TEI>` is just a resource, albeit one with metadata associated; thus `<TEI>` should just be in model.resourceLike”. This makes for very simple content models: 

~~~~~
  start = TEI
  TEI = teiHeader, model.resourceLike+
  model.resourceLike = TEI | \text | facsimile | fsdDecl | standoff | sourceDoc
~~~~~
That’s good, but it also allows some new weird things (in addition to the weird things we already allow but probably shouldn’t), in particular `<TEI>` elements in between other resource thingies:

~~~~~xml
<TEI>
  <teiHeader><!-- ... --></teiHeader>
  <facsimile><!-- ... --></facsimile>
  <TEI>
    <teiHeader><!-- ... --></teiHeader>
    <sourceDoc><!-- ... --></sourceDoc>
    <standoff><!-- ... --></standoff>
  </TEI>
  <fsdDecl><!-- ... --></fsdDecl>
  <text><!-- ... --></text>
  <text><!-- ... --></text>
  <standoff><!-- ... --></standoff>
  <TEI>
    <teiHeader><!-- ... --></teiHeader>
    <text><!-- ... --></text>
  </TEI>
</TEI>
~~~~~

#### Notes

[1] This is a simplification of the actual content model, which actually requires that you have at least one child of `<teiCorpus>`: either one element from model.resourceLike or a `<TEI>` or a `<teiCorpus>`.
 
 [2] This is a simplification of the actual content model, which requires that you have at least one child of `<TEI>`, either one element from model.resourceLike or a `<TEI>`.
