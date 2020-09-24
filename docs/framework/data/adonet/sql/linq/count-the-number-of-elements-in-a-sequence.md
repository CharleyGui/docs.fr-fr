---
title: Dénombrer les éléments d'une séquence
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: d983bc14f4fda04bda0a6f363db4c11f062c4c48
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164348"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>Dénombrer les éléments d'une séquence

Utilisez l'opérateur <xref:System.Linq.Enumerable.Count%2A> pour compter le nombre d'éléments dans une séquence.  
  
 L'exécution de cette requête sur la base de données Northwind génère le résultat suivant : `91`.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant compte le nombre de `Customers` dans la base de données.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant compte le nombre de produits dans la base de données qui n'ont pas été arrêtés.  
  
 L'exécution de cet exemple sur la base de données Northwind génère le résultat suivant : `69`.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes d'agrégation](aggregate-queries.md)
- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
