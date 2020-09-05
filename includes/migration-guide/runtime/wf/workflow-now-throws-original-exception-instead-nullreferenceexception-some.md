---
ms.openlocfilehash: 61d5885c19e39b138090c1a98fa26348724893c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497037"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="f4806-101">Un workflow lève maintenant dans certains cas une exception d’origine au lieu d’une exception NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="f4806-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

#### <a name="details"></a><span data-ttu-id="f4806-102">Détails</span><span class="sxs-lookup"><span data-stu-id="f4806-102">Details</span></span>

<span data-ttu-id="f4806-103">Dans .NET Framework 4.6.2 et antérieur, quand la méthode Execute d’une activité de workflow lève une exception avec une valeur <code>null</code> pour la propriété <xref:System.Exception.Message>, l’exécution du workflow System.Activities lève une <xref:System.NullReferenceException?displayProperty=fullName>, masquant l’exception d’origine. Dans .NET Framework 4.7, l’exception précédemment masquée est levée.</span><span class="sxs-lookup"><span data-stu-id="f4806-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=fullName>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f4806-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="f4806-104">Suggestion</span></span>

<span data-ttu-id="f4806-105">Si votre code s’appuie sur la gestion de <xref:System.NullReferenceException?displayProperty=fullName>, modifiez-le afin d’intercepter les exceptions qui peuvent être levées depuis vos activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="f4806-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=fullName>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>

| <span data-ttu-id="f4806-106">Name</span><span class="sxs-lookup"><span data-stu-id="f4806-106">Name</span></span>    | <span data-ttu-id="f4806-107">Valeur</span><span class="sxs-lookup"><span data-stu-id="f4806-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f4806-108">Étendue</span><span class="sxs-lookup"><span data-stu-id="f4806-108">Scope</span></span>   |<span data-ttu-id="f4806-109">Secondaire</span><span class="sxs-lookup"><span data-stu-id="f4806-109">Minor</span></span>|
|<span data-ttu-id="f4806-110">Version</span><span class="sxs-lookup"><span data-stu-id="f4806-110">Version</span></span>|<span data-ttu-id="f4806-111">4,7</span><span class="sxs-lookup"><span data-stu-id="f4806-111">4.7</span></span>|
|<span data-ttu-id="f4806-112">Type</span><span class="sxs-lookup"><span data-stu-id="f4806-112">Type</span></span>|<span data-ttu-id="f4806-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="f4806-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="f4806-114">API affectées</span><span class="sxs-lookup"><span data-stu-id="f4806-114">Affected APIs</span></span>

- <xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType>
- <xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType>
- <xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType>
- <xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)`
- `M:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)`
- ``M:System.Activities.AsyncCodeActivity`1.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)``
- `M:System.Activities.WorkflowInvoker.Invoke`

-->
