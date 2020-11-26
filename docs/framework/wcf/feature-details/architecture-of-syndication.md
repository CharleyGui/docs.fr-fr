---
title: Architecture de syndication
ms.date: 03/30/2017
ms.assetid: ed4ca86e-e3d8-4acb-87aa-1921fbc353be
ms.openlocfilehash: bc8c9cfbdc4f5d8ee01dfcf5098cfbc74afc2467
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234802"
---
# <a name="architecture-of-syndication"></a>Architecture de syndication

L'API de syndication est conçue pour fournir un modèle de programmation neutre en ce qui concerne le format qui autorise l'écriture du contenu syndiqué sur le fil dans divers formats. Le modèle de données abstrait inclut les classes suivantes :  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 Ces classes mappent précisément aux constructions définies dans la spécification Atom 1.0, bien que certains noms soient différents.  
  
 Dans Windows Communication Foundation (WCF), les flux de syndication sont modelés comme un autre type d’opération de service, un où le type de retour est l’une des classes dérivées de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> . La récupération d'un flux est modelée comme un échange de messages de demande-réponse. Un client envoie une demande au service et le service répond. Le message de requête est défini sur un protocole d'infrastructure (HTTP brut, par exemple) et le message de réponse contient une charge utile qui se compose d'un format de syndication (RSS 2.0 ou Atom 1.0) communément compris. Les services qui implémentent ces échanges de messages sont appelés « services de syndication ».  
  
 Le contrat pour un service de syndication se compose d'un jeu d'opérations qui retourne une instance de la classe <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. L'exemple suivant montre une déclaration d'interface pour un service de syndication.  
  
 [!code-csharp[S_UE_SyndicationBoth#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_syndicationboth/cs/service.cs#0)]  
  
 La prise en charge de la syndication repose sur le modèle de programmation WCF REST qui définit la <xref:System.ServiceModel.WebHttpBinding> liaison utilisée conjointement avec <xref:System.ServiceModel.Description.WebHttpBehavior> pour rendre les flux disponibles en tant que services. Pour plus d’informations sur le modèle de programmation WCF REST, consultez [vue d’ensemble du modèle de programmation http Web WCF](wcf-web-http-programming-model-overview.md).  
  
> [!NOTE]
> La spécification Atom 1.0 permet de spécifier des fractions de seconde dans l'un de ses constructeurs Date. Lors de la sérialisation et de la désérialisation de l’implémentation WCF, les fractions de seconde sont ignorées.  
  
## <a name="object-model"></a>Modèle objet  

 Le modèle objet pour la syndication se compose de groupes de classes répertoriés dans les tableaux suivants.  
  
 Classes de formatage :  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter>|Classe chargée de sérialiser une instance <xref:System.ServiceModel.Syndication.SyndicationFeed> au format Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601>|Classe chargée de sérialiser des classes dérivées de <xref:System.ServiceModel.Syndication.SyndicationFeed> au format Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter>|Classe chargée de sérialiser une instance <xref:System.ServiceModel.Syndication.SyndicationItem> au format Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601>|Classe chargée de sérialiser des classes dérivées de <xref:System.ServiceModel.Syndication.SyndicationItem> au format Atom 1.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>|Classe chargée de sérialiser une instance <xref:System.ServiceModel.Syndication.SyndicationFeed> au format RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601>|Classe chargée de sérialiser des classes dérivées de <xref:System.ServiceModel.Syndication.SyndicationFeed> au format RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter>|Classe chargée de sérialiser une instance <xref:System.ServiceModel.Syndication.SyndicationItem> au format RSS 2.0.|  
|<xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601>|Classe chargée de sérialiser des classes dérivées de <xref:System.ServiceModel.Syndication.SyndicationItem> au format RSS 2.0.|  
  
 Classes de modèle objet :  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Syndication.SyndicationCategory>|Classe qui représente la catégorie d'un flux de syndication.|  
|<xref:System.ServiceModel.Syndication.SyndicationContent>|Classe de base qui représente le contenu de syndication.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtension>|Classe représentant une extension d’élément de syndication.|  
|<xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>|Collection d'objets <xref:System.ServiceModel.Syndication.SyndicationElementExtension>.|  
|<xref:System.ServiceModel.Syndication.SyndicationFeed>|Classe qui représente un objet de flux de niveau supérieur.|  
|<xref:System.ServiceModel.Syndication.SyndicationItem>|Classe qui représente un élément de flux.|  
|<xref:System.ServiceModel.Syndication.SyndicationLink>|Classe qui représente un lien dans un flux ou un élément de syndication.|  
|<xref:System.ServiceModel.Syndication.SyndicationPerson>|Classe qui représente une construction Atom Person.|  
|<xref:System.ServiceModel.Syndication.SyndicationVersions>|Classe qui représente les versions du protocole de syndication prises en charge.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContent>|Classe qui représente tout contenu <xref:System.ServiceModel.Syndication.SyndicationItem> à afficher pour un utilisateur final.|  
|<xref:System.ServiceModel.Syndication.TextSyndicationContentKind>|Énumération qui représente les différents types de contenu de syndication de texte pris en charge.|  
|<xref:System.ServiceModel.Syndication.UrlSyndicationContent>|Classe qui représente un contenu de syndication qui se compose d'une URL à une autre ressource.|  
|<xref:System.ServiceModel.Syndication.XmlSyndicationContent>|Classe qui représente un contenu de syndication qui ne sera pas affiché dans un navigateur.|  
  
 Les abstractions des données principales dans le modèle objet sont Flux et Élément, qui correspondent aux classes <xref:System.ServiceModel.Syndication.SyndicationFeed> et <xref:System.ServiceModel.Syndication.SyndicationItem>. Un flux expose des métadonnées (par exemple, Title, Description et Author) au niveau du flux, un emplacement pour stocker des extensions inconnues et un jeu d’éléments qui composent le reste du contenu d’information du flux. Un élément met à disposition les métadonnées (par exemple, Title, Summary et PublicationDate) au niveau de l’élément, un emplacement pour stocker des extensions inconnues et un élément de contenu qui contient le reste du contenu d’information de l’élément. Les abstractions principales de Flux et Élément sont prises en charge par des classes supplémentaires qui représentent des constructions de données communes référencées dans les spécifications Atom 1.0 et RSS.  
  
 Les informations contenues dans une instance de flux peuvent être converties en divers formats XML. Le processus de conversion vers et depuis XML est géré par la classe <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. Cette classe est abstraite ; les implémentations concrètes sont fournies pour Atom 1.0 et RSS 2.0, <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> et <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>. Pour utiliser des classes Feed dérivées, utilisez <xref:System.ServiceModel.Syndication.Atom10FeedFormatter%601> ou <xref:System.ServiceModel.Syndication.Rss20FeedFormatter%601> car ils vous permettent de spécifier une classe Feed dérivée. Pour utiliser des classes d'élément dérivées utilisez <xref:System.ServiceModel.Syndication.Atom10ItemFormatter%601> ou <xref:System.ServiceModel.Syndication.Rss20ItemFormatter%601> car ils vous permettent de spécifier une classe d'élément dérivée. Les tiers peuvent dériver leur propre implémentation de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> pour prendre en charge des formats de syndication différents.  
  
## <a name="extensibility"></a>Extensibilité  
  
- L’une des fonctionnalités clés de protocoles de syndication est l’extensibilité. Atom 1.0 et RSS 2.0 vous permettent d'ajouter aux flux de syndication des attributs et des éléments qui ne sont pas définis dans les spécifications. Le modèle de programmation de syndication WCF offre deux façons d’utiliser des attributs personnalisés et des extensions : la dérivation d’une nouvelle classe et l’accès faiblement typé. Pour plus d’informations, consultez extensibilité de la [syndication](syndication-extensibility.md).  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de la syndication WCF](wcf-syndication-overview.md)
- [Comment le modèle objet Syndication WCF est mappé à Atom et RSS](how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)
- [Modèle de programmation HTTP Web WCF](wcf-web-http-programming-model.md)
