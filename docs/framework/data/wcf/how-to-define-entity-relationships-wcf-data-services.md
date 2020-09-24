---
title: "Comment : définir les relations d'entité (services de données WCF)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: dec22f2f1e1d259e341100bce2b99d71540797db
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150633"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>Comment : définir les relations d'entité (services de données WCF)

Lorsque vous ajoutez une nouvelle entité dans WCF Data Services, les relations entre la nouvelle entité et les entités associées ne sont pas définies automatiquement. Vous pouvez créer et modifier les relations entre des instances d'entité et faire répercuter par la bibliothèque cliente ces modifications dans le service de données. Pour plus d’informations, consultez [mise à jour du service de données](updating-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  

 L'exemple suivant crée une nouvelle instance de l'objet puis appelle la méthode <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> sur <xref:System.Data.Services.Client.DataServiceContext> pour créer l'élément dans le contexte avec le lien vers l'ordre connexe. Un message HTTP POST est envoyé au service de données lorsque la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> est appelée.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant montre comment utiliser la méthode <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> pour ajouter un objet `Order_Details` à un objet `Orders` connexe avec une référence à un objet `Products` spécifique. Les méthodes <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> et <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> définissent les relations. Dans cet exemple, les propriétés de navigation sur l'objet `Order_Details` sont également définies explicitement.  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
- [Procédure : Ajouter, modifier et supprimer des entités](how-to-add-modify-and-delete-entities-wcf-data-services.md)
