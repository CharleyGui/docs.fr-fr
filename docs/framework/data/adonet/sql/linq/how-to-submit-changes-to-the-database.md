---
title: 'Procédure : Soumettre des modifications à la base de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: 5952cce5469d7a7e13e8b896f91ea1279fd62d8b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197038"
---
# <a name="how-to-submit-changes-to-the-database"></a><span data-ttu-id="1e8c4-102">Procédure : Soumettre des modifications à la base de données</span><span class="sxs-lookup"><span data-stu-id="1e8c4-102">How to: Submit Changes to the Database</span></span>

<span data-ttu-id="1e8c4-103">Indépendamment du nombre de modifications apportées aux objets, celles-ci sont apportées uniquement aux réplicas en mémoire.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-103">Regardless of how many changes you make to your objects, changes are made only to in-memory replicas.</span></span> <span data-ttu-id="1e8c4-104">Vous n'avez pas apporté de modifications aux données effectives dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-104">You have made no changes to the actual data in the database.</span></span> <span data-ttu-id="1e8c4-105">Vos modifications ne sont pas transmises au serveur tant que vous n'appelez pas explicitement <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-105">Your changes are not transmitted to the server until you explicitly call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="1e8c4-106">Lorsque vous effectuez cet appel, le <xref:System.Data.Linq.DataContext> essaie de traduire vos modifications en commandes SQL équivalentes.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-106">When you make this call, the <xref:System.Data.Linq.DataContext> tries to translate your changes into equivalent SQL commands.</span></span> <span data-ttu-id="1e8c4-107">Vous pouvez utiliser votre propre logique personnalisée pour remplacer ces actions, mais l’ordre d’envoi est orchestrée par un service du <xref:System.Data.Linq.DataContext> appelé « *processeur de modification*».</span><span class="sxs-lookup"><span data-stu-id="1e8c4-107">You can use your own custom logic to override these actions, but the order of submission is orchestrated by a service of the <xref:System.Data.Linq.DataContext> known as the *change processor*.</span></span> <span data-ttu-id="1e8c4-108">La séquence d'événements se décompose comme suit :</span><span class="sxs-lookup"><span data-stu-id="1e8c4-108">The sequence of events is as follows:</span></span>  
  
1. <span data-ttu-id="1e8c4-109">Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examine l'ensemble d'objets connus pour déterminer si de nouvelles instances ont été attachées.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-109">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examines the set of known objects to determine whether new instances have been attached to them.</span></span> <span data-ttu-id="1e8c4-110">Le cas échéant, ces nouvelles instances sont ajoutées au jeu d'objets suivis.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-110">If they have, these new instances are added to the set of tracked objects.</span></span>  
  
2. <span data-ttu-id="1e8c4-111">Tous les objets qui ont des modifications en attente sont organisés dans une séquence d'objets en fonction de leurs dépendances.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-111">All objects that have pending changes are ordered into a sequence of objects based on the dependencies between them.</span></span> <span data-ttu-id="1e8c4-112">Les objets dont les modifications dépendent d'autres objets sont classés d'après leurs dépendances.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-112">Objects whose changes depend on other objects are sequenced after their dependencies.</span></span>  
  
3. <span data-ttu-id="1e8c4-113">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] démarre une transaction pour encapsuler la série de commandes individuelles, juste avant que toutes les modifications réelles soient transmises.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-113">Immediately before any actual changes are transmitted, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a transaction to encapsulate the series of individual commands.</span></span>  
  
4. <span data-ttu-id="1e8c4-114">Les modifications apportées aux objets sont traduites une par une en commandes SQL et sont envoyées au serveur.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-114">The changes to the objects are translated one by one to SQL commands and sent to the server.</span></span>  
  
 <span data-ttu-id="1e8c4-115">À ce stade, toutes les erreurs détectées par la base de données interrompent le processus de soumission et une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-115">At this point, any errors detected by the database cause the submission process to stop, and an exception is raised.</span></span> <span data-ttu-id="1e8c4-116">Toutes les modifications apportées à la base de données sont restaurées comme si aucune soumission ne s'était produite.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-116">All changes to the database are rolled back as if no submissions ever occurred.</span></span> <span data-ttu-id="1e8c4-117">Le <xref:System.Data.Linq.DataContext> a encore un enregistrement complet de toutes les modifications.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-117">The <xref:System.Data.Linq.DataContext> still has a full recording of all changes.</span></span> <span data-ttu-id="1e8c4-118">Par conséquent, vous pouvez essayer de résoudre le problème et d'appeler encore <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, comme dans l'exemple de code qui suit.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-118">You can therefore try to correct the problem and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> again, as in the code example that follows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e8c4-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="1e8c4-119">Example</span></span>  

 <span data-ttu-id="1e8c4-120">Lorsque la transaction autour de la soumission a réussi, le <xref:System.Data.Linq.DataContext> accepte les modifications apportées aux objets en ignorant les informations de suivi des modifications.</span><span class="sxs-lookup"><span data-stu-id="1e8c4-120">When the transaction around the submission is completed successfully, the <xref:System.Data.Linq.DataContext> accepts the changes to the objects by ignoring the change-tracking information.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1e8c4-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e8c4-121">See also</span></span>

- [<span data-ttu-id="1e8c4-122">Procédure : Détecter et résoudre des soumissions en conflit</span><span class="sxs-lookup"><span data-stu-id="1e8c4-122">How to: Detect and Resolve Conflicting Submissions</span></span>](how-to-detect-and-resolve-conflicting-submissions.md)
- [<span data-ttu-id="1e8c4-123">Procédure : Gérer les conflits de changement</span><span class="sxs-lookup"><span data-stu-id="1e8c4-123">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="1e8c4-124">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="1e8c4-124">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="1e8c4-125">Apport et soumission de modifications de données</span><span class="sxs-lookup"><span data-stu-id="1e8c4-125">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
