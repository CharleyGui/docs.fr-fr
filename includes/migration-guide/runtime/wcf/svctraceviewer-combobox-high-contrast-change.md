---
ms.openlocfilehash: 4bc8db52efdfe483acb4f6b6e33c4fa7716e0b79
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770921"
---
### <a name="svctraceviewer-combobox-high-contrast-change"></a>Changement du contraste élevé des contrôles ComboBox svcTraceViewer

#### <a name="details"></a>Détails

Dans l’[outil Microsoft Service Trace Viewer](~/docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), les contrôles ComboBox n’étaient pas affichés dans la bonne couleur dans certains thèmes à contraste élevé. Le problème a été résolu dans .NET Framework 4.7.2. Toutefois, en raison des besoins de compatibilité descendante des kits SDK du .NET Framework, le correctif n’était pas visible pour les clients par défaut. .NET 4.8 fait apparaître ce changement en ajoutant les [commutateurs de configuration AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivants dans le fichier svcTraceViewer.exe.config :

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

#### <a name="suggestion"></a>Suggestion

Si vous ne souhaitez pas que le comportement du contraste élevé soit modifié, vous pouvez le désactiver en supprimant la section suivante du fichier svcTraceViewer.exe.config :

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
```

| Nom    | Valeur   |
|:--------|:--------|
| Étendue   | Edge    |
| Version | 4.8     |
| Type    | Runtime |

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
