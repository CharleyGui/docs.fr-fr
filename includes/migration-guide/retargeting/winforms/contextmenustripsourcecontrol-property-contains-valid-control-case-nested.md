---
ms.openlocfilehash: 5529b8379c5cb9f1bc525e0c2340f6b885e35822
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606728"
---
### <a name="contextmenustripsourcecontrol-property-contains-a-valid-control-in-the-case-of-nested-toolstripmenuitems"></a>La propriété ContextMenuStrip.SourceControl contient un contrôle valide dans le cas des ToolStripMenuItems imbriqués

#### <a name="details"></a>Détails

Dans .NET Framework 4.7.1 et versions antérieures, la propriété <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType> retourne la valeur null quand l’utilisateur ouvre le menu à partir de contrôles <xref:System.Windows.Forms.ToolStripMenuItem> imbriqués. Dans .NET Framework 4.7.2 et versions ultérieures, la propriété <xref:System.Windows.Forms.ContextMenuStrip.SourceControl> est toujours définie sur le contrôle de code source réel.

#### <a name="suggestion"></a>Suggestion

**Comment accepter ou refuser ces modifications** Pour qu’une application tire parti de ces modifications, elle doit s’exécuter sur le .NET Framework 4.7.2 ou version ultérieure. Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :

- Faites-lui cibler .NET Framework 4.7.2. Ce changement est activé par défaut sur les applications Windows Forms qui ciblent .NET Framework 4.7.2 ou ultérieur.
- Faites-lui cibler .NET Framework version 4.7.1 ou antérieure et refusez les comportements d’accessibilité hérités en ajoutant le [commutateur AppContext](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier app.config et en lui affectant la valeur `false`, comme dans l’exemple suivant.

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue=false"/>
</runtime>
```

Si votre application cible .NET Framework 4.7.2 ou une version ultérieure et que vous souhaitez conserver le comportement hérité, choisissez d’utiliser la valeur de contrôle de code source héritée en affectant explicitement à ce commutateur AppContext la valeur `true`.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl?displayProperty=nameWithType>
