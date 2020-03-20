---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858650"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>Les fenêtres WPF sont restituées sans découpage lors de l’extension en dehors d’un même écran

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6 s’exécutant sur Windows 8 et ultérieur, la totalité de la fenêtre est restituée sans découpage quand elle s’étend en dehors d’un même écran dans un scénario à plusieurs écrans. Ceci diffère des versions précédentes du .NET Framework, qui découpait les fenêtres WPF étendues au-delà d’un même écran.|
|Suggestion|Ce comportement (découper ou non) peut être défini explicitement avec l’élément <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> de <code>&lt;appSettings&gt;</code> dans le fichier de configuration d’une application, ou en définissant la propriété <code>EnableMultiMonitorDisplayClipping</code> au démarrage de l’application.|
|Étendue|Secondaire|
|Version|4.6|
|Type|Runtime|
