---
title: 'Procédure : Récupérer des informations sur les conflits entre membres'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 4848ef69914f0520d2365538faea7fa064c1a15c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155807"
---
# <a name="how-to-retrieve-member-conflict-information"></a>Procédure : Récupérer des informations sur les conflits entre membres

Vous pouvez utiliser la classe <xref:System.Data.Linq.MemberChangeConflict> pour récupérer des informations sur des membres individuels en conflit. Dans ce contexte, vous pouvez assurer la gestion personnalisée du conflit pour un membre quelconque. Pour plus d’informations, consultez [accès concurrentiel optimiste : vue d’ensemble](optimistic-concurrency-overview.md).  
  
## <a name="example"></a>Exemple  

 Le code suivant itère au sein des objets <xref:System.Data.Linq.ObjectChangeConflict>. Pour chacun de ces objets, il itère ensuite au sein des objets <xref:System.Data.Linq.MemberChangeConflict>.  
  
> [!NOTE]
> Incluez <xref:System.Reflection> pour fournir des informations <xref:System.Data.Linq.MemberChangeConflict.Member%2A>.  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : Gérer les conflits de changement](how-to-manage-change-conflicts.md)
