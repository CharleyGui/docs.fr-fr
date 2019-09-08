---
title: 'Procédure : Spécifier le moment où des exceptions d’accès concurrentiel sont levées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: c0f41d23264bbe5c9130cb5a0b03686331bc92b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781619"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Procédure : Spécifier le moment où des exceptions d’accès concurrentiel sont levées
Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque des objets ne sont pas mis à jour en raison de conflits d'accès concurrentiel optimiste. Pour plus d’informations, [consultez accès concurrentiel optimiste : Vue](optimistic-concurrency-overview.md)d’ensemble.  
  
 Avant de soumettre vos modifications à la base de données, vous pouvez spécifier quand des exceptions d'accès concurrentiel doivent être levées :  
  
- Lever l'exception au premier échec (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
- Terminer toutes les tentatives de mise à jour, cumuler les échecs et signaler les échecs cumulés dans l'exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).  
  
 Lorsqu’elle est levée, l’exception <xref:System.Data.Linq.ChangeConflictException> donne accès à une collection <xref:System.Data.Linq.ChangeConflictCollection>. Cette collection fournit des détails pour chaque conflit (mappé à une seule tentative de mise à jour non réussie), y compris l'accès à la collection <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A>. Chaque conflit entre membres mappe à un seul membre dans la mise à jour au cours de laquelle le contrôle d'accès concurrentiel a échoué.  
  
## <a name="example"></a>Exemple  
 Le code suivant présente des exemples des deux valeurs.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique : Gérer les conflits de modification](how-to-manage-change-conflicts.md)
- [Apport et soumission de modifications de données](making-and-submitting-data-changes.md)
