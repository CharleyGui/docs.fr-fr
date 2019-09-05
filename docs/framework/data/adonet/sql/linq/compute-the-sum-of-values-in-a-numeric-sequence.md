---
title: 'Comment : calculer la somme de valeurs dans une séquence numérique'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 24e335b0-984e-4825-8721-0a91b533b7c3
ms.openlocfilehash: 3a404068c2d89610aa9b01b392bca40f82e17707
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70247924"
---
# <a name="compute-the-sum-of-values-in-a-numeric-sequence"></a>Comment : calculer la somme de valeurs dans une séquence numérique
Utilisez l'opérateur <xref:System.Linq.Enumerable.Sum%2A> pour calculer la somme des valeurs numériques dans une séquence.  
  
 Notez les caractéristiques suivantes de l'opérateur `Sum` dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :  
  
- L'opérateur d'agrégation (opérateur de requête standard) `Sum` prend la valeur zéro pour une séquence vide ou contenant uniquement des valeurs null. Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], la sémantique de SQL reste inchangée. `Sum` prend donc la valeur null plutôt que la valeur zéro pour une séquence vide ou contenant uniquement des valeurs null.  
  
- Les limitations SQL sur les résultats intermédiaires s'appliquent aux agrégats dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. La somme des quantités d’entiers 32 bits n’est pas calculée à l’aide des résultats 64 bits et le dépassement de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] capacité peut `Sum`se produire pour la traduction de. Ce risque existe même si l'implémentation de l'opérateur de requête standard n'entraîne pas de dépassement de capacité pour la séquence en mémoire correspondante.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant recherche les frais de transport totaux pour toutes les commandes de la table `Order`.  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `64942.6900`.  
  
 [!code-csharp[DLinqQueryExamples#12](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#12)]
 [!code-vb[DLinqQueryExamples#12](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#12)]  
  
## <a name="example"></a>Exemples  
 L'exemple suivant recherche le nombre total d'unités commandées pour tous les produits.  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, vous obtenez le résultat suivant : `780`.  
  
 Notez que vous devez effectuer un cast des types `short` (par exemple, `UnitsOnOrder`) car `Sum` n'a aucune surcharge pour les types courts.  
  
 [!code-csharp[DLinqQueryExamples#13](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#13)]
 [!code-vb[DLinqQueryExamples#13](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#13)]  
  
## <a name="see-also"></a>Voir aussi

- [Requêtes d’agrégation](aggregate-queries.md)
- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
