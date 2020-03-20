---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803213"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Il n’est plus possible de définir EnableViewStateMac sur false

|   |   |
|---|---|
|Détails|ASP.NET ne permet plus aux développeurs de spécifier <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> ou <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. Le code d'authentification de message (code MAC) de l'état d'affichage est à présent appliqué à toutes les demandes avec état d'affichage intégré. Seules les applications qui définissent explicitement la propriété EnableViewStateMac sur <code>false</code> sont affectées.|
|Suggestion|EnableViewStateMac doit être supposé être vrai, et toutes les erreurs MAC résultant doivent être résolues (comme expliqué dans [cette directive](https://support.microsoft.com/kb/2915218), qui contient plusieurs résolutions en fonction des spécificités de ce qui cause des erreurs DE MAC).|
|Étendue|Majeure|
|Version|4.5.2|
|Type|Runtime|
