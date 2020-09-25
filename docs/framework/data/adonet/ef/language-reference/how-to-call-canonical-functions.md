---
title: 'Comment : appeler des fonctions de chaînes canoniques'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: acfbdbaf21fe1d454b68dfef5bf4f88d8020ea65
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204448"
---
# <a name="how-to-call-canonical-functions"></a>Comment : appeler des fonctions de chaînes canoniques

La classe <xref:System.Data.Objects.EntityFunctions> contient des méthodes qui exposent les fonctions canoniques à utiliser dans les requêtes LINQ to Entities. Pour plus d’informations sur les fonctions canoniques, consultez [Fonctions canoniques](canonical-functions.md).  
  
> [!NOTE]
> Les méthodes <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> et <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> dans la classe <xref:System.Data.Objects.EntityFunctions> n'ont pas d'équivalents de fonction canonique.  
  
 Les fonctions canoniques qui effectuent un calcul sur un ensemble de valeurs et retournent une valeur unique (également appelées fonctions canoniques d'agrégation) peuvent être appelées directement. Les autres fonctions canoniques peuvent être appelées uniquement dans le cadre d'une requête LINQ to Entities. Pour appeler directement une fonction d'agrégation, vous devez passer un objet <xref:System.Data.Objects.ObjectQuery%601> à la fonction. Pour plus d'informations, consultez le second exemple ci-dessous.  
  
 Vous pouvez appeler certaines fonctions canoniques en utilisant des méthodes CLR (Common Language Runtime) dans les requêtes LINQ to Entities. Pour obtenir la liste des méthodes CLR qui mappent aux fonctions canoniques, consultez [méthode CLR pour le mappage de fonction canonique](clr-method-to-canonical-function-mapping.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). L'exemple exécute une requête LINQ to Entities qui utilise la méthode <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> pour retourner tous les produits pour lesquels la différence entre `SellEndDate` et `SellStartDate` est inférieure à 365 jours :  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a>Exemple  

 L’exemple suivant utilise le [modèle de vente AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks). L'exemple appelle directement la méthode <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> d'agrégation pour retourner l'écart type des sous-totaux `SalesOrderHeader`. Notez qu'un <xref:System.Data.Objects.ObjectQuery%601> est passé à la fonction, ce qui lui permet d'être appelée même si elle ne figure pas dans une requête LINQ to Entities.  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Appel de fonctions dans les requêtes LINQ to Entities](calling-functions-in-linq-to-entities-queries.md)
- [Requêtes dans LINQ to Entities](queries-in-linq-to-entities.md)
