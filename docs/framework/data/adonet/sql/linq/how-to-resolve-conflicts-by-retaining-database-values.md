---
title: 'Procédure : Résoudre des conflits en conservant des valeurs de bases de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: e42f48a188741c3ddff44f6444fa351192c8175f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793339"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="c1424-102">Procédure : Résoudre des conflits en conservant des valeurs de bases de données</span><span class="sxs-lookup"><span data-stu-id="c1424-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="c1424-103">Pour rapprocher les différences entre les valeurs de base de données attendues et réelles avant d’essayer de renvoyer vos modifications, vous pouvez utiliser <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> pour conserver les valeurs trouvées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="c1424-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="c1424-104">Les valeurs actuelles dans le modèle objet sont alors remplacées.</span><span class="sxs-lookup"><span data-stu-id="c1424-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="c1424-105">Pour plus d’informations, [consultez accès concurrentiel optimiste : Vue](optimistic-concurrency-overview.md)d’ensemble.</span><span class="sxs-lookup"><span data-stu-id="c1424-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1424-106">Dans tous les cas, l'enregistrement sur le client est actualisé lors de la récupération des données mises à jour de la base de données.</span><span class="sxs-lookup"><span data-stu-id="c1424-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="c1424-107">Cette action permet de s'assurer que la prochaine tentative de mise à jour n'échouera pas sur les mêmes vérifications d'accès concurrentiel.</span><span class="sxs-lookup"><span data-stu-id="c1424-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1424-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="c1424-108">Example</span></span>  
 <span data-ttu-id="c1424-109">Dans ce scénario, une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque User1 tente de soumettre des modifications car User2 a modifié entre-temps les colonnes Assistant et Department.</span><span class="sxs-lookup"><span data-stu-id="c1424-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="c1424-110">Le tableau suivant présente la situation.</span><span class="sxs-lookup"><span data-stu-id="c1424-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="c1424-111">Responsable</span><span class="sxs-lookup"><span data-stu-id="c1424-111">Manager</span></span>|<span data-ttu-id="c1424-112">Assistant</span><span class="sxs-lookup"><span data-stu-id="c1424-112">Assistant</span></span>|<span data-ttu-id="c1424-113">department</span><span class="sxs-lookup"><span data-stu-id="c1424-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="c1424-114">État de la base de données d'origine lors d'une interrogation par User1 et User2.</span><span class="sxs-lookup"><span data-stu-id="c1424-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="c1424-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="c1424-115">Alfreds</span></span>|<span data-ttu-id="c1424-116">Maria</span><span class="sxs-lookup"><span data-stu-id="c1424-116">Maria</span></span>|<span data-ttu-id="c1424-117">Sales</span><span class="sxs-lookup"><span data-stu-id="c1424-117">Sales</span></span>|  
|<span data-ttu-id="c1424-118">User1 s'apprête à soumettre ces modifications.</span><span class="sxs-lookup"><span data-stu-id="c1424-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="c1424-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="c1424-119">Alfred</span></span>||<span data-ttu-id="c1424-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="c1424-120">Marketing</span></span>|  
|<span data-ttu-id="c1424-121">User2 a déjà soumis ces modifications.</span><span class="sxs-lookup"><span data-stu-id="c1424-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="c1424-122">Mary</span><span class="sxs-lookup"><span data-stu-id="c1424-122">Mary</span></span>|<span data-ttu-id="c1424-123">de diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="c1424-123">Service</span></span>|  
  
 <span data-ttu-id="c1424-124">User1 décide de résoudre ce conflit en remplaçant les valeurs actuelles dans le modèle objet par les valeurs de base de données les plus récentes.</span><span class="sxs-lookup"><span data-stu-id="c1424-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="c1424-125">Lorsque User1 résout le conflit à l'aide de <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, le résultat dans la base de données se présente comme dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="c1424-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="c1424-126">Responsable</span><span class="sxs-lookup"><span data-stu-id="c1424-126">Manager</span></span>|<span data-ttu-id="c1424-127">Assistant</span><span class="sxs-lookup"><span data-stu-id="c1424-127">Assistant</span></span>|<span data-ttu-id="c1424-128">department</span><span class="sxs-lookup"><span data-stu-id="c1424-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="c1424-129">Nouvel état après résolution du conflit.</span><span class="sxs-lookup"><span data-stu-id="c1424-129">New state after conflict resolution.</span></span>|<span data-ttu-id="c1424-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="c1424-130">Alfreds</span></span><br /><br /> <span data-ttu-id="c1424-131">(d'origine)</span><span class="sxs-lookup"><span data-stu-id="c1424-131">(original)</span></span>|<span data-ttu-id="c1424-132">Mary</span><span class="sxs-lookup"><span data-stu-id="c1424-132">Mary</span></span><br /><br /> <span data-ttu-id="c1424-133">(de User2)</span><span class="sxs-lookup"><span data-stu-id="c1424-133">(from User2)</span></span>|<span data-ttu-id="c1424-134">de diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="c1424-134">Service</span></span><br /><br /> <span data-ttu-id="c1424-135">(de User2)</span><span class="sxs-lookup"><span data-stu-id="c1424-135">(from User2)</span></span>|  
  
 <span data-ttu-id="c1424-136">Le code d'exemple suivant indique comment remplacer les valeurs actuelles dans le modèle objet par les valeurs de base de données.</span><span class="sxs-lookup"><span data-stu-id="c1424-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="c1424-137">Aucune inspection ni aucune gestion personnalisée des conflits de membres individuels n'est effectuée.</span><span class="sxs-lookup"><span data-stu-id="c1424-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c1424-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1424-138">See also</span></span>

- [<span data-ttu-id="c1424-139">Guide pratique pour Gérer les conflits de modification</span><span class="sxs-lookup"><span data-stu-id="c1424-139">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
