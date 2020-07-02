---
ms.openlocfilehash: e528a41748d9353c96d443f68e15e7a98ee7f4ae
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616249"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a>Améliorations des fonctionnalités d’accessibilité dans les contrôles Windows Forms pour .NET 4.8

#### <a name="details"></a>Détails

Windows Forms Framework continue d’améliorer la façon dont il utilise les technologies d’accessibilité pour mieux répondre aux besoins de ses clients. Citons notamment les changements suivants :

- Changements visant à améliorer l’affichage en mode Contraste élevé.
- Changements apportés à l’interaction avec le Narrateur.
- Changements dans la hiérarchie accessible (amélioration de la navigation dans l’arborescence UI Automation).

#### <a name="suggestion"></a>Suggestion

**Comment accepter ou refuser ces modifications** Pour que l’application tire parti de ces modifications, elle doit s’exécuter sur le .NET Framework 4,8. Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :

- Recompilez-la pour qu’elle cible .NET Framework 4.8. Ces changements d’accessibilité sont activés par défaut sur les applications Windows Forms qui ciblent .NET Framework 4.8.
- Faites-lui cibler .NET Framework version 4.7.2 ou antérieure et cessez d’adhérer aux comportements d’accessibilité existants, en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant dans la section `<runtime>` du fichier de configuration de l’application et en lui affectant la valeur `false`, comme dans l’exemple suivant.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
  </runtime>
</configuration>
```

Notez que pour adhérer aux fonctionnalités d’accessibilité ajoutées à .NET Framework 4.8, vous devez également adhérer aux fonctionnalités d’accessibilité de .NET Framework 4.7.1 et 4.7.2. Si vos applications ciblent .NET Framework 4.8 et que vous souhaitez conserver le comportement d’accessibilité existant, choisissez d’adhérer aux fonctionnalités d’accessibilité existantes en affectant explicitement à ce commutateur AppContext la valeur `true`. L’activation de la prise en charge de l’appel des info-bulles au clavier demande d’ajouter la ligne `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` à la valeur AppContextSwitchOverrides :

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false" />
```

Notez que l’activation de cette fonctionnalité demande d’adhérer aux fonctionnalités d’accessibilité susmentionnées de .NET Framework 4.7.1 - 4.8. De plus, si vous n’avez pas adhéré à l’une des fonctionnalités d’accessibilité mais que l’info-bulle affiche le contraire, une <xref:System.NotSupportedException> d’exécution est levée la première fois que vous accédez à ces fonctionnalités. Le message d’exception indique que les info-bulles de clavier requièrent des améliorations de l’accessibilité du niveau 3 pour être activées.

**Utilisation des couleurs définies par le système d’exploitation dans les thèmes à contraste élevé**

- Thèmes à contraste élevé améliorés.

**Amélioration de la prise en charge du Narrateur**

- Le Narrateur annonce désormais le sens du tri de la <xref:System.Windows.Forms.DataGridViewColumn> quand il annonce un nom accessible d’une <xref:System.Windows.Forms.DataGridViewCell>.

**Prise en charge améliorée de l’accessibilité de CheckedListBox**

- Prise en charge améliorée du Narrateur pour le contrôle <xref:System.Windows.Forms.CheckedListBox>. Quand vous accédez au contrôle <xref:System.Windows.Forms.CheckedListBox> à l’aide du clavier, le Narrateur se focalise sur l’élément <xref:System.Windows.Forms.CheckedListBox> et l’annonce.
- Un contrôle CheckedListBox vide a maintenant un rectangle dessiné pour un premier élément virtuel quand le contrôle a le focus.

**Prise en charge améliorée de l’accessibilité de ComboBox**

- Activation de la prise en charge d’UI Automation pour le contrôle <xref:System.Windows.Forms.ComboBox>, avec la possibilité d’utiliser les notifications UI Automation et autres fonctionnalités UI Automation.
**Amélioration de la prise en charge de l’accessibilité DataGridView**

- Activation de la prise en charge d’UI Automation pour le contrôle <xref:System.Windows.Forms.DataGridView> avec la possibilité d’utiliser les notifications UI Automation et autres fonctionnalités UI Automation.
- L’élément UI Automation qui correspond au <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> ou au <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> est maintenant un enfant de la cellule d’édition correspondante.

**Prise en charge améliorée de l’accessibilité de LinkLabel**

- Amélioration <xref:System.Windows.Forms.LinkLabel> de l’accessibilité des contrôles : le narrateur annonce l’état désactivé pour le lien si le <xref:System.Windows.Forms.LinkLabel> contrôle correspondant est désactivé.

**Prise en charge améliorée de l’accessibilité de ProgressBar**

- Activation de la prise en charge d’UI Automation pour le contrôle <xref:System.Windows.Forms.ProgressBar> avec la possibilité d’utiliser les notifications UI Automation et autres fonctionnalités UI Automation. Les développeurs peuvent maintenant utiliser les notifications UI Automation que le Narrateur peut annoncer pour indiquer la progression.
Pour obtenir une vue d’ensemble de la vue d’ensemble des événements UI Automation, notamment les événements de notification UI Automation, consultez la [vue d’ensemble des événements UI Automation](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview).

**Prise en charge améliorée de l’accessibilité PropertyGrid**

- Activation de la prise en charge d’UI Automation pour le contrôle <xref:System.Windows.Forms.PropertyGrid>, avec la possibilité d’utiliser les notifications UI Automation et autres fonctionnalités UI Automation.
- L’élément UI Automation qui correspond à la propriété en cours de modification est maintenant un enfant de l’élément UI Automation de l’élément de propriété correspondant.
- L’élément de l’élément de propriété UI Automation est maintenant un enfant de l’élément de catégorie correspondant si le contrôle <xref:System.Windows.Forms.PropertyGrid> parent est défini sur la vue des catégories.

**Prise en charge améliorée de ToolStrip**

- Activation de la prise en charge d’UI Automation pour le contrôle <xref:System.Windows.Forms.ToolStrip>, avec la possibilité d’utiliser les notifications UI Automation et autres fonctionnalités UI Automation.
- Amélioration de la navigation des éléments <xref:System.Windows.Forms.ToolStrip>.
- En mode Éléments, le focus du Narrateur ne disparaît pas et ne va pas vers les éléments masqués.

**Amélioration des signaux visuels**

- Un contrôle <xref:System.Windows.Forms.CheckedListBox> vide affiche maintenant un indicateur de focus quand il reçoit le focus.
Remarque : la prise en charge d’UI Automation est activée pour les contrôles dans l’exécution, mais n’est pas utilisée au moment du Design. Pour une vue d’ensemble d’UI Automation, consultez la [Vue d’ensemble d’UI Automation](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).

**Appel des info-bulles des contrôles au clavier**

- Maintenant, vous pouvez utiliser le clavier pour appeler les info-bulles des contrôles en mettant le focus sur le contrôle souhaité. Cette fonctionnalité doit être activée explicitement pour l’application (voir la section ** &quot; Comment accepter ou refuser ces modifications &quot; **)

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Majeure       |
| Version | 4.8         |
| Type    | Reciblage |
