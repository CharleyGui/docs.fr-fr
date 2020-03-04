---
title: Transformations XSLT avec la classe XslTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 500335af-f9b5-413b-968a-e6d9a824478c
ms.openlocfilehash: e03eb08c71ff2d031ac61a702683e3950d94f2be
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160233"
---
# <a name="xslt-transformations-with-the-xsltransform-class"></a>Transformations XSLT avec la classe XslTransform

> [!NOTE]
> La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans .NET Framework 2.0. Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Pour plus d'informations, consultez les pages [Utiliser la classe XslCompiledTransform](using-the-xslcompiledtransform-class.md) et [Migrer à partir de la classe XslTransform](migrating-from-the-xsltransform-class.md).

Le but des transformations XSLT est de transformer le contenu d’un document XML source en un autre document différent par son format ou sa structure (par exemple, transformer du code XML en HTML afin de l’utiliser sur un site web ou le transformer en un document contenant uniquement les champs requis par une application). Ce processus de transformation est spécifié par la [recommandation sur XSLT version 1.0](https://www.w3.org/TR/1999/REC-xslt-19991116) du World Wide Web Consortium (W3C). Dans le .NET Framework, la classe <xref:System.Xml.Xsl.XslTransform>, située dans l’espace de noms <xref:System.Xml.Xsl>, est le processeur XSLT qui implémente les fonctionnalités de cette spécification. Certaines fonctionnalités n’ayant pas été implémentées à partir de la recommandation du W3C sur XSLT 1.0 sont répertoriées dans [Sorties à partir de XslTransform](outputs-from-an-xsltransform.md). La figure suivante illustre l’architecture de transformation du .NET Framework.

## <a name="overview"></a>Overview

![Diagramme qui montre l’architecture de transformation XSLT.](./media/xslt-transformations-with-the-xsltransform-class/xslt-transformation-architecture.gif)

La recommandation XSLT utilise XML Path Language (XPath) pour sélectionner des parties d'un document XML, où XPath est un langage de requête utilisé pour accéder aux nœuds d'une arborescence de document. Comme illustré dans le diagramme, l’implémentation du NET Framework de XPath est utilisée pour sélectionner des parties de XML dans plusieurs classes, comme <xref:System.Xml.XmlDocument>, <xref:System.Xml.XmlDataDocument> et <xref:System.Xml.XPath.XPathDocument>. Un objet <xref:System.Xml.XPath.XPathDocument> est un magasin de données XSLT optimisé qui fournit des transformations XSLT performantes lorsqu'il est utilisé avec l'objet <xref:System.Xml.Xsl.XslTransform>.

Le tableau suivant répertorie les classes généralement utilisées lors de l’utilisation de l’objet <xref:System.Xml.Xsl.XslTransform> et de XPath et leur fonction.

|Classe ou interface|Fonction|
|------------------------|--------------|
|<xref:System.Xml.XPath.XPathNavigator>|API qui fournit un modèle de style curseur pour naviguer dans un magasin ainsi qu’une prise en charge de requête XPath. Elle ne permet pas de modifier le magasin sous-jacent. Pour le modifier, utilisez la classe <xref:System.Xml.XmlDocument>.|
|<xref:System.Xml.XPath.IXPathNavigable>|Interface qui fournit une méthode `CreateNavigator` à un objet <xref:System.Xml.XPath.XPathNavigator> pour le magasin.|
|<xref:System.Xml.XmlDocument>|Permet la modification de ce document. Cette classe implémente l'objet <xref:System.Xml.XPath.IXPathNavigable>, autorisant des scénarios de modification de documents où des transformations XSLT sont ultérieurement requises. Pour plus d'informations, consultez [Entrée XmlDocument dans XslTransform](xmldocument-input-to-xsltransform.md).|
|<xref:System.Xml.XmlDataDocument>|Classe dérivée de l'objet <xref:System.Xml.XmlDocument>. Elle établit une passerelle entre les mondes relationnels et XML en utilisant un objet <xref:System.Data.DataSet> pour optimiser le stockage de données structurées dans le document XML selon les mappages spécifiés sur l'objet <xref:System.Data.DataSet>. Elle implémente l'interface <xref:System.Xml.XPath.IXPathNavigable>, autorisant des scénarios où des transformations XSLT peuvent être effectuées sur des données relationnelles extraites d'une base de données. Pour plus d'informations, voir [Intégration de XML aux données relationnelles et à ADO.NET](xml-integration-with-relational-data-and-adonet.md).|
|<xref:System.Xml.XPath.XPathDocument>|Classe optimisée pour le traitement de l’objet <xref:System.Xml.Xsl.XslTransform> et les requêtes XPath, elle fournit un cache très performant en lecture seule. Elle implémente l'interface <xref:System.Xml.XPath.IXPathNavigable> et représente le magasin par défaut à utiliser pour les transformations XSLT.|
|<xref:System.Xml.XPath.XPathNodeIterator>|Permet la navigation dans des collections de nœuds XPath. Toutes les méthodes de sélection XPath sur l’objet <xref:System.Xml.XPath.XPathNavigator> retournent une classe <xref:System.Xml.XPath.XPathNodeIterator>. Plusieurs objets <xref:System.Xml.XPath.XPathNodeIterator> peuvent être créés sur le même magasin, chacune représentant une collection de nœuds sélectionnée.|

## <a name="msxml-xslt-extensions"></a>Extensions de MSXML XSLT

Les fonctions `msxsl:script` et `msxsl:node-set` sont les seules extensions de Microsoft XML Core Services (MSXML) XSLT prises en charge par la classe <xref:System.Xml.Xsl.XslTransform>.

## <a name="example"></a>Exemple

L'exemple de code suivant charge une feuille de style XSLT, lit un fichier nommé mydata.xml dans un objet <xref:System.Xml.XPath.XPathDocument> et effectue une transformation des données sur un fichier fictif nommé myStyleSheet.xsl, en envoyant le résultat mis en forme à la console.

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.XPath
Imports System.Xml.Xsl

Public Class Sample
    Private filename As [String] = "mydata.xml"
    Private stylesheet As [String] = "myStyleSheet.xsl"

    Public Shared Sub Main()
        Dim xslt As New XslTransform()
        xslt.Load(stylesheet)
        Dim xpathdocument As New XPathDocument(filename)
        Dim writer As New XmlTextWriter(Console.Out)
        writer.Formatting = Formatting.Indented

        xslt.Transform(xpathdocument, Nothing, writer, Nothing)
    End Sub 'Main
End Class 'Sample
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.XPath;
using System.Xml.Xsl;

public class Sample
{
    private const String filename = "mydata.xml";
    private const String stylesheet = "myStyleSheet.xsl";

    public static void Main()
    {
        XslTransform xslt = new XslTransform();
        xslt.Load(stylesheet);
        XPathDocument xpathdocument = new XPathDocument(filename);
        XmlTextWriter writer = new XmlTextWriter(Console.Out);
        writer.Formatting = Formatting.Indented;

        xslt.Transform(xpathdocument, null, writer, null);
    }
}
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Xsl.XslTransform>
- [Implémentation du processeur XSLT par la classe XslTransform](xsltransform-class-implements-the-xslt-processor.md)
- [Implémentation de comportements discrétionnaires dans la classe XslTransform](implementation-of-discretionary-behaviors-in-the-xsltransform-class.md)
- [XPathNavigator dans les transformations](xpathnavigator-in-transformations.md)
- [XPathNodeIterator dans les transformations](xpathnodeiterator-in-transformations.md)
- [Entrée XPathDocument dans XslTransform](xpathdocument-input-to-xsltransform.md)
- [Entrée XmlDataDocument dans XslTransform](xmldatadocument-input-to-xsltransform.md)
- [Entrée XmlDocument dans XslTransform](xmldocument-input-to-xsltransform.md)
