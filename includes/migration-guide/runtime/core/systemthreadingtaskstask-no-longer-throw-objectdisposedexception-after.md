---
ms.openlocfilehash: 3eab96149be1e40d528cfd552bbe05ca766cf4e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619992"
---
### <a name="systemthreadingtaskstask-no-longer-throw-objectdisposedexception-after-object-is-disposed"></a><span data-ttu-id="38d0e-101">System.Threading.Tasks.Task ne lève plus d’exception ObjectDisposedException après la suppression de l’objet</span><span class="sxs-lookup"><span data-stu-id="38d0e-101">System.Threading.Tasks.Task no longer throw ObjectDisposedException after object is disposed</span></span>

#### <a name="details"></a><span data-ttu-id="38d0e-102">Détails</span><span class="sxs-lookup"><span data-stu-id="38d0e-102">Details</span></span>

<span data-ttu-id="38d0e-103">À l’exception de <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, les méthodes <xref:System.Threading.Tasks.Task?displayProperty=fullName> ne lèvent plus d’exception <xref:System.ObjectDisposedException?displayProperty=fullName> après la suppression de l’objet. Cette modification prend en charge l’utilisation des tâches mises en cache.</span><span class="sxs-lookup"><span data-stu-id="38d0e-103">Except for <xref:System.Threading.Tasks.Task.System%23IAsyncResult%23AsyncWaitHandle>, <xref:System.Threading.Tasks.Task?displayProperty=fullName> methods no longer throw an <xref:System.ObjectDisposedException?displayProperty=fullName> exception after the object is disposed.This change supports the use of cached tasks.</span></span> <span data-ttu-id="38d0e-104">Par exemple, une méthode peut retourner une tâche mise en cache pour représenter une opération déjà terminée au lieu d'allouer une nouvelle tâche.</span><span class="sxs-lookup"><span data-stu-id="38d0e-104">For example, a method can return a cached task to represent an already completed operation instead of allocating a new task.</span></span> <span data-ttu-id="38d0e-105">Cette opération était impossible dans les versions précédentes du .NET Framework, car tout consommateur de la tâche pouvait la supprimer, ce qui la rendait inutilisable.</span><span class="sxs-lookup"><span data-stu-id="38d0e-105">This was impossible in previous .NET Framework versions, because any consumer of the task could dispose of it, which rendered it unusable.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="38d0e-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="38d0e-106">Suggestion</span></span>

<span data-ttu-id="38d0e-107">N’oubliez pas que les méthodes Task peuvent ne plus lever d’exceptions <xref:System.ObjectDisposedException?displayProperty=fullName> quand l’objet est supprimé.</span><span class="sxs-lookup"><span data-stu-id="38d0e-107">Be aware that Task methods may no longer throw <xref:System.ObjectDisposedException?displayProperty=fullName> in cases when the object is disposed.</span></span> <span data-ttu-id="38d0e-108">Si une application dépendait de cette exception pour savoir qu’une tâche avait été supprimée, elle doit être mise à jour pour vérifier explicitement l’état de la tâche à l’aide de <xref:System.Threading.Tasks.Task.Status>.</span><span class="sxs-lookup"><span data-stu-id="38d0e-108">If an app was depending on this exception to know that a task was disposed, it should be updated to explicitly check the task's status using <xref:System.Threading.Tasks.Task.Status>.</span></span>

| <span data-ttu-id="38d0e-109">Nom</span><span class="sxs-lookup"><span data-stu-id="38d0e-109">Name</span></span>    | <span data-ttu-id="38d0e-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="38d0e-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="38d0e-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="38d0e-111">Scope</span></span>   |<span data-ttu-id="38d0e-112">Secondaire</span><span class="sxs-lookup"><span data-stu-id="38d0e-112">Minor</span></span>|
|<span data-ttu-id="38d0e-113">Version</span><span class="sxs-lookup"><span data-stu-id="38d0e-113">Version</span></span>|<span data-ttu-id="38d0e-114">4,5</span><span class="sxs-lookup"><span data-stu-id="38d0e-114">4.5</span></span>|
|<span data-ttu-id="38d0e-115">Type</span><span class="sxs-lookup"><span data-stu-id="38d0e-115">Type</span></span>|<span data-ttu-id="38d0e-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="38d0e-116">Runtime</span></span>|
