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
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="d60af-102">Procédure : Spécifier le moment où des exceptions d’accès concurrentiel sont levées</span><span class="sxs-lookup"><span data-stu-id="d60af-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="d60af-103">Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque des objets ne sont pas mis à jour en raison de conflits d'accès concurrentiel optimiste.</span><span class="sxs-lookup"><span data-stu-id="d60af-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="d60af-104">Pour plus d’informations, [consultez accès concurrentiel optimiste : Vue](optimistic-concurrency-overview.md)d’ensemble.</span><span class="sxs-lookup"><span data-stu-id="d60af-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="d60af-105">Avant de soumettre vos modifications à la base de données, vous pouvez spécifier quand des exceptions d'accès concurrentiel doivent être levées :</span><span class="sxs-lookup"><span data-stu-id="d60af-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="d60af-106">Lever l'exception au premier échec (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="d60af-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="d60af-107">Terminer toutes les tentatives de mise à jour, cumuler les échecs et signaler les échecs cumulés dans l'exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="d60af-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="d60af-108">Lorsqu’elle est levée, l’exception <xref:System.Data.Linq.ChangeConflictException> donne accès à une collection <xref:System.Data.Linq.ChangeConflictCollection>.</span><span class="sxs-lookup"><span data-stu-id="d60af-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="d60af-109">Cette collection fournit des détails pour chaque conflit (mappé à une seule tentative de mise à jour non réussie), y compris l'accès à la collection <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A>.</span><span class="sxs-lookup"><span data-stu-id="d60af-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="d60af-110">Chaque conflit entre membres mappe à un seul membre dans la mise à jour au cours de laquelle le contrôle d'accès concurrentiel a échoué.</span><span class="sxs-lookup"><span data-stu-id="d60af-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d60af-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="d60af-111">Example</span></span>  
 <span data-ttu-id="d60af-112">Le code suivant présente des exemples des deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="d60af-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d60af-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d60af-113">See also</span></span>

- [<span data-ttu-id="d60af-114">Guide pratique : Gérer les conflits de modification</span><span class="sxs-lookup"><span data-stu-id="d60af-114">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="d60af-115">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="d60af-115">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
