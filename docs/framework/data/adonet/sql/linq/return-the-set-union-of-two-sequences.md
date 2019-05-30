---
title: Retourner l'union définie de deux séquences
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 9ade12c42ac6a307c341bc5be26430fb56e51ee5
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380038"
---
# <a name="return-the-set-union-of-two-sequences"></a>Retourner l'union définie de deux séquences
Utilisez l'opérateur <xref:System.Linq.Queryable.Union%2A> pour retourner l'union définie de deux séquences.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise <xref:System.Linq.Queryable.Union%2A> pour retourner une séquence de tous les pays/régions dans lesquels sont soit `Customers` ou `Employees`.  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], le <xref:System.Linq.Queryable.Union%2A> opérateur est défini pour des multijeux comme la concaténation non ordonnée des multijeux (le résultat de la [ `UNION ALL` ](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) clause dans SQL).

Pour plus d’informations et des exemples, consultez <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>.
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Traduction des opérateurs de requête standard](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
