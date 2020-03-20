---
ms.openlocfilehash: cc6d96bd614ff015ae2125c0f1477e18a91a68f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802710"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>Changement du contraste élevé des contrôles ComboBox svcTraceViewer

|   |   |
|---|---|
|Détails|Dans l’[outil Microsoft Service Trace Viewer](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), les contrôles ComboBox n’étaient pas affichés dans la bonne couleur dans certains thèmes à contraste élevé. Le problème a été résolu dans .NET Framework 4.7.2. Toutefois, en raison des besoins de compatibilité descendante des kits SDK du .NET Framework, le correctif n’était pas visible pour les clients par défaut. .NET 4.8 fait apparaître ce changement en ajoutant les [commutateurs de configuration AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivants dans le fichier svcTraceViewer.exe.config :<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Suggestion|<ul><li>Si vous ne voulez pas accepter ce changement de comportement du contraste élevé, vous pouvez le désactiver en supprimant la section suivante du fichier svcTraceViewer.exe.config :</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>|
|Étendue|Edge|
|Version|4.8|
|Type|Runtime|
