---
title: Prise en main
description: Avec cet exemple de code, commencez à utiliser LINQ to SQL pour utiliser la technologie LINQ pour accéder aux bases de données SQL, tout comme vous accéderiez à une collection en mémoire.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: b886518d4cff687a18f363c3e3ba43b40631a22f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194373"
---
# <a name="getting-started"></a>Mise en route

À l’aide de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , vous pouvez utiliser la technologie LINQ pour accéder aux bases de données SQL, tout comme vous accéderiez à une collection en mémoire.  
  
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
