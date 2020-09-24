---
title: 'Procédure : Demander des informations'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: d45fdfa8b8976e3cdc86b905443bf7bcea578714
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166402"
---
# <a name="how-to-query-for-information"></a>Procédure : Demander des informations

Les requêtes dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] utilisent la même syntaxe que les requêtes dans LINQ. La seule différence est que les objets référencés dans les [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requêtes sont mappés aux éléments d’une base de données. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez en requêtes SQL équivalentes et les envoie au serveur pour traitement.  
  
 Certaines fonctionnalités des requêtes LINQ peuvent nécessiter une attention particulière dans les [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications. Pour plus d’informations, consultez [concepts de requête](query-concepts.md).  
  
## <a name="example"></a>Exemple  

 La requête suivante demande une liste de clients de Londres. Dans cet exemple, `Customers` est une table de l'exemple de base de données Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Création du modèle objet](creating-the-object-model.md)
- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
- [Interrogation de la base de données](querying-the-database.md)
