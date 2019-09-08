---
title: Prise en main
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: bd82b7e83149aaa53cf1b240cb79f8747bccba47
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793917"
---
# <a name="getting-started"></a>Prise en main
À l' [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]aide de, vous pouvez [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] utiliser la technologie pour accéder aux bases de données SQL, tout comme vous accéderiez à une collection en mémoire.  
  
 Par exemple, l'objet `nw` dans le code suivant est créé pour représenter la base de données `Northwind`, la table `Customers` est ciblée, les lignes sont filtrées sur `Customers` à partir de `London`, et une chaîne pour `CompanyName` est sélectionnée pour la récupération.  
  
 Lors de l’exécution de la boucle, la collection de valeurs `CompanyName` est récupérée.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Étapes suivantes  
 Pour obtenir des exemples supplémentaires, notamment l’insertion et la mise à jour, consultez [ce que vous pouvez faire avec LINQ to SQL](what-you-can-do-with-linq-to-sql.md).  
  
 Suivez ensuite des procédures pas à pas et des didacticiels pour bénéficier d'une expérience pratique de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Consultez [l’apprentissage par les procédures pas à pas](learning-by-walkthroughs.md).  
  
 Enfin, Découvrez comment prendre en main votre propre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projet en lisant les [étapes typiques de l’utilisation de LINQ to SQL](typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Voir aussi

- [LINQ to SQL](index.md)
- [Présentation de LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Introduction à LINQ (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Modèle objet LINQ to SQL](the-linq-to-sql-object-model.md)
