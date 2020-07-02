---
ms.openlocfilehash: c557f1cb65a675446bc77c57ef91972df92712bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617162"
---
### <a name="iasyncresultcompletedsynchronously-property-must-be-correct-for-the-resulting-task-to-complete"></a><span data-ttu-id="2fb95-101">La propriété IAsyncResult.CompletedSynchronously doit être correcte pour que la tâche obtenue se termine</span><span class="sxs-lookup"><span data-stu-id="2fb95-101">IAsyncResult.CompletedSynchronously property must be correct for the resulting task to complete</span></span>

#### <a name="details"></a><span data-ttu-id="2fb95-102">Détails</span><span class="sxs-lookup"><span data-stu-id="2fb95-102">Details</span></span>

<span data-ttu-id="2fb95-103">Lors de l’appel à TaskFactory.FromAsync, l’implémentation de la propriété <xref:System.IAsyncResult.CompletedSynchronously> doit être correctement configurée pour que la tâche résultante puisse se terminer.</span><span class="sxs-lookup"><span data-stu-id="2fb95-103">When calling TaskFactory.FromAsync, the implementation of the <xref:System.IAsyncResult.CompletedSynchronously> property must be correct for the resulting task to complete.</span></span> <span data-ttu-id="2fb95-104">Autrement dit, la propriété doit retourner la valeur true si, et uniquement si, l’implémentation s’est terminée de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="2fb95-104">That is, the property must return true if, and only if, the implementation completed synchronously.</span></span> <span data-ttu-id="2fb95-105">Auparavant, la propriété n’était pas vérifiée.</span><span class="sxs-lookup"><span data-stu-id="2fb95-105">Previously, the property was not checked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2fb95-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="2fb95-106">Suggestion</span></span>

<span data-ttu-id="2fb95-107">Si les implémentations d’<xref:System.IAsyncResult?displayProperty=fullName> retournent comme il se doit la valeur true pour la propriété <xref:System.IAsyncResult.CompletedSynchronously?displayProperty=fullName> uniquement quand une tâche se termine de façon synchrone, l’exécution n’est pas arrêtée.</span><span class="sxs-lookup"><span data-stu-id="2fb95-107">If <xref:System.IAsyncResult?displayProperty=fullName> implementations correctly return true for the <xref:System.IAsyncResult.CompletedSynchronously?displayProperty=fullName> property only when a task completed synchronously, then no break will be observed.</span></span> <span data-ttu-id="2fb95-108">Les utilisateurs doivent examiner leurs éventuelles implémentations d’<xref:System.IAsyncResult?displayProperty=fullName> afin de vérifier qu’elles évaluent correctement si une tâche se termine de manière synchrone ou non.</span><span class="sxs-lookup"><span data-stu-id="2fb95-108">Users should review <xref:System.IAsyncResult?displayProperty=fullName> implementations they own (if any) to ensure that they correctly evaluate whether a task completed synchronously or not.</span></span>

| <span data-ttu-id="2fb95-109">Nom</span><span class="sxs-lookup"><span data-stu-id="2fb95-109">Name</span></span>    | <span data-ttu-id="2fb95-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="2fb95-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2fb95-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="2fb95-111">Scope</span></span>   | <span data-ttu-id="2fb95-112">Edge</span><span class="sxs-lookup"><span data-stu-id="2fb95-112">Edge</span></span>        |
| <span data-ttu-id="2fb95-113">Version</span><span class="sxs-lookup"><span data-stu-id="2fb95-113">Version</span></span> | <span data-ttu-id="2fb95-114">4,5</span><span class="sxs-lookup"><span data-stu-id="2fb95-114">4.5</span></span>         |
| <span data-ttu-id="2fb95-115">Type</span><span class="sxs-lookup"><span data-stu-id="2fb95-115">Type</span></span>    | <span data-ttu-id="2fb95-116">Reciblage</span><span class="sxs-lookup"><span data-stu-id="2fb95-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="2fb95-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="2fb95-117">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult},System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.IAsyncResult,System.Action{System.IAsyncResult},System.Threading.Tasks.TaskCreationOptions,System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600})?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%600},System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.Func{System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%600},System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600},System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%601(System.IAsyncResult,System.Func{System.IAsyncResult,%60%600},System.Threading.Tasks.TaskCreationOptions,System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%601},%60%600,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%602(System.Func{%60%600,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%601},%60%600,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%602},%60%600,%60%601,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,%60%602,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Action{System.IAsyncResult},%60%600,%60%601,%60%602,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%603(System.Func{%60%600,%60%601,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%602},%60%600,%60%601,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%603},%60%600,%60%601,%60%602,System.Object)?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskFactory.FromAsync%60%604(System.Func{%60%600,%60%601,%60%602,System.AsyncCallback,System.Object,System.IAsyncResult},System.Func{System.IAsyncResult,%60%603},%60%600,%60%601,%60%602,System.Object,System.Threading.Tasks.TaskCreationOptions)?displayProperty=nameWithType>
