---
title: 'Procédure : Mettre entre parenthèses des soumissions de données à l’aide de transactions'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
ms.openlocfilehash: 6a4c5ba7c4938b48fe489e43ff4a3ff806bd8916
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793808"
---
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a><span data-ttu-id="8ff9f-102">Procédure : Mettre entre parenthèses des soumissions de données à l’aide de transactions</span><span class="sxs-lookup"><span data-stu-id="8ff9f-102">How to: Bracket Data Submissions by Using Transactions</span></span>
<span data-ttu-id="8ff9f-103">Vous pouvez utiliser <xref:System.Transactions.TransactionScope> pour mettre entre parenthèses vos soumissions à la base de données.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-103">You can use <xref:System.Transactions.TransactionScope> to bracket your submissions to the database.</span></span> <span data-ttu-id="8ff9f-104">Pour plus d’informations, consultez [prise en charge des transactions](transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="8ff9f-104">For more information, see [Transaction Support](transaction-support.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ff9f-105">Exemples</span><span class="sxs-lookup"><span data-stu-id="8ff9f-105">Example</span></span>  
 <span data-ttu-id="8ff9f-106">Le code suivant place la soumission de base de données dans un <xref:System.Transactions.TransactionScope>.</span><span class="sxs-lookup"><span data-stu-id="8ff9f-106">The following code encloses the database submission in a <xref:System.Transactions.TransactionScope>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8ff9f-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ff9f-107">See also</span></span>

- [<span data-ttu-id="8ff9f-108">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="8ff9f-108">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="8ff9f-109">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="8ff9f-109">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="8ff9f-110">Prise en charge des transactions</span><span class="sxs-lookup"><span data-stu-id="8ff9f-110">Transaction Support</span></span>](transaction-support.md)
