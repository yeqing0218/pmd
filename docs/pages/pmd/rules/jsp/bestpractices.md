---
title: Best Practices
summary: Rules which enforce generally accepted best practices.
permalink: pmd_rules_jsp_bestpractices.html
folder: pmd/rules/jsp
sidebaractiveurl: /pmd_rules_jsp.html
editmepath: ../pmd-jsp/src/main/resources/category/jsp/bestpractices.xml
keywords: Best Practices, DontNestJsfInJstlIteration, NoClassAttribute, NoHtmlComments, NoJspForward
language: Java Server Pages
---
## DontNestJsfInJstlIteration

**Since:** PMD 3.6

**Priority:** Medium (3)

Do not nest JSF component custom actions inside a custom action that iterates over its body.

**This rule is defined by the following XPath expression:**
```
//Element[ @Name="c:forEach" ] // Element[ @NamespacePrefix="h" or @NamespacePrefix="f" ]
```

**Example(s):**

``` jsp
<html>
  <body>
    <ul>
      <c:forEach items='${books}' var='b'>
        <li> <h:outputText value='#{b}' /> </li>
      </c:forEach>
    </ul>
  </body>
</html>
```

**Use this rule by referencing it:**
``` xml
<rule ref="category/jsp/bestpractices.xml/DontNestJsfInJstlIteration" />
```

## NoClassAttribute

**Since:** PMD 3.6

**Priority:** Medium High (2)

Do not use an attribute called 'class'. Use "styleclass" for CSS styles.

**This rule is defined by the following XPath expression:**
```
//Attribute[ upper-case(@Name)="CLASS" ]
```

**Example(s):**

``` jsp
<HTML> <BODY>
<P class="MajorHeading">Some text</P>
</BODY> </HTML>
```

**Use this rule by referencing it:**
``` xml
<rule ref="category/jsp/bestpractices.xml/NoClassAttribute" />
```

## NoHtmlComments

**Since:** PMD 3.6

**Priority:** Medium High (2)

In a production system, HTML comments increase the payload
between the application server to the client, and serve
little other purpose. Consider switching to JSP comments.

**This rule is defined by the following XPath expression:**
```
//CommentTag
```

**Example(s):**

``` jsp
<HTML><title>bad example><BODY>
<!-- HTML comment -->
</BODY> </HTML>

<HTML><title>good example><BODY>
<%-- JSP comment --%>
</BODY> </HTML>
```

**Use this rule by referencing it:**
``` xml
<rule ref="category/jsp/bestpractices.xml/NoHtmlComments" />
```

## NoJspForward

**Since:** PMD 3.6

**Priority:** Medium (3)

Do not do a forward from within a JSP file.

**This rule is defined by the following XPath expression:**
```
//Element[ @Name="jsp:forward" ]
```

**Example(s):**

``` jsp
<jsp:forward page='UnderConstruction.jsp'/>
```

**Use this rule by referencing it:**
``` xml
<rule ref="category/jsp/bestpractices.xml/NoJspForward" />
```

