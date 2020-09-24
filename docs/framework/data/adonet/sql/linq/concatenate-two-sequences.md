---
title: Concaténer deux séquences
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 87d341357b8d11eafbc3f3867c45ac5a32270688
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164400"
---
# <a name="concatenate-two-sequences"></a>Concaténer deux séquences

Utilisez l'opérateur <xref:System.Linq.Queryable.Concat%2A> pour concaténer deux séquences.  
  
 L’opérateur <xref:System.Linq.Queryable.Concat%2A> est défini pour les multijeux ordonnés pour lesquels l’ordre du destinataire et de l’argument est identique.  
  
 Le classement dans SQL est la dernière étape avant la génération des résultats. Par conséquent, l’opérateur <xref:System.Linq.Queryable.Concat%2A> est implémenté en utilisant `UNION ALL` et ne conserve pas l’ordre de ses arguments. Pour vérifier que le classement est correct dans les résultats, assurez-vous de classer les résultats explicitement.  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise <xref:System.Linq.Queryable.Concat%2A> pour retourner une séquence de tous les numéros de téléphone et de télécopie de `Customer` et `Employee`.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise <xref:System.Linq.Queryable.Concat%2A> pour retourner une séquence de tous les mappages de nom et de numéro de téléphone de `Customer` et `Employee`.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Voir aussi

- [Exemples de requêtes](query-examples.md)
- [Traduction des opérateurs de requête standard](standard-query-operator-translation.md)
