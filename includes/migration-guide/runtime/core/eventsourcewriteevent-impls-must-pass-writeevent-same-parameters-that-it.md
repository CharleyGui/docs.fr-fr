---
ms.openlocfilehash: 662c140f019add66ff6605d47ad1f32c3f50d711
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619974"
---
### <a name="eventsourcewriteevent-impls-must-pass-writeevent-the-same-parameters-that-it-received-plus-id"></a>Les implémentations d’EventSource.WriteEvent doivent passer à WriteEvent les mêmes paramètres qu’il a reçus (plus l’ID)

#### <a name="details"></a>Détails

Le runtime applique à présent le contrat qui stipule ce qui suit : une classe dérivée de <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> qui définit une méthode d'événement ETW doit appeler la méthode <code>EventSource.WriteEvent</code> de la classe de base avec l'ID d'événement suivi des mêmes arguments que ceux passés à la méthode d'événement ETW.

#### <a name="suggestion"></a>Suggestion

Une exception <xref:System.IndexOutOfRangeException?displayProperty=fullName> est levée si un <xref:System.Diagnostics.Tracing.EventListener?displayProperty=fullName> lit des données <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> dans le processus pour une source d'événement qui ne respecte pas ce contrat.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5.1|
|Type|Runtime|
