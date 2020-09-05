---
ms.openlocfilehash: 61d5885c19e39b138090c1a98fa26348724893c5
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497037"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>Un workflow lève maintenant dans certains cas une exception d’origine au lieu d’une exception NullReferenceException

#### <a name="details"></a>Détails

Dans .NET Framework 4.6.2 et antérieur, quand la méthode Execute d’une activité de workflow lève une exception avec une valeur <code>null</code> pour la propriété <xref:System.Exception.Message>, l’exécution du workflow System.Activities lève une <xref:System.NullReferenceException?displayProperty=fullName>, masquant l’exception d’origine. Dans .NET Framework 4.7, l’exception précédemment masquée est levée.

#### <a name="suggestion"></a>Suggestion

Si votre code s’appuie sur la gestion de <xref:System.NullReferenceException?displayProperty=fullName>, modifiez-le afin d’intercepter les exceptions qui peuvent être levées depuis vos activités personnalisées.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,7|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

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
