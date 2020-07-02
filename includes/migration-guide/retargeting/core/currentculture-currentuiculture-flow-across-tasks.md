---
ms.openlocfilehash: 78faa5f4008b41bac75c94ce09a58c8227e5b485
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614451"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>CurrentCulture et CurrentUICulture se propagent d’une tâche à l’autre

#### <a name="details"></a>Détails

À compter de .NET Framework 4.6, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> sont stockés dans le <xref:System.Threading.ExecutionContext?displayProperty=fullName> du thread, qui circulent d’une opération asynchrone à une autre. Cela signifie que les changements apportés à <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> sont reflétés dans des tâches qui sont exécutées de façon asynchrone par la suite. Cela diffère du comportement des précédentes versions du .NET Framework (qui réinitialisaient <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> dans toutes les tâches asynchrones).

#### <a name="suggestion"></a>Suggestion

Si vos applications sont affectées par ce changement, vous pouvez le contourner en définissant explicitement le <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> ou <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> souhaité comme première opération dans une tâche asynchrone. L’ancien comportement (qui ne transmet pas <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) peut également être adopté en définissant le commutateur de compatibilité suivant :

```csharp
AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);
```

Ce problème a été résolu par WPF dans le .NET Framework 4.6.2. Il a également été résolu dans .NET Framework versions 4.6 et 4.6.1 par le biais du correctif décrit dans [l’article 3139549 de la Base de connaissances](https://support.microsoft.com/kb/3139549). Les applications qui ciblent .NET Framework 4.6 ou ultérieur obtiennent automatiquement le comportement approprié dans les applications WPF. <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> est conservé d’une opération de répartiteur à l’autre.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.6         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType>
