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
# <a name="result-tree-fragment-in-transformations"></a><span data-ttu-id="18058-102">Fragment d’arborescence résultat dans Transformations</span><span class="sxs-lookup"><span data-stu-id="18058-102">Result Tree Fragment in Transformations</span></span>

> [!NOTE]
> <span data-ttu-id="18058-103">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="18058-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="18058-104">Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="18058-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="18058-105">Pour plus d'informations, consultez les pages [Utiliser la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migrer à partir de la classe XslTransform](migrating-from-the-xsltransform-class.md).</span><span class="sxs-lookup"><span data-stu-id="18058-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

 <span data-ttu-id="18058-106">Les fragments d'arborescence résultat ne sont rien d'autre qu'un type spécial de collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="18058-106">Result tree fragments, also known as result tree fragments, are nothing more than a special type of node set.</span></span> <span data-ttu-id="18058-107">Vous pouvez effectuer sur ces collections toutes les fonctions pouvant être effectuées sur une collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="18058-107">You can perform any function on them that can be performed on a node set.</span></span> <span data-ttu-id="18058-108">Vous pouvez également convertir un fragment d’arborescence résultat en une collection de nœuds à l’aide la fonction `node-set()`, puis l’utiliser ensuite partout où il est possible d’utiliser une collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="18058-108">Or, you can also convert a result tree fragment to a node set using the `node-set()` function and subsequently use it any place that a node set can be used.</span></span>

 <span data-ttu-id="18058-109">Un fragment d'arborescence résultat est créé suite à l'utilisation d'un élément `<xsl:variable>` ou `<xsl:param>` d'une manière spécifique dans une feuille de style.</span><span class="sxs-lookup"><span data-stu-id="18058-109">A result tree fragment is created as a result of using an `<xsl:variable>` or `<xsl:param>` element in a specific manner in a style sheet.</span></span> <span data-ttu-id="18058-110">La syntaxe pour les éléments `variable` et `parameter` est la suivante :</span><span class="sxs-lookup"><span data-stu-id="18058-110">The syntax for the `variable` and `parameter` elements is as follows:</span></span>

```xml
<xsl:param name=Qname select= XPath Expression >
    template body
</xsl:param>

<xsl:variable name=Qname select=XPath Expression >
    template body
</xsl:variable>
```

<span data-ttu-id="18058-111">Pour l'élément `parameter`, la valeur est assignée au nom qualifié (`Qname`) de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="18058-111">For the `parameter` element, the value is assigned to the qualified name (`Qname`) in several ways.</span></span> <span data-ttu-id="18058-112">Vous pouvez attribuer une valeur par défaut au paramètre en retournant du contenu de l’expression XPath (XML Path Language) dans l’attribut `select` ou en lui assignant le contenu du corps du modèle.</span><span class="sxs-lookup"><span data-stu-id="18058-112">You can assign a default value to the parameter by returning content from the XML Path Language (XPath) expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>

<span data-ttu-id="18058-113">Pour l'élément `variable`, la valeur est également assignée de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="18058-113">For the `variable` element, the value is also assigned in several ways.</span></span> <span data-ttu-id="18058-114">Vous pouvez l’attribuer en retournant du contenu de l’expression XPath dans l’attribut `select` ou en lui assignant le contenu du corps du modèle.</span><span class="sxs-lookup"><span data-stu-id="18058-114">You can assign it by returning content from the XPath expression in the `select` attribute, or by assigning it the contents of the template body.</span></span>

<span data-ttu-id="18058-115">Pour les éléments `parameter` et `variable`, si une valeur est assignée par l’expression XPath, un des quatre types XPath de base sera retourné : booléen, chaîne, nombre ou collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="18058-115">For both the `parameter` and `variable` elements, if a value is assigned by the XPath expression, then one of the four basic XPath types will be returned: Boolean, string, number, or node set.</span></span> <span data-ttu-id="18058-116">Lorsque la valeur est fournie à l’aide d’un corps de modèle non vide, un type de données non XPath est retourné qui correspond à un fragment d’arborescence résultat.</span><span class="sxs-lookup"><span data-stu-id="18058-116">When the value is given by using a non-empty template body, then a non-XPath data type is returned, and that will be a result tree fragment.</span></span>

<span data-ttu-id="18058-117">Lorsqu'une variable est liée à un fragment d'arborescence résultat au lieu d'un des quatre types de données XPath de base, c'est la seule fois où une requête XPath retourne un type qui ne correspond pas à un des quatre types d'objet XPath.</span><span class="sxs-lookup"><span data-stu-id="18058-117">When a variable is bound to a result tree fragment instead of one of the four basic XPath data types, this is the only time that an XPath query returns a type that is not one of the four XPath object types.</span></span> <span data-ttu-id="18058-118">Les fragments d’arborescence résultat et leur comportement sont expliqués dans la [spécification du World Wide Web Consortium (W3C)](https://www.w3.org/TR/xslt-10/), de la [section 11.1 sur les fragments d’arborescence résultat](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) à la [section 11.6 sur le transfert des paramètres aux modèles](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates).</span><span class="sxs-lookup"><span data-stu-id="18058-118">Result tree fragments and their behavior are discussed in the [World Wide Web Consortium (W3C) specification](https://www.w3.org/TR/xslt-10/), [section 11.1 Result Tree Fragments](https://www.w3.org/TR/xslt-10/#section-Result-Tree-Fragments) through [section 11.6 Passing Parameters to Templates](https://www.w3.org/TR/xslt-10/#section-Passing-Parameters-to-Templates).</span></span> <span data-ttu-id="18058-119">De plus, la [section 1 Introduction](https://www.w3.org/TR/xslt-10/#section-Introduction) explique comment des modèles peuvent contenir des éléments provenant de l’espace de noms XSLT qui retournent ou créent des fragments d’arborescence résultat.</span><span class="sxs-lookup"><span data-stu-id="18058-119">Also, [section 1 Introduction](https://www.w3.org/TR/xslt-10/#section-Introduction) discusses how templates can contain elements from the XSLT namespace that return or create result tree fragments.</span></span>

<span data-ttu-id="18058-120">Un fragment d'arborescence résultat, en théorie, se comporte comme une collection de nœuds avec rien de plus qu'un nœud racine unique.</span><span class="sxs-lookup"><span data-stu-id="18058-120">A result tree fragment, in concept, behaves like a node set with nothing more than a single root node.</span></span> <span data-ttu-id="18058-121">Cependant, le reste des nœuds retournés sont des nœuds enfants.</span><span class="sxs-lookup"><span data-stu-id="18058-121">However, the rest of the nodes returned are child nodes.</span></span> <span data-ttu-id="18058-122">Pour voir les nœuds enfants par programme, copiez le fragment d’arborescence résultat dans l’arborescence résultat à l’aide de l’élément `<xsl:copy-of>`.</span><span class="sxs-lookup"><span data-stu-id="18058-122">To programmatically see the child nodes, copy the result tree fragment to the result tree using the `<xsl:copy-of>` element.</span></span> <span data-ttu-id="18058-123">Une fois la copie effectuée, tous les nœuds enfants sont copiés également dans l’arborescence résultat, les uns après les autres.</span><span class="sxs-lookup"><span data-stu-id="18058-123">When the copy-of is performed, all the child nodes are also copied to the result tree in sequence.</span></span> <span data-ttu-id="18058-124">Tant qu’un `copy` ou `copy-of` n’est pas utilisé, un fragment d’arborescence résultat ne fait pas partie de l’arborescence résultat ou de la sortie provenant de la transformation.</span><span class="sxs-lookup"><span data-stu-id="18058-124">Until a `copy` or `copy-of` is used, a result tree fragment is not part of the result tree or the output from the transformation.</span></span>

<span data-ttu-id="18058-125">Pour itérer sur les nœuds retournés d'un fragment d'arborescence résultat, un objet <xref:System.Xml.XPath.XPathNavigator> est utilisé.</span><span class="sxs-lookup"><span data-stu-id="18058-125">To iterate over the returned nodes of a result tree fragment, an <xref:System.Xml.XPath.XPathNavigator> is used.</span></span> <span data-ttu-id="18058-126">L'exemple de code suivant montre comment créer un fragment d'arborescence résultat dans une feuille de style en appelant la fonction avec un paramètre `fragment` contenant XML.</span><span class="sxs-lookup"><span data-stu-id="18058-126">The following code sample shows how to create a result tree fragment within a style sheet by calling the function with a parameter `fragment`, which contains XML.</span></span>

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

<span data-ttu-id="18058-127">Voici un autre exemple présentant une variable au format RTF, et donc un type de fragment d’arborescence résultat qui n’est pas converti en une collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="18058-127">Here is another sample showing a variable, which is in Rich Text Format (RTF), and hence, a type of result tree fragment, that is not converted to a node set.</span></span> <span data-ttu-id="18058-128">Au lieu de cela, il est passé à une fonction de script et l'objet <xref:System.Xml.XPath.XPathNavigator> est utilisé pour naviguer sur les nœuds.</span><span class="sxs-lookup"><span data-stu-id="18058-128">Instead, it is passed to a script function, and the <xref:System.Xml.XPath.XPathNavigator> is used to navigate over the nodes.</span></span>

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

<span data-ttu-id="18058-129">Le résultat de la transformation du XML avec cette feuille de style est illustré dans la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="18058-129">The result of transforming any XML with this style sheet is shown in the following output.</span></span>

## <a name="output"></a><span data-ttu-id="18058-130">Sortie</span><span class="sxs-lookup"><span data-stu-id="18058-130">Output</span></span>

```xml
<first_book xmlns:user="urn:books">Book1</first_book>
```

<span data-ttu-id="18058-131">Comme indiqué précédemment, la fonction `node-set` vous permet de convertir un fragment d’arborescence résultat en une collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="18058-131">As stated above, the `node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="18058-132">Le nœud obtenu contient toujours un seul nœud qui représente le nœud racine de l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="18058-132">The resulting node always contains a single node that is the root node of the tree.</span></span> <span data-ttu-id="18058-133">Si vous convertissez un fragment d’arborescence résultat en une collection de nœuds, vous pouvez dès lors l’utiliser partout où un nœud régulier est utilisé, comme dans une instruction for-each ou dans la valeur d’un attribut `select`.</span><span class="sxs-lookup"><span data-stu-id="18058-133">If you convert a result tree fragment to a node set, then you can use it anywhere a regular node set is used, such as in a for-each statement or in the value of a `select` attribute.</span></span> <span data-ttu-id="18058-134">Les lignes de code suivantes illustrent la conversion du fragment en une collection de nœuds et son utilisation comme une collection de nœuds :</span><span class="sxs-lookup"><span data-stu-id="18058-134">The following lines of code show the fragment being converted to a node set and used as a node set:</span></span>

`<xsl:for-each select="msxsl:node-set($node-fragment)">`

`<xsl:value-of select="user:func(msxsl:node-set($node-fragment))"/>`

<span data-ttu-id="18058-135">Lorsqu'un fragment est converti en une collection de nœuds, vous n'utilisez plus l'objet <xref:System.Xml.XPath.XPathNavigator> pour naviguer sur celui-ci.</span><span class="sxs-lookup"><span data-stu-id="18058-135">When a fragment is converted to a node set, you no longer use the <xref:System.Xml.XPath.XPathNavigator> to navigate over it.</span></span> <span data-ttu-id="18058-136">Pour une collection de nœuds, vous utilisez plutôt l'objet <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="18058-136">For a node set, you use the <xref:System.Xml.XPath.XPathNodeIterator> instead.</span></span>

<span data-ttu-id="18058-137">Dans l'exemple suivant, `$var` est une variable qui est une arborescence de nœuds dans la feuille de style.</span><span class="sxs-lookup"><span data-stu-id="18058-137">In the following example, `$var` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="18058-138">L’instruction for-each associée à la fonction `node-set` permet à l’utilisateur d’itérer sur cette arborescence comme une collection de nœuds.</span><span class="sxs-lookup"><span data-stu-id="18058-138">The for-each statement, combined with the `node-set` function, allows the user to iterate over this tree as a node set.</span></span>

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

<span data-ttu-id="18058-139">Voici un autre exemple d'une variable qui correspond à un RTF, et donc de fragment d'arborescence résultat type qui est converti en une collection de nœuds avant d'être passé à une fonction de script comme XPathNodeIterator.</span><span class="sxs-lookup"><span data-stu-id="18058-139">Here is another example of a variable that is in RTF, and hence of type result tree fragment, that is converted to a node set before being passed to a script function as XPathNodeIterator.</span></span>

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

<span data-ttu-id="18058-140">Voici le résultat de la transformation du XML à l'aide de cette feuille de style :</span><span class="sxs-lookup"><span data-stu-id="18058-140">The following is the result of transforming XML with this style sheet:</span></span>

```xml
<books xmlns:user="urn:books">Book1Book2Book3Book4</books>
```

## <a name="see-also"></a><span data-ttu-id="18058-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18058-141">See also</span></span>

- <xref:System.Xml.XPath.XPathNodeIterator>
- [<span data-ttu-id="18058-142">Transformations XSLT avec la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="18058-142">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="18058-143">Implémentation du processeur XSLT par la classe XslTransform</span><span class="sxs-lookup"><span data-stu-id="18058-143">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
