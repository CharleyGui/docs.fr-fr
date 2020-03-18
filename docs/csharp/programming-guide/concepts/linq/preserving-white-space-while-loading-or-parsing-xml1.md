---
title: Conservation des espaces blancs lors du chargement ou de l’analyse de code XML
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: d015c21813df2224356bb49212fe282fa5372d03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591542"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Conservation des espaces blancs lors du chargement ou de l’analyse de code XML
Cette rubrique décrit comment contrôler la gestion des espaces blancs par [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d'espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait. Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés. Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait. Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière. Pour ce faire dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous devez conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.  
  
 Cette rubrique décrit la gestion des espaces blancs par les méthodes qui remplissent les arborescences XML. Pour plus d’informations sur le contrôle des espaces blancs quand vous sérialisez des arborescences XML, consultez [Conservation des espaces blancs lors de la sérialisation](./preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Comportement des méthodes qui remplissent des arborescences XML  
 Les méthodes suivantes dans les classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XDocument> remplissent une arborescence XML. Vous pouvez remplir une arborescence XML à partir d'un fichier, d'un objet <xref:System.IO.TextReader>, d'un objet <xref:System.Xml.XmlReader> ou d'une chaîne :  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Si la méthode ne prend pas l’objet <xref:System.Xml.Linq.LoadOptions> comme argument, elle ne conservera pas les espaces non significatifs.  
  
 Dans la plupart des cas, si la méthode prend l'objet <xref:System.Xml.Linq.LoadOptions> comme argument, vous pouvez, si vous le souhaitez, conserver les espaces non significatifs en tant que nœuds de texte dans l'arborescence XML. Toutefois, si la méthode charge le code XML à partir d'un objet <xref:System.Xml.XmlReader>, l'objet <xref:System.Xml.XmlReader> détermine si les espaces seront conservés. La définition de <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> n'aura aucun effet.  
  
 Avec ces méthodes, si les espaces sont conservés, des espaces non significatifs sont insérés dans l’arborescence XML en tant que nœuds <xref:System.Xml.Linq.XText>. Si les espaces ne sont pas conservés, aucun nœud de texte n'est inséré.  
  
 Vous pouvez créer une arborescence XML à l’aide d’un objet <xref:System.Xml.XmlWriter>. Les nœuds écrits dans l’objet <xref:System.Xml.XmlWriter> sont remplis dans l’arborescence. Toutefois, lorsque vous générez une arborescence XML à l’aide de cette méthode, tous les nœuds sont conservés, qu’ils soient constitués d’espaces ou non et que ces espaces soient significatifs ou non.  
  