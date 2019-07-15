---
ms.openlocfilehash: 2e974d277d6659aaada321b2a7e7a604df78a7bd
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858650"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a>Les fenêtres WPF sont restituées sans découpage lors de l’extension en dehors d’un même écran

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6 s’exécutant sur Windows 8 et ultérieur, la totalité de la fenêtre est restituée sans découpage quand elle s’étend en dehors d’un même écran dans un scénario à plusieurs écrans. Ceci diffère des versions précédentes du .NET Framework, qui découpait les fenêtres WPF étendues au-delà d’un même écran.|
|Suggestion|Ce comportement (découper ou non) peut être défini explicitement avec l’élément <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> de <code>&lt;appSettings&gt;</code> dans le fichier de configuration d’une application, ou en définissant la propriété <code>EnableMultiMonitorDisplayClipping</code> au démarrage de l’application.|
|Portée|Mineur|
|Version|4.6|
|Type|Runtime|

