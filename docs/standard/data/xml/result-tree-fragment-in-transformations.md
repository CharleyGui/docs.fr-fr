---
title: Fragment d’arborescence résultat dans Transformations
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: df363480-ba02-4233-9ddf-8434e421c4f1
ms.openlocfilehash: e454c1194e8c280042857f106e22d0d0509417e3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156359"
---
# <a name="result-tree-fragment-in-transformations"></a>Fragment d’arborescence résultat dans Transformations

> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez les pages [Utiliser la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migrer à partir de la classe XslTransform](migrating-from-the-xsltransform-class.md).

 Les fragments d'arborescence résultat ne sont rien d'autre qu'un type spécial de collection de nœuds. Vous pouvez effectuer sur ces collections toutes les fonctions pouvant être effectuées sur une collection de nœuds. Vous pouvez également convertir un fragment d’arborescence résultat en une collection de nœuds à l’aide la fonction `node-set()`, puis l’utiliser ensuite partout où il est possible d’utiliser une collection de nœuds.

 Un fragment d'arborescence résultat est créé suite à l'utilisation d'un élément `<xsl:variable>` ou `<xsl:param>` d'une manière spécifique dans une feuille de style. La syntaxe pour les éléments `variable` et `parameter` est la suivante :

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

Pour l'élément `parameter`, la valeur est assignée au nom qualifié (`Qname`) de plusieurs façons. Vous pouvez attribuer une valeur par défaut au paramètre en retournant du contenu de l’expression XPath (XML Path Language) dans l’attribut `select` ou en lui assignant le contenu du corps du modèle.

Pour l'élément `variable`, la valeur est également assignée de plusieurs façons. Vous pouvez l’attribuer en retournant du contenu de l’expression XPath dans l’attribut `select` ou en lui assignant le contenu du corps du modèle.

Pour les éléments `parameter` et `variable`, si une valeur est assignée par l’expression XPath, un des quatre types XPath de base sera retourné : booléen, chaîne, nombre ou collection de nœuds. Lorsque la valeur est fournie à l’aide d’un corps de modèle non vide, un type de données non XPath est retourné qui correspond à un fragment d’arborescence résultat.

Lorsqu'une variable est liée à un fragment d'arborescence résultat au lieu d'un des quatre types de données XPath de base, c'est la seule fois où une requête XPath retourne un type qui ne correspond pas à un des quatre types d'objet XPath. Les fragments d’arborescence résultat et leur comportement sont expliqués dans la [spécification du World Wide Web Consortium (W3C)](https://www.w3.org/TR/xslt-10/), de la [section 11.1 sur les fragments d’arborescence résultat](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) à la [section 11.6 sur le transfert des paramètres aux modèles](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates). De plus, la [section 1 Introduction](https://www.w3.org/TR/xslt-10/#section-Introduction) explique comment des modèles peuvent contenir des éléments provenant de l’espace de noms XSLT qui retournent ou créent des fragments d’arborescence résultat.

Un fragment d'arborescence résultat, en théorie, se comporte comme une collection de nœuds avec rien de plus qu'un nœud racine unique. Cependant, le reste des nœuds retournés sont des nœuds enfants. Pour voir les nœuds enfants par programme, copiez le fragment d’arborescence résultat dans l’arborescence résultat à l’aide de l’élément `<xsl:copy-of>`. Une fois la copie effectuée, tous les nœuds enfants sont copiés également dans l’arborescence résultat, les uns après les autres. Tant qu’un `copy` ou `copy-of` n’est pas utilisé, un fragment d’arborescence résultat ne fait pas partie de l’arborescence résultat ou de la sortie provenant de la transformation.

Pour itérer sur les nœuds retournés d'un fragment d'arborescence résultat, un objet <xref:System.Xml.XPath.XPathNavigator> est utilisé. L'exemple de code suivant montre comment créer un fragment d'arborescence résultat dans une feuille de style en appelant la fonction avec un paramètre `fragment` contenant XML.

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"
                xmlns:user="http://www.adventure-works.com"
                version="1.0">
    <xsl:var name="fragment">
        <node1>
            <node2/>
        </node1>
    <xsl:var>

  <msxsl:script language="C#" implements-prefix="user">
    function NodeFragment(XPathNavigator nav)
    {
      if (nav.HasSelection == false)
        XPathNavigator.MoveToNext();
      return;
    }
  </msxsl:script>

    <xsl:template match="/">
            <xsl:value-of select="user:NodeFragment(msxml:node-set($fragment))"/>
    </xsl:template>
</xsl:stylesheet>
```

Voici un autre exemple présentant une variable au format RTF, et donc un type de fragment d’arborescence résultat qui n’est pas converti en une collection de nœuds. Au lieu de cela, il est passé à une fonction de script et l'objet <xref:System.Xml.XPath.XPathNavigator> est utilisé pour naviguer sur les nœuds.

```xml
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"
        xmlns:user="urn:books"
        exclude-result-prefixes="msxsl">

<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>

<xsl:variable name="node-fragment">
    <book>Book1</book>
    <book>Book2</book>
    <book>Book3</book>
    <book>Book4</book>
</xsl:variable>

<msxsl:script implements-prefix="user" language="c#">

<![CDATA[
    string func(XPathNavigator nav)
    {
        bool b = nav.MoveToFirstChild();
        if (b)
            return nav.Value;
        else
            return "Does not exist";
    }

]]>

</msxsl:script>

<xsl:template match="/">
    <first_book>
        <xsl:value-of select="user:func($node-fragment)"/>
    </first_book>
</xsl:template>

</xsl:stylesheet>
```

Le résultat de la transformation du XML avec cette feuille de style est illustré dans la sortie suivante.

## <a name="output"></a>Sortie

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

Comme indiqué précédemment, la fonction `node-set` vous permet de convertir un fragment d’arborescence résultat en une collection de nœuds. Le nœud obtenu contient toujours un seul nœud qui représente le nœud racine de l’arborescence. Si vous convertissez un fragment d’arborescence résultat en une collection de nœuds, vous pouvez dès lors l’utiliser partout où un nœud régulier est utilisé, comme dans une instruction for-each ou dans la valeur d’un attribut `select`. Les lignes de code suivantes illustrent la conversion du fragment en une collection de nœuds et son utilisation comme une collection de nœuds :

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

Lorsqu'un fragment est converti en une collection de nœuds, vous n'utilisez plus l'objet <xref:System.Xml.XPath.XPathNavigator> pour naviguer sur celui-ci. Pour une collection de nœuds, vous utilisez plutôt l'objet <xref:System.Xml.XPath.XPathNodeIterator>.

Dans l'exemple suivant, `$var` est une variable qui est une arborescence de nœuds dans la feuille de style. L’instruction for-each associée à la fonction `node-set` permet à l’utilisateur d’itérer sur cette arborescence comme une collection de nœuds.

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"
                xmlns:user="http://www.adventure-works.com"
                version="1.0">
    <xsl:variable name="states">
        <node1>AL</node1>
        <node1>CA</node1>
        <node1>CO</node1>
        <node1>WA</node1>
    </xsl:variable>

    <xsl:template match="/">
            <xsl:for-each select="msxsl:node-set($states)"/>
    </xsl:template>
</xsl:stylesheet>
```

Voici un autre exemple d'une variable qui correspond à un RTF, et donc de fragment d'arborescence résultat type qui est converti en une collection de nœuds avant d'être passé à une fonction de script comme XPathNodeIterator.

```xml
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
        xmlns:msxsl="urn:schemas-microsoft-com:xslt"
        xmlns:user="urn:books"
        exclude-result-prefixes="msxsl">

<xsl:output method="xml" indent="yes" omit-xml-declaration="yes"/>

<xsl:variable name="node-fragment">
    <book>Book1</book>
    <book>Book2</book>
    <book>Book3</book>
    <book>Book4</book>
</xsl:variable>

<msxsl:script implements-prefix="user" language="c#">

<![CDATA[
    string func(XPathNodeIterator it)
    {
        it.MoveNext();
        return it.Current.Value;
        //it.Current returns XPathNavigator positioned on the current node
    }

]]>

</msxsl:script>
<xsl:template match="/">
    <books>
        <xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>
    </books>
</xsl:template>

</xsl:stylesheet>
```

Voici le résultat de la transformation du XML à l'aide de cette feuille de style :

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XPath.XPathNodeIterator>
- [Transformations XSLT avec la classe XslTransform](xslt-transformations-with-the-xsltransform-class.md)
- [Implémentation du processeur XSLT par la classe XslTransform](xsltransform-class-implements-the-xslt-processor.md)
