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
ms.openlocfilehash: d3e2d587978a4c82784c8cfc8a7acc17cf601c3a
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569144"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="1d89b-102">Comment : personnaliser les flux avec le fournisseur de réflexion (services de données WCF)</span><span class="sxs-lookup"><span data-stu-id="1d89b-102">How to: Customize Feeds with the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="1d89b-103">WCF Data Services vous permet de personnaliser la sérialisation Atom dans une réponse du service de données afin que les propriétés d’une entité puissent être mappées aux éléments inutilisés définis dans le protocole AtomPub.</span><span class="sxs-lookup"><span data-stu-id="1d89b-103">WCF Data Services enables you to customize the Atom serialization in a data service response so that properties of an entity may be mapped to unused elements that are defined in the AtomPub protocol.</span></span> <span data-ttu-id="1d89b-104">Cette rubrique indique comment définir des attributs de mappage pour les types d'entité dans un modèle de données défini à l'aide du fournisseur de réflexion.</span><span class="sxs-lookup"><span data-stu-id="1d89b-104">This topic shows how to define mapping attributes for the entity types in a data model that is defined by using the reflection provider.</span></span> <span data-ttu-id="1d89b-105">Pour plus d’informations, consultez [Personnalisation des flux](feed-customization-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="1d89b-105">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="1d89b-106">Le modèle de données de cet exemple est défini dans la rubrique [Comment : créer un service de données à l’aide du fournisseur de réflexion](create-a-data-service-using-rp-wcf-data-services.md) .</span><span class="sxs-lookup"><span data-stu-id="1d89b-106">The data model for this example is defined in the topic [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md)</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d89b-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d89b-107">Example</span></span>  
 <span data-ttu-id="1d89b-108">Dans l'exemple suivant, les deux propriétés du type `Order` sont mappées aux éléments Atom existants.</span><span class="sxs-lookup"><span data-stu-id="1d89b-108">In the following example, both properties of the `Order` type are mapped to existing Atom elements.</span></span> <span data-ttu-id="1d89b-109">La propriété `Product` du type `Item` est mappée à un attribut de flux personnalisé dans un espace de noms séparé.</span><span class="sxs-lookup"><span data-stu-id="1d89b-109">The `Product` property of the `Item` type is mapped to a custom feed attribute in a separate namespace.</span></span>  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_custom_feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_custom_feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a><span data-ttu-id="1d89b-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d89b-110">Example</span></span>  
 <span data-ttu-id="1d89b-111">L'exemple précédent retourne le résultat suivant pour l'URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span><span class="sxs-lookup"><span data-stu-id="1d89b-111">The previous example returns the following result for the URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items`.</span></span>  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a><span data-ttu-id="1d89b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d89b-112">See also</span></span>

- [<span data-ttu-id="1d89b-113">Fournisseur de réflexion</span><span class="sxs-lookup"><span data-stu-id="1d89b-113">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
