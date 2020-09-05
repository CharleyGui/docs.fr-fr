---
ms.openlocfilehash: a133c2ea48df11915f8708029c70549e8a1ccefd
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497800"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>Les fenêtres WPF sont restituées sans découpage lors de l’extension en dehors d’un même écran

#### <a name="details"></a>Détails

Dans .NET Framework 4.6 s’exécutant sur Windows 8 et ultérieur, la totalité de la fenêtre est restituée sans découpage quand elle s’étend en dehors d’un même écran dans un scénario à plusieurs écrans. Ceci diffère des versions précédentes du .NET Framework, qui découpait les fenêtres WPF étendues au-delà d’un même écran.

#### <a name="suggestion"></a>Suggestion

Ce comportement (découper ou non) peut être défini explicitement avec l’élément <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> de <code>&lt;appSettings&gt;</code> dans le fichier de configuration d’une application, ou en définissant la propriété <code>EnableMultiMonitorDisplayClipping</code> au démarrage de l’application.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,6|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
