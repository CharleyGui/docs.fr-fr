---
ms.openlocfilehash: ae0c7322b7415157838278b5568e6e49936e9a93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621099"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a>Un workflow lève maintenant dans certains cas une exception d’origine au lieu d’une exception NullReferenceException

#### <a name="details"></a>Détails

Dans .NET Framework 4.6.2 et antérieur, quand la méthode Execute d’une activité de workflow lève une exception avec une valeur <code>null</code> pour la propriété <xref:System.Exception.Message>, l’exécution du workflow System.Activities lève une <xref:System.NullReferenceException?displayProperty=fullName>, masquant l’exception d’origine. Dans .NET Framework 4.7, l’exception précédemment masquée est levée.

#### <a name="suggestion"></a>Suggestion

Si votre code s’appuie sur la gestion de <xref:System.NullReferenceException?displayProperty=fullName>, modifiez-le afin d’intercepter les exceptions qui peuvent être levées depuis vos activités personnalisées.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,7|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
