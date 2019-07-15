---
ms.openlocfilehash: 6e5e90a4cfb862b3bfd74ac5a3715e97a736f598
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802525"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="cd5cc-101">Un workflow lève maintenant dans certains cas une exception d’origine au lieu d’une exception NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="cd5cc-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

|   |   |
|---|---|
|<span data-ttu-id="cd5cc-102">Détails</span><span class="sxs-lookup"><span data-stu-id="cd5cc-102">Details</span></span>|<span data-ttu-id="cd5cc-103">Dans .NET Framework 4.6.2 et antérieur, quand la méthode Execute d’une activité de workflow lève une exception avec une valeur <code>null</code> pour la propriété <xref:System.Exception.Message>, l’exécution du workflow System.Activities lève une <xref:System.NullReferenceException?displayProperty=name>, masquant l’exception d’origine. Dans .NET Framework 4.7, l’exception précédemment masquée est levée.</span><span class="sxs-lookup"><span data-stu-id="cd5cc-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=name>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>|
|<span data-ttu-id="cd5cc-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="cd5cc-104">Suggestion</span></span>|<span data-ttu-id="cd5cc-105">Si votre code s’appuie sur la gestion de <xref:System.NullReferenceException?displayProperty=name>, modifiez-le afin d’intercepter les exceptions qui peuvent être levées depuis vos activités personnalisées.</span><span class="sxs-lookup"><span data-stu-id="cd5cc-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=name>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>|
|<span data-ttu-id="cd5cc-106">Portée</span><span class="sxs-lookup"><span data-stu-id="cd5cc-106">Scope</span></span>|<span data-ttu-id="cd5cc-107">Mineur</span><span class="sxs-lookup"><span data-stu-id="cd5cc-107">Minor</span></span>|
|<span data-ttu-id="cd5cc-108">Version</span><span class="sxs-lookup"><span data-stu-id="cd5cc-108">Version</span></span>|<span data-ttu-id="cd5cc-109">4.7</span><span class="sxs-lookup"><span data-stu-id="cd5cc-109">4.7</span></span>|
|<span data-ttu-id="cd5cc-110">Type</span><span class="sxs-lookup"><span data-stu-id="cd5cc-110">Type</span></span>|<span data-ttu-id="cd5cc-111">Runtime</span><span class="sxs-lookup"><span data-stu-id="cd5cc-111">Runtime</span></span>|
|<span data-ttu-id="cd5cc-112">API affectées</span><span class="sxs-lookup"><span data-stu-id="cd5cc-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|

