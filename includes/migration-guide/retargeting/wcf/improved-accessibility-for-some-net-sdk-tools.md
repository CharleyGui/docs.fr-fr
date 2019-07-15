---
ms.openlocfilehash: 79005f19ac31ba32e7e468ef61eb867a052eff40
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858960"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Amélioration de l’accessibilité pour certains outils du SDK .NET

|   |   |
|---|---|
|Détails|Dans le kit .NET Framework SDK 4.7.1, les outils SvcConfigEditor.exe et SvcTraceViewer.exe ont été améliorés en corrigeant différents problèmes d’accessibilité. La plupart étaient des petits problèmes comme un nom non défini ou certains modèles d’automatisation de l’interface utilisateur non implémentés correctement. Alors que de nombreux utilisateurs n’ont pas connaissance de ces valeurs incorrectes, les clients qui utilisent des technologies d’assistance comme les lecteurs d’écran trouveront ces outils de SDK plus accessibles. Il est évident que ces correctifs changent certains comportements précédents, comme l’ordre de focus clavier. Pour obtenir tous les correctifs liés à l’accessibilité dans ces outils, vous pouvez ajouter ce qui suit à votre fichier app.config :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Portée|Microsoft Edge|
|Version|4.7.1|
|Type|Reciblage|

