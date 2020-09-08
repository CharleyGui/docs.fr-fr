---
title: Conserver les espaces blancs lors de la sérialisation de-LINQ to XML
description: Vous pouvez contrôler les espaces de différentes façons lors de la sérialisation d’une arborescence XML.
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d907e68a2df3905794b555954330f31b5e75655
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552488"
---
# <a name="preserve-white-space-while-serializing-linq-to-xml"></a>Conserver les espaces blancs lors de la sérialisation (LINQ to XML)

Cet article explique comment contrôler l’espace blanc lors de la sérialisation d’une arborescence XML.

Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d’espace blanc (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait. Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés. Il s’agit du comportement par défaut pour LINQ to XML.

Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait. Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière. Pour effectuer cette opération dans LINQ to XML, vous conservez l’espace blanc lorsque vous chargez ou analysez le XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.

## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Comportement d’espace blanc des méthodes qui sérialisent des arborescences XML

Les méthodes suivantes dans les classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XDocument> sérialisent une arborescence XML. Vous pouvez sérialiser une arborescence XML vers un fichier, un objet <xref:System.IO.TextReader> ou un objet <xref:System.Xml.XmlReader>. La méthode `ToString` sérialise vers une chaîne.

- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)

Si la méthode ne prend pas <xref:System.Xml.Linq.SaveOptions> comme argument, la méthode met en forme (en retrait) le code XML sérialisé. Dans ce cas, tous les espaces blancs non significatifs dans l'arborescence XML seront ignorés.

Si la méthode prend l'objet <xref:System.Xml.Linq.SaveOptions> comme argument, vous pouvez spécifier qu'elle ne mettra pas en forme (en retrait) le code XML sérialisé. Dans ce cas, tous les espaces blancs dans l’arborescence XML seront conservés.
