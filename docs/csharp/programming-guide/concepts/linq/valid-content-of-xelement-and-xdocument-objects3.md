---
title: Contenu valide des objets XElement et XDocument3
description: Découvrez les arguments valides qui peuvent être passés aux constructeurs et aux méthodes que vous utilisez pour ajouter du contenu aux éléments et aux documents.
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: dfafbe76b078db6c22b475770ebadaff38c75ba8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302254"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Contenu valide des objets XElement et XDocument
Cette rubrique décrit les arguments valides qui peuvent être passés aux constructeurs et méthodes utilisés pour ajouter du contenu aux éléments et aux documents.  
  
## <a name="valid-content"></a>Contenu valide  
 Les requêtes sont souvent évaluées à un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> ou un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XAttribute>. Vous pouvez passer des collections d'objets <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> au constructeur <xref:System.Xml.Linq.XElement>. Par conséquent, il est commode de passer les résultats d'une requête en tant que contenu dans des méthodes et des constructeurs que vous utilisez pour remplir des arborescences XML.  
  
 Lors de l'ajout de contenu simple, divers types peuvent être passés à cette méthode. Les types valides sont les suivants :  
  
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
  
 Lors de l'ajout de contenu complexe, divers types peuvent être passés à cette méthode :  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- Tout type qui implémente <xref:System.Collections.Generic.IEnumerable%601>  
  
 Si un objet implémente <xref:System.Collections.Generic.IEnumerable%601>, la collection dans l'objet est énumérée et tous les éléments de la collection sont ajoutés. Si la collection contient des objets <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, chaque élément de la collection est ajouté séparément. Si la collection contient du texte (ou des objets convertis en texte), le texte dans la collection est concaténé et ajouté en tant que nœud de texte simple.  
  
 Si le contenu est `null`, rien n'est ajouté. Lors du passage d'une collection, des éléments de cette collection peuvent avoir la valeur `null`. Un élément `null` dans la collection n'a aucun effet sur l'arborescence.  
  
 Un attribut ajouté doit avoir un nom unique dans son élément conteneur.  
  
 Lors de l’ajout d’objets <xref:System.Xml.Linq.XNode> ou <xref:System.Xml.Linq.XAttribute>, si le contenu n’a pas de parent, les objets sont simplement attachés à l’arborescence XML. Si le nouveau contenu a déjà un parent et fait partie d'une autre arborescence XML, il est cloné et le nouveau contenu cloné est attaché à l'arborescence XML.  
  
## <a name="valid-content-for-documents"></a>Contenu valide pour les documents  
 Les attributs et le contenu simple ne peuvent pas être ajoutés à un document.  
  
 Il n'existe pas beaucoup de scénarios qui requièrent la création d'un objet <xref:System.Xml.Linq.XDocument>. Au lieu de cela, vous pouvez généralement créer vos arborescences XML avec un nœud racine <xref:System.Xml.Linq.XElement>. À moins que la création d'un document ne soit spécifiquement requise (par exemple si vous devez créer des instructions de traitement et des commentaires au niveau supérieur ou si vous devez prendre en charge des types de documents), il est souvent plus commode d'utiliser <xref:System.Xml.Linq.XElement> comme nœud racine.  
  
 Le contenu valide pour un document inclut les éléments suivants :  
  
- Zéro ou un objet <xref:System.Xml.Linq.XDocumentType>. Les types de documents doivent figurer avant l'élément.  
  
- Zéro ou un élément.  
  
- Zéro ou plusieurs commentaires.  
  
- Zéro ou plusieurs instructions de traitement.  
  
- Zéro ou plusieurs nœuds de texte qui contiennent uniquement des espaces blancs.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Constructeurs et fonctions qui autorisent l'ajout de contenu  
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

- [Création d’arborescences XML (C#)](./linq-to-xml-overview.md)
