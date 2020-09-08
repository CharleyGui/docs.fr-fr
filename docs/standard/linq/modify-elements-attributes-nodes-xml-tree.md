---
title: Modification d’éléments, d’attributs et de nœuds dans une arborescence XML
description: En savoir plus sur les méthodes et les propriétés que vous pouvez utiliser pour modifier un élément, ses nœuds enfants ou ses attributs.
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 671ba38350e443d95c92a9bd790eac3d2deb5cdd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553748"
---
# <a name="modify-elements-attributes-and-nodes-in-an-xml-tree-linq-to-xml"></a>Modifier des éléments, des attributs et des nœuds dans une arborescence XML (LINQ to XML)

Le tableau suivant résume les méthodes et propriétés que vous pouvez utiliser pour modifier un élément, ses éléments enfants ou ses attributs.

Les méthodes suivantes modifient un <xref:System.Xml.Linq.XElement> :

|Méthode|Description|
|------------|-----------------|
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|Remplace un élément par du code XML analysé.|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|Supprime tout le contenu (nœuds enfants et attributs) d'un élément.|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|Supprime les attributs d'un élément.|
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|Remplace tout le contenu (nœuds enfants et attributs) d'un élément.|
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|Remplace les attributs d'un élément.|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|Définit la valeur d'un attribut. Crée l'attribut s'il n'existe pas. Si la valeur est définie à `null`, supprime l'attribut.|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|Définit la valeur d'un élément enfant. Crée l'élément s'il n'existe pas. Si la valeur est définie à `null`, supprime l'élément.|
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|Remplace le contenu (nœuds enfants) d'un élément par le texte spécifié.|
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|Définit la valeur d'un élément.|

Les méthodes suivantes modifient un <xref:System.Xml.Linq.XAttribute> :

|Méthode|Description|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|Définit la valeur d'un attribut.|
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|Définit la valeur d'un attribut.|

 Les méthodes suivantes modifient un <xref:System.Xml.Linq.XNode> (y compris un <xref:System.Xml.Linq.XElement> ou un <xref:System.Xml.Linq.XDocument> ) :

|Méthode|Description|
|------------|-----------------|
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|Remplace un nœud par du nouveau contenu.|

 Les méthodes suivantes modifient un <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> ) :

|Méthode|Description|
|------------|-----------------|
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|Remplace les nœuds enfants par le nouveau contenu :|
