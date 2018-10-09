# xml2json xslt
xml2json xslt will transform XML into JSON format.

This [blog post](http://www.bjelic.net/?p=1117) has more details.

## Running tests

In the command line, run npm to install the dependencies, and then run the tests.

```
npm install
npm test
```

//Todo: Add character escaping for 

```
    '\' escape
escape
    '"'
    '\'
    '/'
    'b'
    'n'
    'r'
    't'
    'u' hex hex hex hex
```
Reference method from: http://geekswithblogs.net/Erik/archive/2008/04/01/120915.aspx
```
 <xsl:template name="string-replace-all">
    <xsl:param name="text" />
    <xsl:param name="replace" />
    <xsl:param name="by" />
    <xsl:choose>
      <xsl:when test="contains($text, $replace)">
        <xsl:value-of select="substring-before($text,$replace)" />
        <xsl:value-of select="$by" />
        <xsl:call-template name="string-replace-all">
          <xsl:with-param name="text"
          select="substring-after($text,$replace)" />
          <xsl:with-param name="replace" select="$replace" />
          <xsl:with-param name="by" select="$by" />
        </xsl:call-template>
      </xsl:when>
      <xsl:otherwise>
        <xsl:value-of select="$text" />
      </xsl:otherwise>
    </xsl:choose>
  </xsl:template>
```
 
How it's called: 
```
  <xsl:variable name="myVar">
    <xsl:call-template name="string-replace-all">
      <xsl:with-param name="text" select="'This is a sample text : {ReplaceMe} and {ReplaceMe}'" />
      <xsl:with-param name="replace" select="'{ReplaceMe}'" />
      <xsl:with-param name="by" select="'String.Replace() in XSLT'" />
    </xsl:call-template>
  </xsl:variable>
```
