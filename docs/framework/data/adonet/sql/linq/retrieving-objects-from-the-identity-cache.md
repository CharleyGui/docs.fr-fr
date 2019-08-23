---
title: Récupération d'objets du cache d'identité
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: ef771d924d9b508c29061f75a45808b5f81abb53
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963834"
---
# <a name="retrieving-objects-from-the-identity-cache"></a>Récupération d'objets du cache d'identité
Cette rubrique décrit les types des requêtes LINQ to SQL qui retournent un objet à partir du cache d'identité qui est géré par le <xref:System.Data.Linq.DataContext>.  
  
 Dans LINQ to SQL, l'une des façons utilisées par le <xref:System.Data.Linq.DataContext> pour gérer les objets consiste à journaliser les identités d'objet dans un cache d'identité au fur et à mesure que les requêtes sont exécutées. Dans certains cas, LINQ to SQL essaie de récupérer un objet à partir du cache d'identité avant l'exécution d'une requête dans la base de données.  
  
 Généralement, pour qu'une requête LINQ to SQL retourne un objet à partir du cache d'identité, la requête doit être basée sur la clé primaire d'un objet et doit retourner un objet unique. En particulier, la requête doit se présenter sous l'une des formes générales suivantes.  
  
> [!NOTE]
> Les requêtes précompilées ne retournent pas d'objets à partir du cache d'identité. Pour plus d’informations sur les requêtes précompilées <xref:System.Data.Linq.CompiledQuery> , [consultez et procédure: Stocker et réutiliser](../../../../../../docs/framework/data/adonet/sql/linq/how-to-store-and-reuse-queries.md)des requêtes.  
  
 Une requête doit se présenter sous l'une des formes générales suivantes pour pouvoir récupérer un objet à partir du cache d'identité :  
  
- <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`  
  
- <xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`  
  
 Dans ces formes générales, `Function1`, `Function2` et `predicate` sont définis comme suit.  
  
 `Function1` peut être l'une des fonctions suivantes :  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `Function2` peut être l'une des fonctions suivantes :  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 `predicate` doit être une expression dans laquelle la propriété de la clé primaire de l'objet est définie sur une valeur constante. Si la clé primaire d'un objet est définie par plusieurs propriétés, chaque propriété de clé primaire doit être définie sur une valeur constante. Vous trouverez ci-dessous des exemples de formes requises pour `predicate` :  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a>Exemple  
 Le code suivant fournit des exemples de types de requêtes LINQ to SQL qui récupèrent un objet à partir du cache d'identité.  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Identité d’un objet](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
- [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Identité d’un objet](../../../../../../docs/framework/data/adonet/sql/linq/object-identity.md)
