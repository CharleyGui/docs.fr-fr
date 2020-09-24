---
title: 'Procédure : Mettre entre parenthèses des soumissions de données à l’aide de transactions'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 4d3efedbf15be55fa7a9ab235f881f1c97758953
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161358"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="1f470-102">Procédure : Mettre entre parenthèses des soumissions de données à l’aide de transactions</span><span class="sxs-lookup"><span data-stu-id="1f470-102">How to: Bracket Data Submissions by Using Transactions</span></span>

<span data-ttu-id="1f470-103">Vous pouvez utiliser <xref:System.Transactions.TransactionScope> pour mettre entre parenthèses vos soumissions à la base de données.</span><span class="sxs-lookup"><span data-stu-id="1f470-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="1f470-104">Pour plus d’informations, consultez [prise en charge des transactions](transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="1f470-104">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f470-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f470-105">Example</span></span>  

 <span data-ttu-id="1f470-106">Le code suivant place la soumission de base de données dans un <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="1f470-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1f470-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f470-107">See also</span></span>

- [<span data-ttu-id="1f470-108">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="1f470-108">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="1f470-109">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="1f470-109">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="1f470-110">Prise en charge des transactions</span><span class="sxs-lookup"><span data-stu-id="1f470-110">Transaction Support</span></span>](transaction-support.md)
