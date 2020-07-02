---
ms.openlocfilehash: ae0c7322b7415157838278b5568e6e49936e9a93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621099"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="80cdf-101">Un workflow lève maintenant dans certains cas une exception d’origine au lieu d’une exception NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="80cdf-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

#### <a name="details"></a><span data-ttu-id="80cdf-102">Détails</span><span class="sxs-lookup"><span data-stu-id="80cdf-102">Details</span></span>

<span data-ttu-id="80cdf-103">Dans .NET Framework 4.6.2 et antérieur, quand la méthode Execute d’une activité de workflow lève une exception avec une valeur <code>null</code> pour la propriété <xref:System.Exception.Message>, l’exécution du workflow System.Activities lève une <xref:System.NullReferenceException?displayProperty=fullName>, masquant l’exception d’origine. Dans .NET Framework 4.7, l’exception précédemment masquée est levée.</span><span class="sxs-lookup"><span data-stu-id="80cdf-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=fullName>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="80cdf-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="80cdf-104">Suggestion</span></span>

<span data-ttu-id="80cdf-105">Si votre code s’appuie sur la gestion de <xref:System.NullReferenceException?displayProperty=fullName>, modifiez-le afin d’intercepter les exceptions qui peuvent être levées depuis vos activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="80cdf-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=fullName>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>

| <span data-ttu-id="80cdf-106">Nom</span><span class="sxs-lookup"><span data-stu-id="80cdf-106">Name</span></span>    | <span data-ttu-id="80cdf-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="80cdf-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="80cdf-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="80cdf-108">Scope</span></span>   |<span data-ttu-id="80cdf-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="80cdf-109">Minor</span></span>|
|<span data-ttu-id="80cdf-110">Version</span><span class="sxs-lookup"><span data-stu-id="80cdf-110">Version</span></span>|<span data-ttu-id="80cdf-111">4,7</span><span class="sxs-lookup"><span data-stu-id="80cdf-111">4.7</span></span>|
|<span data-ttu-id="80cdf-112">Type</span><span class="sxs-lookup"><span data-stu-id="80cdf-112">Type</span></span>|<span data-ttu-id="80cdf-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="80cdf-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="80cdf-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="80cdf-114">Affected APIs</span></span>

-<xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
