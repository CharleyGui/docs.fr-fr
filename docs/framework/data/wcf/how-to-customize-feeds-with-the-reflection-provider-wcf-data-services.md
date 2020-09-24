---
title: 'Comment : personnaliser les flux avec le fournisseur de réflexion (services de données WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: fb22e87569a8e243813b3186232b6989abeb2a5e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161306"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>Comment : personnaliser les flux avec le fournisseur de réflexion (services de données WCF)

WCF Data Services vous permet de personnaliser la sérialisation Atom dans une réponse du service de données afin que les propriétés d’une entité puissent être mappées aux éléments inutilisés définis dans le protocole AtomPub. Cette rubrique indique comment définir des attributs de mappage pour les types d'entité dans un modèle de données défini à l'aide du fournisseur de réflexion. Pour plus d’informations, consultez [Personnalisation des flux](feed-customization-wcf-data-services.md).  
  
 Le modèle de données de cet exemple est défini dans la rubrique [Comment : créer un service de données à l’aide du fournisseur de réflexion](create-a-data-service-using-rp-wcf-data-services.md) .  
  
## <a name="example"></a>Exemple  

 Dans l'exemple suivant, les deux propriétés du type `Order` sont mappées aux éléments Atom existants. La propriété `Product` du type `Item` est mappée à un attribut de flux personnalisé dans un espace de noms séparé.  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>Exemple  

 L'exemple précédent retourne le résultat suivant pour l'URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseur de réflexion](reflection-provider-wcf-data-services.md)
