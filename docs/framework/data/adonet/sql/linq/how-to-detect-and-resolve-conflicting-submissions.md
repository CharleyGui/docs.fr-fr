---
title: 'Procédure : Détecter et résoudre des soumissions en conflit'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 96e96208d9bb28092701164e6cd5943ef81515a5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147721"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a>Procédure : Détecter et résoudre des soumissions en conflit

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit de nombreuses ressources pour détecter et résoudre des conflits issus de modifications effectuées par plusieurs utilisateurs dans la base de données. Pour plus d’informations, consultez [Comment : gérer les conflits de modifications](how-to-manage-change-conflicts.md).  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre un `try` / `catch` bloc qui intercepte <xref:System.Data.Linq.ChangeConflictException> une exception. La fenêtre de console affiche des informations sur les entités et les membres de chaque conflit.  
  
> [!NOTE]
> Vous devez inclure la directive `using System.Reflection` (`Imports System.Reflection` dans Visual Basic) pour prendre en charge la récupération d'informations. Pour plus d'informations, consultez <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Apport et soumission de modifications de données](making-and-submitting-data-changes.md)
- [Procédure : Gérer les conflits de changement](how-to-manage-change-conflicts.md)
