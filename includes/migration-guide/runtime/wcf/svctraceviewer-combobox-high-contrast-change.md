---
ms.openlocfilehash: 6a6c0af9cc0f3e5d1bbc3a4462a9ff7eaa748a5f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497854"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>Changement du contraste élevé des contrôles ComboBox svcTraceViewer

#### <a name="details"></a>Détails

Dans l’[outil Microsoft Service Trace Viewer](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), les contrôles ComboBox n’étaient pas affichés dans la bonne couleur dans certains thèmes à contraste élevé. Le problème a été résolu dans .NET Framework 4.7.2. Toutefois, en raison des besoins de compatibilité descendante des kits SDK du .NET Framework, le correctif n’était pas visible pour les clients par défaut. .NET 4.8 fait apparaître ce changement en ajoutant les [commutateurs de configuration AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivants dans le fichier svcTraceViewer.exe.config :<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

#### <a name="suggestion"></a>Suggestion

<ul><li>Si vous ne voulez pas accepter ce changement de comportement du contraste élevé, vous pouvez le désactiver en supprimant la section suivante du fichier svcTraceViewer.exe.config :</li></ul><pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false&quot; /&gt;&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.8|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
