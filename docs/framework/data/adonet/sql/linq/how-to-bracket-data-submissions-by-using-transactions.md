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
# <a name="how-to-bracket-data-submissions-by-using-transactions"></a>Procédure : Mettre entre parenthèses des soumissions de données à l’aide de transactions
Vous pouvez utiliser <xref:System.Transactions.TransactionScope> pour mettre entre parenthèses vos soumissions à la base de données. Pour plus d’informations, consultez [prise en charge des transactions](transaction-support.md).  
  
## <a name="example"></a>Exemples  
 Le code suivant place la soumission de base de données dans un <xref:System.Transactions.TransactionScope>.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
- [Apport et soumission de modifications de données](making-and-submitting-data-changes.md)
- [Prise en charge des transactions](transaction-support.md)
