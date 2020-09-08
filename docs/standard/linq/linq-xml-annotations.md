---
title: Annotations-LINQ to XML
description: Apprenez à utiliser des annotations dans LINQ to XML pour associer tout objet arbitraire de tout type arbitraire à n’importe quel composant XML dans une arborescence XML.
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 80710b3596fc37ed76f23e31d1d781c64d0bc909
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553367"
---
# <a name="linq-to-xml-annotations-linq-to-xml"></a>Annotations de LINQ to XML (LINQ to XML)

Les annotations dans LINQ to XML vous permettent d’associer n’importe quel objet arbitraire de n’importe quel type arbitraire à n’importe quel composant XML dans une arborescence XML.

Pour ajouter une annotation à un composant XML, tel qu'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous appelez la méthode <xref:System.Xml.Linq.XObject.AddAnnotation%2A>. Vous pouvez récupérer des annotations par type.

Notez que les annotations ne font pas partie de l’Infoset XML. ils ne sont pas sérialisés ou désérialisés.

## <a name="methods"></a>Méthodes

Vous pouvez utiliser les méthodes suivantes lorsque vous travaillez avec des annotations :

|Méthode|Description|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Ajoute un objet à la liste d'annotation de <xref:System.Xml.Linq.XObject>.|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Obtient le premier objet annotation du type spécifié de <xref:System.Xml.Linq.XObject>.|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Obtient une collection d’annotations du type spécifié pour un objet <xref:System.Xml.Linq.XObject>.|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Supprime les annotations du type spécifié d’un objet <xref:System.Xml.Linq.XObject>.|
