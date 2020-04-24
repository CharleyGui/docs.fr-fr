---
title: Implémentation du processeur XSLT par la classe XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
ms.openlocfilehash: 73a432db9a3fcb6587184e27e6dfe9ba49010e92
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709606"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a>Implémentation du processeur XSLT par la classe XslTransform

> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez [Utilisation de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [Migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).

La classe <xref:System.Xml.Xsl.XslTransform> est un processeur XSLT qui implémente la recommandation XSL Transformations (XSLT) version 1.0. La méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> localise et lit des feuilles de style, et la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> transforme le document source donné. Tout magasin implémentant l'interface <xref:System.Xml.XPath.IXPathNavigable> peut être utilisé comme document source pour l'objet <xref:System.Xml.Xsl.XslTransform>. Le .NET Framework implémente actuellement l’interface <xref:System.Xml.XPath.IXPathNavigable> sur les éléments <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument> et <xref:System.Xml.XPath.XPathDocument>, de sorte qu’ils peuvent tous être utilisés comme le document source d’entrée d’une transformation.

L’objet <xref:System.Xml.Xsl.XslTransform> du .NET Framework prend uniquement en charge la spécification XSLT 1.0, définie par l’espace de noms suivant :

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

La feuille de style peut être chargée, à l'aide de la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A>, à partir de l'une des classes suivantes :

- XPathNavigator

- XmlReader

- Une chaîne représentant une URL

Il existe une méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> différente pour chacune des classes d'entrée ci-avant. Certaines méthodes prennent une combinaison de ces classes et la classe <xref:System.Xml.XmlResolver> comme arguments. L'objet <xref:System.Xml.XmlResolver> localise les ressources référencées par `<xsl:import>` ou `<xsl:include>` trouvées dans la feuille de style. Les méthodes suivantes prennent une chaîne, l'objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XPath.XPathNavigator>, comme entrée.

```vb
Overloads Public Sub Load(String)
```

```csharp
public void Load(string);
```

```vb
Overloads Public Sub Load(String, XmlResolver)
```

```csharp
public void Load(string, XmlResolver);
```

```vb
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)
```

```csharp
public void Load(XmlReader, XmlResolver, Evidence);
```

```vb
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)
```

```csharp
public void Load(XPathNavigator, XmlResolver, Evidence);
```

La plupart des méthodes <xref:System.Xml.Xsl.XslTransform.Load%2A> illustrées ci-avant prennent un objet <xref:System.Xml.XmlResolver> comme paramètre. L'objet <xref:System.Xml.XmlResolver> s'utilise pour charger la feuille de style et toutes les feuilles de style référencées dans les éléments xsl:import et xsl:include.

La plupart des méthodes <xref:System.Xml.Xsl.XslTransform.Load%2A> prennent également la preuve comme paramètre. Le paramètre de preuve correspond à l'objet <xref:System.Security.Policy.Evidence> associé à la feuille de style. Le niveau de sécurité de la feuille de style affecte le niveau de sécurité de toutes les ressources ultérieures qu'elle référence, comme le script qu'elle contient, toute fonction `document()` qu'elle utilise, et tous les objets d'extension utilisés par l'objet <xref:System.Xml.Xsl.XsltArgumentList>.

Si la feuille de style est chargée à l'aide de la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A> qui contient un paramètre d'URL et aucune preuve, la preuve de la feuille de style est calculée en combinant l'URL donnée avec son site et sa zone.

Si aucun URI ou aucune preuve n'est fourni, la preuve définie pour la feuille de style est d'un niveau de confiance suffisant. Ne chargez pas de feuilles de style à partir de sources non fiables ou n'ajoutez pas d'objets d'extension non fiables dans l'objet <xref:System.Xml.Xsl.XsltArgumentList>.

Pour plus d'informations sur les niveaux de sécurité et les preuves, ainsi que sur la manière dont ils affectent la création de scripts, consultez [XSLT Stylesheet Scripting à l’aide de \<msxsl:script>](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md). Pour plus d’informations sur les niveaux de sécurité et les preuves, ainsi que sur la manière dont ils affectent les objets d’extension, consultez [XsltArgumentList pour les paramètres de feuille de style et les objets d’extension](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).

Pour plus d'informations sur les niveaux de sécurité et les preuves, ainsi que la manière dont ceux-ci affectent la fonction `document()`, consultez [Résolution de feuilles de style XSLT externes et de documents](../../../../docs/standard/data/xml/resolving-external-xslt-style-sheets-and-documents.md).

Une feuille de style peut être fournie par un nombre de paramètres d'entrée. La feuille de style peut également appeler des fonctions sur des objets d'extension. Tant les paramètres que les objets d'extension sont fournis à la feuille de style à l'aide de la classe <xref:System.Xml.Xsl.XsltArgumentList>. Pour plus d'informations sur le <xref:System.Xml.Xsl.XsltArgumentList>, consultez <xref:System.Xml.Xsl.XsltArgumentList>.

## <a name="recommended-secure-use-of-xsltransform-class"></a>Utilisation sécurisée recommandée de la classe XslTransform

Les privilèges de sécurité de la feuille de style dépendent de la preuve fournie. Le tableau suivant résume l'emplacement de la feuille de style et donne une explication du type de preuve à fournir.

- La feuille de style XSLT n'a pas de référence externe ou la feuille de style provient d'une base de code auquel vous faites confiance.

  - Fournissez la preuve à partir de votre assembly :

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- La feuille de style XSLT provient d'une source externe. L'origine de la source est connue et il existe un URI vérifiable.

  - Créez la preuve à l'aide de l'URI.

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- La feuille de style XSLT provient d'une source externe. L'origine de la source n'est pas connue.

  - Attribuez à la preuve la valeur `null`. Les blocs de script ne sont pas traités, la fonction `document()` XSLT n’est pas prise en charge et les objets d’extension privilégiés ne sont pas autorisés.

    En outre, vous pouvez également attribuer la valeur `resolver` au paramètre `null`. Vous garantissez ainsi que les éléments `xsl:import` et `xsl:include` ne sont pas traités.

- La feuille de style XSLT provient d'une source externe. L'origine de la source n'est pas connue, mais vous avez besoin de la prise en charge des scripts.

  - Demandez une preuve à l'appelant.

## <a name="transformation-of-xml-data"></a>Transformation de données XML

Dès qu'une feuille de style est chargée, la transformation démarre en appelant l'une des méthodes <xref:System.Xml.Xsl.XslTransform.Transform%2A> et en fournissant un document source d'entrée. La méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est surchargée pour fournir diverses sorties de transformation. La transformation peut avoir comme résultat l'un des formats de sortie suivants :

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- String URL de fichier

Le dernier format (String URL) prévoit un scénario généralement utilisé consistant à transformer un document d'entrée situé dans une URL et à écrire le document dans l'URL de sortie. Cette méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est une méthode pratique pour charger un document XML à partir d'un fichier, effectuer la transformation XSLT et écrire la sortie dans un fichier. Il n'est donc pas nécessaire de créer et de charger le document source d'entrée, puis d'écrire dans un flux de fichier. L'exemple de code suivant illustre l'utilisation de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> utilisant le String URL en tant qu'entrée et sortie :

```vb
Dim xsltransform As XslTransform = New XslTransform()
xsltransform.Load("favorite.xsl")
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)
```

```csharp
XslTransform xsltransform = new XslTransform();
xsltransform.Load("favorite.xsl");
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);
```

## <a name="transforming-a-section-of-an-xml-document"></a>Transformation d'une section d'un document XML

Les transformations s'appliquent à l'ensemble du document. En d'autres termes, si vous passez dans un autre nœud que le nœud racine du document, cela n'empêche pas le processus de transformation d'accéder à tous les nœuds dans le document chargé. Pour transformer un fragment d’arbre résultat, vous devez créer un objet <xref:System.Xml.XmlDocument> contenant uniquement le fragment d’arbre résultat et passer l’objet <xref:System.Xml.XmlDocument> à la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>. L’exemple suivant effectue une transformation sur un fragment d’arbre résultat.

```vb
Dim xslt As New XslTransform()
xslt.Load("print_root.xsl")
Dim doc As New XmlDocument()
doc.Load("library.xml")
' Create a new document containing just the result tree fragment.
Dim testNode As XmlNode = doc.DocumentElement.FirstChild
Dim tmpDoc As New XmlDocument()
tmpDoc.LoadXml(testNode.OuterXml)
' Pass the document containing the result tree fragment
' to the Transform method.
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)
```

```csharp
XslTransform xslt = new XslTransform();
xslt.Load("print_root.xsl");
XmlDocument doc = new XmlDocument();
doc.Load("library.xml");
// Create a new document containing just the result tree fragment.
XmlNode testNode = doc.DocumentElement.FirstChild;
XmlDocument tmpDoc = new XmlDocument();
tmpDoc.LoadXml(testNode.OuterXml);
// Pass the document containing the result tree fragment
// to the Transform method.
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");
xslt.Transform(tmpDoc, null, Console.Out, null);
```

L’exemple utilise les fichiers Library. xml et print_root. xsl comme entrée et génère le résultat suivant sur la console :

```console
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

library.xml

```xml
<library>
  <book genre='novel' ISBN='1-861001-57-5'>
     <title>Pride And Prejudice</title>
  </book>
  <book genre='novel' ISBN='1-81920-21-2'>
     <title>Hook</title>
  </book>
</library>
```

print_root.xsl

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a>Migration de XSLT depuis le .NET Framework version 1.0 vers le .NET Framework version 1.1

Le tableau suivant montre les méthodes obsolètes de .NET Framework version 1.0 et les nouvelles méthodes de .NET Framework version 1.1 pour la méthode <xref:System.Xml.Xsl.XslTransform.Load%2A>. Les nouvelles méthodes vous permettent de limiter les autorisations de la feuille de style en spécifiant une preuve.

|Méthodes Load obsolètes du .NET Framework version 1.0|Méthodes Load de remplacement du .NET Framework version 1.1|
|------------------------------------------------------|---------------------------------------------------------|
|Load(entrée XPathNavigator)<br /><br /> Load(entrée XPathNavigator, programme de résolution XmlResolver)|Load(feuille de style XPathNavigator, programme de résolution XmlResolver, preuve Evidence)|
|Load(feuille de style IXPathNavigable)<br /><br /> Load(feuille de style IXPathNavigable, programme de résolution XmlResolver)|Load(feuille de style IXPathNavigable, programme de résolution XmlResolver, preuve Evidence)|
|Load(feuille de style XmlReader)<br /><br /> Load(feuille de style XmlReader, programme de résolution XmlResolver)|Load(feuille de style XmlReader, programme de résolution XmlResolver, preuve Evidence)|

Le tableau suivant illustre les méthodes obsolètes et nouvelles pour la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A>. Les nouvelles méthodes prennent un objet <xref:System.Xml.XmlResolver>.

|Méthodes Transform obsolètes du .NET Framework version 1.0|Méthodes Transform de remplacement du .NET Framework version 1.1|
|-----------------------------------------------------------|--------------------------------------------------------------|
|XmlReader Transform(entrée XPathNavigator, argument XsltArgumentList)|XmlReader Transform(entrée XPathNavigator, argument XsltArgumentList, programme de résolution XmlResolver)|
|XmlReader Transform(entrée IXPathNavigable, argument XsltArgumentList)|XmlReader Transform(entrée IXPathNavigable, argument XsltArgumentList, programme de résolution XmlResolver)|
|Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie XmlWriter)|Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie XmlWriter, programme de résolution XmlResolver)|
|Void Transform(entrée IXPathNavigable, argument XsltArgumentList, sortie XmlWriter)|Void Transform(entrée IXpathNavigable, argument XsltArgumentList, sortie XmlWriter, programme de résolution XmlResolver)|
|Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie TextWriter)|Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie TextWriter, programme de résolution XmlResolver)|
|Void Transform(entrée IXPathNavigable, argument XsltArgumentList, sortie TextWriter)|Void Transform(entrée IXPathNavigable, argument XsltArgumentList, sortie TextWriter, programme de résolution XmlResolver)|
|Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie Stream)|Void Transform(entrée XPathNavigator, argument XsltArgumentList, sortie Stream, programme de résolution XmlResolver)|
|Void Transform(entrée IXPathNavigable, argument XsltArgumentList, sortie Stream)|Void Transform(entrée IXPathNavigable, argument XsltArgumentList, sortie Stream, programme de résolution XmlResolver)|
|Void Transform(entrée String, sortie String)|Void Transform(entrée String, sortie String, programme de résolution XmlResolver)|

La propriété <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> est obsolète dans .NET Framework version 1.1. Utilisez à la place les nouvelles surcharges <xref:System.Xml.Xsl.XslTransform.Transform%2A> qui acceptent un objet <xref:System.Xml.XmlResolver>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Xsl.XslTransform>
- [Transformations XSLT avec la classe XslTransform](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [XPathNavigator dans les transformations](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [XPathNodeIterator dans les transformations](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [Entrée XPathDocument dans XslTransform](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [Entrée XmlDataDocument dans XslTransform](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [Entrée XmlDocument dans XslTransform](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
