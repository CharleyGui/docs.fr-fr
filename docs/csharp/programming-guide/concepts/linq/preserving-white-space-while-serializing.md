---
title: Conservation des espaces blancs lors de la sérialisation3
description: Découvrez comment contrôler l’espace blanc lors de la sérialisation d’une arborescence XML à l’aide de méthodes dans les classes XElement et XDocument.
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 01e68671e2fde1a2b5b1d0bc429841077ba0205f
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303411"
---
# <a name="preserving-white-space-while-serializing"></a>Conservation des espaces blancs lors de la sérialisation
Cette rubrique décrit comment contrôler les espaces blancs lors de la sérialisation d'une arborescence XML.  
  
 Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d’espaces (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait. Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés. Il s'agit du comportement par défaut pour [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait. Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière. Pour ce faire dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous devez conserver les espaces lorsque vous chargez ou analysez le code XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Gestion des espaces blancs par les méthodes qui sérialisent des arborescences XML  
 Les méthodes suivantes dans les classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XDocument> sérialisent une arborescence XML. Vous pouvez sérialiser une arborescence XML vers un fichier, un objet <xref:System.IO.TextReader> ou un objet <xref:System.Xml.XmlReader>. La méthode `ToString` sérialise vers une chaîne.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Si la méthode ne prend pas l'objet <xref:System.Xml.Linq.SaveOptions> comme argument, elle mettra en forme (en retrait) le code XML sérialisé. Dans ce cas, tous les espaces blancs non significatifs dans l'arborescence XML seront ignorés.  
  
 Si la méthode prend l'objet <xref:System.Xml.Linq.SaveOptions> comme argument, vous pouvez spécifier qu'elle ne mettra pas en forme (en retrait) le code XML sérialisé. Dans ce cas, tous les espaces blancs dans l’arborescence XML seront conservés.  
