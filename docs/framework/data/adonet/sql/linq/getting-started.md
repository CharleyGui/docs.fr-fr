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
# <a name="getting-started"></a><span data-ttu-id="488e1-103">Mise en route</span><span class="sxs-lookup"><span data-stu-id="488e1-103">Getting Started</span></span>

<span data-ttu-id="488e1-104">À l’aide de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , vous pouvez utiliser la technologie LINQ pour accéder aux bases de données SQL, tout comme vous accéderiez à une collection en mémoire.</span><span class="sxs-lookup"><span data-stu-id="488e1-104">By using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you can use the LINQ technology to access SQL databases just as you would access an in-memory collection.</span></span>  
  
 <span data-ttu-id="488e1-105">Par exemple, l'objet `nw` dans le code suivant est créé pour représenter la base de données `Northwind`, la table `Customers` est ciblée, les lignes sont filtrées sur `Customers` à partir de `London`, et une chaîne pour `CompanyName` est sélectionnée pour la récupération.</span><span class="sxs-lookup"><span data-stu-id="488e1-105">For example, the `nw` object in the following code is created to represent the `Northwind` database, the `Customers` table is targeted, the rows are filtered for `Customers` from `London`, and a string for `CompanyName` is selected for retrieval.</span></span>  
  
 <span data-ttu-id="488e1-106">Lors de l’exécution de la boucle, la collection de valeurs `CompanyName` est récupérée.</span><span class="sxs-lookup"><span data-stu-id="488e1-106">When the loop is executed, the collection of `CompanyName` values is retrieved.</span></span>  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a><span data-ttu-id="488e1-107">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="488e1-107">Next Steps</span></span>  

 <span data-ttu-id="488e1-108">Pour obtenir des exemples supplémentaires, notamment l’insertion et la mise à jour, consultez [ce que vous pouvez faire avec LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="488e1-108">For some additional examples, including inserting and updating, see [What You Can Do With LINQ to SQL](what-you-can-do-with-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="488e1-109">Suivez ensuite des procédures pas à pas et des didacticiels pour bénéficier d'une expérience pratique de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="488e1-109">Next, try some walkthroughs and tutorials to have a hands-on experience of using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="488e1-110">Consultez [l’apprentissage par les procédures pas à pas](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="488e1-110">See [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>  
  
 <span data-ttu-id="488e1-111">Enfin, Découvrez comment prendre en main votre propre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projet en lisant les [étapes typiques de l’utilisation de LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="488e1-111">Finally, learn how to get started on your own [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project by reading [Typical Steps for Using LINQ to SQL](typical-steps-for-using-linq-to-sql.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488e1-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="488e1-112">See also</span></span>

- [<span data-ttu-id="488e1-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="488e1-113">LINQ to SQL</span></span>](index.md)
- [<span data-ttu-id="488e1-114">Présentation de LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="488e1-114">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="488e1-115">Introduction à LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="488e1-115">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [<span data-ttu-id="488e1-116">Modèle objet LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="488e1-116">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
