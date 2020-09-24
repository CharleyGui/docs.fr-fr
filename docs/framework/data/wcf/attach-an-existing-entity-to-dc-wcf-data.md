---
title: 'Comment : attacher une entité existante au DataServiceContext (services de données WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 69ca64f4ab3470c1a4f58c582b31c06aed9cadd5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166129"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Comment : attacher une entité existante au DataServiceContext (services de données WCF)

Lorsqu’une entité existe déjà dans un service de données, la bibliothèque cliente WCF Data Services vous permet de joindre un objet qui représente directement l’entité au <xref:System.Data.Services.Client.DataServiceContext> sans exécuter d’abord une requête. Pour plus d’informations, consultez [mise à jour du service de données](updating-the-data-service-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  

 L'exemple suivant montre comment créer un objet `Customer` existant qui contient des modifications à enregistrer dans le service de données. L'objet est joint au contexte et la méthode <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> est appelée pour marquer l'objet joint comme <xref:System.Data.Services.Client.EntityStates.Modified> avant d'appeler la méthode <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
