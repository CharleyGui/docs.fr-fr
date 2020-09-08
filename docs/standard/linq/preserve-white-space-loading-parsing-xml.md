---
title: Conserver l’espace blanc lors du chargement ou de l’analyse du XML-LINQ to XML
description: Vous pouvez contrôler le comportement des espaces blancs des méthodes LINQ to XML qui remplissent les arborescences XML. Par exemple, vous pouvez supprimer la mise en retrait pour le traitement en mémoire ou la conserver telle quelle.
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 783a1198f0b1754c690f04159860056a0fbadeb4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552501"
---
# <a name="preserve-white-space-while-loading-or-parsing-xml-linq-to-xml"></a>Conserver l’espace blanc lors du chargement ou de l’analyse du XML (LINQ to XML)

Cet article explique comment contrôler le comportement des espaces blancs de LINQ to XML.

Un scénario courant consiste à lire le code XML mis en retrait, à créer une arborescence XML en mémoire sans nœuds d’espace blanc (autrement dit, ne pas conserver les espaces), à effectuer certaines opérations sur le code XML, puis à enregistrer le code XML avec mise en retrait. Lorsque vous sérialisez le code XML avec mise en forme, seuls les espaces significatifs dans l'arborescence XML sont conservés. Il s’agit du comportement par défaut pour LINQ to XML.

Un autre scénario courant consiste à lire et à modifier du code XML qui a déjà été intentionnellement mis en retrait. Vous ne souhaiterez peut-être modifier cette mise en retrait en aucune manière. Pour effectuer cette opération dans LINQ to XML, vous conservez l’espace blanc lorsque vous chargez ou analysez le XML et que vous désactivez la mise en forme lors de la sérialisation du code XML.

Cet article décrit le comportement des espaces blancs des méthodes qui remplissent les arborescences XML. Pour plus d’informations sur le contrôle des espaces blancs lors de la sérialisation d’arborescences XML, consultez conserver les espaces [blancs lors de la sérialisation](preserve-white-space-serializing.md).

## <a name="behavior-of-methods-that-populate-xml-trees"></a>Comportement des méthodes qui remplissent des arborescences XML

Les méthodes suivantes dans les classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XDocument> remplissent une arborescence XML. Vous pouvez remplir une arborescence XML à partir d'un fichier, d'un objet <xref:System.IO.TextReader>, d'un objet <xref:System.Xml.XmlReader> ou d'une chaîne :

- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>

Si la méthode ne prend pas <xref:System.Xml.Linq.LoadOptions> comme argument, la méthode ne conserve pas les espaces blancs non significatifs.

Dans la plupart des cas, si la méthode prend l'objet <xref:System.Xml.Linq.LoadOptions> comme argument, vous pouvez, si vous le souhaitez, conserver les espaces non significatifs en tant que nœuds de texte dans l'arborescence XML. Toutefois, si la méthode charge le code XML à partir d'un objet <xref:System.Xml.XmlReader>, l'objet <xref:System.Xml.XmlReader> détermine si les espaces seront conservés. La définition de <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> n'aura aucun effet.

Avec ces méthodes, si les espaces sont conservés, des espaces non significatifs sont insérés dans l’arborescence XML en tant que nœuds <xref:System.Xml.Linq.XText>. Si l’espace blanc n’est pas conservé, les nœuds de texte ne sont pas insérés.

Vous pouvez créer une arborescence XML à l’aide d’un objet <xref:System.Xml.XmlWriter>. Les nœuds écrits dans l’objet <xref:System.Xml.XmlWriter> sont remplis dans l’arborescence. Toutefois, lorsque vous générez une arborescence XML à l’aide de cette méthode, tous les nœuds sont conservés, qu’ils soient constitués d’espaces ou non et que ces espaces soient significatifs ou non.
