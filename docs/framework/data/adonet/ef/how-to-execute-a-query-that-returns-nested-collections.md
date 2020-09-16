---
title: 'Procédure : Exécuter une requête qui retourne des collections imbriquées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: b3a5e3707ee1375ed95159b869e27f3847a67aed
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545270"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a>Procédure : Exécuter une requête qui retourne des collections imbriquées
Cette rubrique indique comment exécuter une commande sur un modèle conceptuel en utilisant un objet <xref:System.Data.EntityClient.EntityCommand> et comment récupérer les collections imbriquées obtenues à l'aide d'un objet <xref:System.Data.EntityClient.EntityDataReader>.  
  
### <a name="to-run-the-code-in-this-example"></a>Pour exécuter le code de cet exemple  
  
1. Ajoutez le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) à votre projet et configurez votre projet pour qu’il utilise le Entity Framework. Pour plus d’informations, consultez [Comment : utiliser l’assistant Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
2. Dans la page de codes de votre application, ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a> Exemple  
 Une *collection imbriquée* est une collection qui se trouve à l’intérieur d’une autre collection. Le code suivant récupère une collection d’éléments `Contacts` et les collections imbriquées de `SalesOrderHeaders` qui sont associées à chaque élément `Contact`.  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a>Voir aussi

- [Fournisseur EntityClient pour Entity Framework](entityclient-provider-for-the-entity-framework.md)
