---
section: Schema
name: pbcoreRelationType
attributes:
  - name: source
    note: optional
  - name: ref
    note: optional
  - name: version
    note: optional
  - name: annotation
    note: optional
controlled-vocabs:
  - vocab: <a href="/pbcore-controlled-vocabularies/pbcorerelationtype-vocabulary/">PBCore's Relation Type Vocabulary</a>
  - vocab: <a href="http://dublincore.org/documents/1999/04/29/rdf-relation-types/">Dublin Core RDF Schema Declaration of Relation Types</a>
---
<pre>
  <code>
  &lt;pbcoreRelation&gt;<br>
      &lt;pbcoreRelationType source=&quot;pbcoreRelationType Vocabulary&quot; ref=&quot;http://pbcore.org/pbcore-controlled-vocabularies/pbcorerelationtype-vocabulary/#IsPartOf&quot;&gt;Is Part Of&lt;/pbcoreRelationType&gt;<br>
      &lt;pbcoreRelationIdentifier&gt;NOVA&lt;/pbcoreRelationIdentifier&gt;<br>
  &lt;/pbcoreRelation&gt;
  </code>
</pre>
