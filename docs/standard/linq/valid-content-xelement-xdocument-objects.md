---
title: Contenu valide des objets XElement et XDocument-LINQ to XML
description: Les constructeurs XElement et XDocument acceptent de nombreux types d’argument, y compris les collections retournées par les requêtes. Il existe d’autres constructeurs et fonctions pour l’ajout de contenu XML.
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: e0288dce06f8040385c9b9a30335fd039d3c45bd
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553766"
---
# <a name="valid-content-of-xelement-and-xdocument-objects-linq-to-xml"></a>Contenu valide des objets XElement et XDocument (LINQ to XML)

Cet article décrit les arguments valides qui peuvent être passés aux constructeurs, ainsi que les méthodes que vous utilisez pour ajouter du contenu aux éléments et aux documents.

## <a name="valid-types-for-the-xelement-constructor"></a>Types valides pour le constructeur XElement

Les requêtes sont souvent évaluées à un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> ou un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XAttribute>. Vous pouvez passer des collections d'objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> au constructeur <xref:System.Xml.Linq.XElement>. C’est pourquoi il est commode de passer les résultats d’une requête en tant que contenu dans des méthodes et des constructeurs que vous utilisez pour remplir des arborescences XML.

Lors de l’ajout de contenu simple, divers types peuvent être passés à cette méthode, notamment ::

- <xref:System.String>
- <xref:System.Double>
- <xref:System.Single>
- <xref:System.Decimal>
- <xref:System.Boolean>
- <xref:System.DateTime>
- <xref:System.TimeSpan>
- <xref:System.DateTimeOffset>
- Tout type qui implémente `Object.ToString`.
- Tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601>.

Lors de l’ajout de contenu complexe, divers types peuvent être passés à cette méthode, notamment :

- <xref:System.Xml.Linq.XObject>
- <xref:System.Xml.Linq.XNode>
- <xref:System.Xml.Linq.XAttribute>
- Tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601>

Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l'objet est énumérée et tous les éléments de la collection sont ajoutés. Si la collection contient des objets <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, chaque élément de la collection est ajouté séparément. Si la collection contient du texte (ou des objets convertis en texte), le texte dans la collection est concaténé et ajouté en tant que nœud de texte simple.

Si le contenu est `null`, rien n'est ajouté. Lors du passage d’une collection, les éléments de la collection peuvent être `null` . Un élément `null` dans la collection n'a aucun effet sur l'arborescence.

Un attribut ajouté doit avoir un nom unique dans son élément conteneur.

Lors de l’ajout d’objets <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, si le contenu n’a pas de parent, les objets sont simplement attachés à l’arborescence XML. Si le nouveau contenu a déjà un parent et fait partie d'une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l'arborescence XML.

## <a name="valid-types-for-the-xdocument-constructor"></a>Types valides pour le constructeur XDocument

Les attributs et le contenu simple ne peuvent pas être ajoutés à un document.

Il n’existe pas de nombreux scénarios qui requièrent la création d’un <xref:System.Xml.Linq.XDocument> . Au lieu de cela, vous pouvez généralement créer vos arborescences XML avec un nœud racine <xref:System.Xml.Linq.XElement>. À moins que vous ayez besoin de créer un document spécifique (par exemple, parce que vous devez créer des instructions de traitement et des commentaires au niveau supérieur, ou que vous devez prendre en charge des types de documents), il est souvent plus pratique d’utiliser <xref:System.Xml.Linq.XElement> comme nœud racine.

Les types valides pour le <xref:System.Xml.Linq.XDocument.%23ctor%2A> constructeur sont les suivants :

- Zéro ou un objet <xref:System.Xml.Linq.XDocumentType>. Les types de documents doivent figurer avant l'élément.
- Zéro ou un élément.
- Zéro ou plusieurs commentaires.
- Zéro ou plusieurs instructions de traitement.
- Zéro ou plusieurs nœuds de texte qui contiennent uniquement des espaces blancs.

## <a name="constructors-and-functions-for-adding-content"></a>Constructeurs et fonctions pour l’ajout de contenu

Les méthodes suivantes vous permettent d'ajouter du contenu enfant à un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument> :

|Méthode|Description|
|------------|-----------------|
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Construit un objet <xref:System.Xml.Linq.XElement>.|
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Construit un objet <xref:System.Xml.Linq.XDocument>.|
|<xref:System.Xml.Linq.XContainer.Add%2A>|Ajoute à la fin du contenu enfant de l'objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>.|
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Ajoute du contenu après l'objet <xref:System.Xml.Linq.XNode>.|
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Ajoute du contenu avant l'objet <xref:System.Xml.Linq.XNode>.|
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Ajoute du contenu au début du contenu enfant de l'objet <xref:System.Xml.Linq.XContainer>.|
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Remplace tout le contenu (nœuds enfants et attributs) d'un objet <xref:System.Xml.Linq.XElement>.|
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Remplace les attributs d'un objet <xref:System.Xml.Linq.XElement>.|
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Remplace les nœuds enfants par du nouveau contenu.|
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Remplace un nœud par du nouveau contenu.|

## <a name="see-also"></a>Voir aussi

- [Arborescences XML](functional-construction.md)
