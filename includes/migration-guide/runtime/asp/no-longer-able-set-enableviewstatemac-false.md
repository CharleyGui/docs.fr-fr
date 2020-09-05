---
ms.openlocfilehash: c1793bb51f7da9169e912078fde202d0d62a4183
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497104"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Il n’est plus possible de définir EnableViewStateMac sur false

#### <a name="details"></a>Détails

ASP.NET ne permet plus aux développeurs de spécifier <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> ou <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Le code d'authentification de message (code MAC) de l'état d'affichage est à présent appliqué à toutes les demandes avec état d'affichage intégré. Seules les applications qui définissent explicitement la propriété EnableViewStateMac sur <code>false</code> sont affectées.

#### <a name="suggestion"></a>Suggestion

EnableViewStateMac doit être supposé être true et toutes les erreurs MAC résultantes doivent être résolues (comme expliqué dans [cette aide](https://support.microsoft.com/kb/2915218), qui contient plusieurs résolutions en fonction des spécificités de la cause des erreurs Mac).

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4.5.2|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
