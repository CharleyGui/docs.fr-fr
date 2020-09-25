---
title: 'Procédure : Résoudre des conflits en remplaçant des valeurs de bases de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 1dc112350451bde28d27c63961733b96f6fc84be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191708"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="2edf5-102">Procédure : Résoudre des conflits en remplaçant des valeurs de bases de données</span><span class="sxs-lookup"><span data-stu-id="2edf5-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>

<span data-ttu-id="2edf5-103">Pour harmoniser des différences entre des valeurs de base de données attendues et réelles avant d'essayer de renvoyer vos modifications, vous pouvez utiliser <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> pour remplacer les valeurs de la base de données.</span><span class="sxs-lookup"><span data-stu-id="2edf5-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="2edf5-104">Pour plus d’informations, consultez [accès concurrentiel optimiste : vue d’ensemble](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2edf5-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2edf5-105">Dans tous les cas, l'enregistrement sur le client est actualisé lors de la récupération des données mises à jour de la base de données.</span><span class="sxs-lookup"><span data-stu-id="2edf5-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="2edf5-106">Cette action permet de s'assurer que la prochaine tentative de mise à jour n'échouera pas sur les mêmes vérifications d'accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="2edf5-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2edf5-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="2edf5-107">Example</span></span>  

 <span data-ttu-id="2edf5-108">Dans ce scénario, une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque User1 tente de soumettre des modifications, car User2 a modifié entre-temps les colonnes Assistant et Department.</span><span class="sxs-lookup"><span data-stu-id="2edf5-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="2edf5-109">Le tableau suivant présente la situation.</span><span class="sxs-lookup"><span data-stu-id="2edf5-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="2edf5-110">Manager</span><span class="sxs-lookup"><span data-stu-id="2edf5-110">Manager</span></span>|<span data-ttu-id="2edf5-111">Assistant</span><span class="sxs-lookup"><span data-stu-id="2edf5-111">Assistant</span></span>|<span data-ttu-id="2edf5-112">department</span><span class="sxs-lookup"><span data-stu-id="2edf5-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="2edf5-113">État de la base de données d'origine lors d'une interrogation par User1 et User2.</span><span class="sxs-lookup"><span data-stu-id="2edf5-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="2edf5-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="2edf5-114">Alfreds</span></span>|<span data-ttu-id="2edf5-115">Maria</span><span class="sxs-lookup"><span data-stu-id="2edf5-115">Maria</span></span>|<span data-ttu-id="2edf5-116">Sales</span><span class="sxs-lookup"><span data-stu-id="2edf5-116">Sales</span></span>|  
|<span data-ttu-id="2edf5-117">User1 s'apprête à soumettre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="2edf5-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="2edf5-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="2edf5-118">Alfred</span></span>||<span data-ttu-id="2edf5-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="2edf5-119">Marketing</span></span>|  
|<span data-ttu-id="2edf5-120">User2 a déjà soumis ces modifications.</span><span class="sxs-lookup"><span data-stu-id="2edf5-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="2edf5-121">Mary</span><span class="sxs-lookup"><span data-stu-id="2edf5-121">Mary</span></span>|<span data-ttu-id="2edf5-122">Service</span><span class="sxs-lookup"><span data-stu-id="2edf5-122">Service</span></span>|  
  
 <span data-ttu-id="2edf5-123">User1 décide de résoudre ce conflit en remplaçant des valeurs de base de données par les valeurs de membre client actuelles.</span><span class="sxs-lookup"><span data-stu-id="2edf5-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="2edf5-124">Lorsque User1 résout le conflit à l'aide de <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, le résultat dans la base de données se présente comme dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="2edf5-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="2edf5-125">Manager</span><span class="sxs-lookup"><span data-stu-id="2edf5-125">Manager</span></span>|<span data-ttu-id="2edf5-126">Assistant</span><span class="sxs-lookup"><span data-stu-id="2edf5-126">Assistant</span></span>|<span data-ttu-id="2edf5-127">department</span><span class="sxs-lookup"><span data-stu-id="2edf5-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="2edf5-128">Nouvel état après résolution du conflit.</span><span class="sxs-lookup"><span data-stu-id="2edf5-128">New state after conflict resolution.</span></span>|<span data-ttu-id="2edf5-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="2edf5-129">Alfred</span></span><br /><br /> <span data-ttu-id="2edf5-130">(de User1)</span><span class="sxs-lookup"><span data-stu-id="2edf5-130">(from User1)</span></span>|<span data-ttu-id="2edf5-131">Maria</span><span class="sxs-lookup"><span data-stu-id="2edf5-131">Maria</span></span><br /><br /> <span data-ttu-id="2edf5-132">(d'origine)</span><span class="sxs-lookup"><span data-stu-id="2edf5-132">(original)</span></span>|<span data-ttu-id="2edf5-133">Marketing</span><span class="sxs-lookup"><span data-stu-id="2edf5-133">Marketing</span></span><br /><br /> <span data-ttu-id="2edf5-134">(de User1)</span><span class="sxs-lookup"><span data-stu-id="2edf5-134">(from User1)</span></span>|  
  
 <span data-ttu-id="2edf5-135">L'exemple suivant montre comment remplacer des valeurs de base de données par des valeurs de membre client actuelles.</span><span class="sxs-lookup"><span data-stu-id="2edf5-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="2edf5-136">Aucune inspection ni aucune gestion personnalisée des conflits de membres individuels n'est effectuée.</span><span class="sxs-lookup"><span data-stu-id="2edf5-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2edf5-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2edf5-137">See also</span></span>

- [<span data-ttu-id="2edf5-138">Procédure : Gérer les conflits de changement</span><span class="sxs-lookup"><span data-stu-id="2edf5-138">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
