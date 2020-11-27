---
title: Extensibilité de la syndication
ms.date: 03/30/2017
ms.assetid: 4d941175-74a2-4b15-81b3-086e8a95d25f
ms.openlocfilehash: 39187f228e47ed4e82c8e737563b860ce5734416
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266530"
---
# <a name="syndication-extensibility"></a>Extensibilité de la syndication

L'API de syndication est conçue pour fournir un modèle de programmation neutre en ce qui concerne le format qui autorise l'écriture du contenu syndiqué sur le câble dans divers formats. Le modèle de données abstrait inclut les classes suivantes :  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Ces classes mappent précisément aux constructions définies dans la spécification Atom 1.0, bien que certains noms soient différents.  
  
 L’une des fonctionnalités clés de protocoles de syndication est l’extensibilité. Atom 1.0 et RSS 2.0 ajoutent des attributs et des éléments aux flux de syndication des attributs et des éléments qui ne sont pas définis dans les spécifications. Le modèle de programmation de syndication de Windows Communication Foundation (WCF) offre les moyens suivants d’utiliser des attributs personnalisés et des extensions, un accès faiblement typé et la dérivation d’une nouvelle classe.  
  
## <a name="loosely-typed-access"></a>Accès peu typé  

 L’ajout des extensions en dérivant une classe nouvelle requiert l’écriture de code supplémentaire. Une autre option accède aux extensions d’une manière peu typée. Tous les types définis dans le modèle de données abstraites de syndication contiennent des propriétés nommées `AttributeExtensions` et `ElementExtensions` (avec une exception, <xref:System.ServiceModel.Syndication.SyndicationContent> possède une propriété `AttributeExtensions` mais aucune propriété `ElementExtensions` ). Ces propriétés sont des collections d'extensions non traitées par les méthodes `TryParseAttribute` et `TryParseElement`, respectivement. Vous pouvez accéder à ces extensions non traitées en appelant <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection.ReadElementExtensions%2A?displayProperty=nameWithType> sur la propriété `ElementExtensions` de <xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationPerson> et <xref:System.ServiceModel.Syndication.SyndicationCategory>. Ce jeu de méthodes recherche toutes les extensions avec le nom et l'espace de noms spécifiés, les désérialise individuellement dans les instances de `TExtension` et les retourne comme une collection d'objets `TExtension`.  
  
## <a name="deriving-a-new-class"></a>Dérivation d'une nouvelle classe  

 Vous pouvez dériver une classe nouvelle à partir des classes de modèle de données abstraites existantes. Procédez ainsi lors de l’implémentation d’une application dans laquelle la plupart des flux que vous utilisez ont une extension particulière. Dans cette rubrique, la plupart des flux que le programme utilise contiennent une extension `MyExtension`. Pour fournir une expérience de programmation améliorée, procédez comme suit :  
  
- Créez une classe pour contenir les données d’extension. Dans ce cas, créez une classe appelée MyExtension.  
  
- Dérivez une classe appelée MyExtensionItem de <xref:System.ServiceModel.Syndication.SyndicationItem> pour exposer une propriété de type MyExtension à des fins de programmabilité.  
  
- Substituez <xref:System.ServiceModel.Syndication.SyndicationItem.TryParseElement%28System.Xml.XmlReader%2CSystem.String%29> dans la classe MyExtensionItem pour instancier une nouvelle instance MyExtension lorsqu'un MyExtension est lu.  
  
- Substituez <xref:System.ServiceModel.Syndication.SyndicationItem.WriteElementExtensions%28System.Xml.XmlWriter%2CSystem.String%29> dans la classe MyExtensionItem pour écrire le contenu de la propriété MyExtension dans un enregistreur XML.  
  
- Dérivez une classe appelée MyExtensionFeed de <xref:System.ServiceModel.Syndication.SyndicationFeed>.  
  
- Substituez <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateItem> dans la classe MyExtensionFeed pour instancier un MyExtensionItem au lieu du <xref:System.ServiceModel.Syndication.SyndicationItem> par défaut. Une série de méthodes est définie dans <xref:System.ServiceModel.Syndication.SyndicationFeed> et <xref:System.ServiceModel.Syndication.SyndicationItem> qui peut créer des objets <xref:System.ServiceModel.Syndication.SyndicationLink>, <xref:System.ServiceModel.Syndication.SyndicationCategory> et <xref:System.ServiceModel.Syndication.SyndicationPerson> (par exemple, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateLink>, <xref:System.ServiceModel.Syndication.SyndicationFeed.CreateCategory>et <xref:System.ServiceModel.Syndication.SyndicationFeed.CreatePerson>). Toutes ces méthodes peuvent être substituées pour créer une classe dérivée personnalisée.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de la syndication WCF](wcf-syndication-overview.md)
- [Architecture de syndication](architecture-of-syndication.md)
