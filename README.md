stopword-it
===========

Italian stop words file

The enable the stop words file in a solr configuration you should use something like this:

```
    <fieldType name="text" class="solr.TextField" positionIncrementGap="100">
      <analyzer type="index">
        <charFilter class="solr.HTMLStripCharFilterFactory"/>
        <tokenizer class="solr.WhitespaceTokenizerFactory" />

        <!-- Here it is possible to add more filters such as SynonymFilterFactory and StopFilterFactory,
             see http://wiki.apache.org/solr/AnalyzersTokenizersTokenFilters -->
        <filter class="solr.StopFilterFactory" words="stopwords.txt" ignoreCase="true"/>
        <filter class="solr.WordDelimiterFilterFactory" generateWordParts="1" generateNumberParts="1" catenateWords="1" catenateNumbers="1" catenateAll="0" splitOnCaseChange="1" />
        <filter class="solr.LowerCaseFilterFactory" />
        <!-- Here it is possible to add language analysis such as KeywordMarkerFilterFactory and SnowballPorterFilterFactory,
             see http://wiki.apache.org/solr/LanguageAnalysis -->
        <filter class="solr.SnowballPorterFilterFactory" language="Italian" />             
        <filter class="solr.RemoveDuplicatesTokenFilterFactory" />
      </analyzer>
      <analyzer type="query">
        <tokenizer class="solr.WhitespaceTokenizerFactory" />
        <!-- Here it is possible to add more filters such as SynonymFilterFactory and StopFilterFactory,
             see http://wiki.apache.org/solr/AnalyzersTokenizersTokenFilters -->
        <filter class="solr.StopFilterFactory" words="stopwords.txt" ignoreCase="true"/>
        <filter class="solr.WordDelimiterFilterFactory" generateWordParts="1" generateNumberParts="1" catenateWords="0" catenateNumbers="0" catenateAll="0" splitOnCaseChange="1" />
        <filter class="solr.LowerCaseFilterFactory" />
        <!-- Here it is possible to add language analysis such as KeywordMarkerFilterFactory and SnowballPorterFilterFactory,
             see http://wiki.apache.org/solr/LanguageAnalysis -->
        <filter class="solr.SnowballPorterFilterFactory" language="Italian" />             
        <filter class="solr.RemoveDuplicatesTokenFilterFactory" />
      </analyzer>
    </fieldType>
```

Please not the use of StopFilterFactory