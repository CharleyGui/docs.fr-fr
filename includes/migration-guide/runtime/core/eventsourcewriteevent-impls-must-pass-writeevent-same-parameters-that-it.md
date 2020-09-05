---
ms.openlocfilehash: 99a7fa0fcfce6d490a182f85709b5dd0e0e8c86f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496600"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>Les implémentations d’EventSource.WriteEvent doivent passer à WriteEvent les mêmes paramètres qu’il a reçus (plus l’ID)

#### <a name="details"></a>Détails

Le runtime applique à présent le contrat qui stipule ce qui suit : une classe dérivée de <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> qui définit une méthode d'événement ETW doit appeler la méthode <code>EventSource.WriteEvent</code> de la classe de base avec l'ID d'événement suivi des mêmes arguments que ceux passés à la méthode d'événement ETW.

#### <a name="suggestion"></a>Suggestion

Une exception <xref:System.IndexOutOfRangeException?displayProperty=fullName> est levée si un <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> lit des données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> dans le processus pour une source d'événement qui ne respecte pas ce contrat.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
