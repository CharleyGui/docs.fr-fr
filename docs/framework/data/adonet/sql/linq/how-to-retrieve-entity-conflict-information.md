---
title: 'Procédure : Récupérer des informations sur les conflits entre entités'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: 766ede90b14f07e2799c2715daf62aaeeeaa83f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782238"
---
# <a name="how-to-retrieve-entity-conflict-information"></a>Procédure : Récupérer des informations sur les conflits entre entités
Vous pouvez utiliser des objets de la classe <xref:System.Data.Linq.ObjectChangeConflict> pour fournir des informations sur des conflits révélés par des exceptions <xref:System.Data.Linq.ChangeConflictException>. Pour plus d’informations, [consultez accès concurrentiel optimiste : Vue](optimistic-concurrency-overview.md)d’ensemble.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant itère au sein d'une liste de conflits cumulés.  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Gérer les conflits de modification](how-to-manage-change-conflicts.md)
