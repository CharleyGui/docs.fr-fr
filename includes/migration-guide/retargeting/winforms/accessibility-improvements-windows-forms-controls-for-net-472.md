---
ms.openlocfilehash: cc3c2c2be179842f87be8892d057a6c4138086cb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614566"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-472"></a>Améliorations apportées aux fonctionnalités d’accessibilité dans les contrôles Windows Forms pour .NET 4.7.2

#### <a name="details"></a>Détails

Windows Forms Framework améliore la façon dont il utilise les technologies d’accessibilité pour mieux répondre aux besoins de ses clients. Citons notamment les changements suivants :

- Changements visant à améliorer l’affichage en mode Contraste élevé.
- Changements visant à améliorer la navigation au clavier dans les contrôles DataGridView et MenuStrip.
- Changements apportés à l’interaction avec le Narrateur.

#### <a name="suggestion"></a>Suggestion

**Comment accepter ou refuser ces modifications** Pour que l’application tire parti de ces modifications, elle doit s’exécuter sur le .NET Framework 4.7.2 ou version ultérieure. Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :

- Recompilez-la pour qu’elle cible .NET Framework 4.7.2. Ces changements d’accessibilité sont activés par défaut sur les applications Windows Forms qui ciblent .NET Framework 4.7.2 ou ultérieur.
- Faites-lui cibler .NET Framework version 4.7.1 ou antérieure et refusez les comportements d’accessibilité hérités, en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant à la section `<runtime>` du fichier de configuration de l’application et en lui affectant la valeur `false`, comme dans l’exemple suivant.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
  </runtime>
</configuration>
```

Notez que pour accepter les fonctionnalités d’accessibilité ajoutées à .NET Framework 4.7.2, vous devez également accepter les fonctionnalités d’accessibilité de .NET Framework 4.7.1. Les applications qui ciblent le .NET Framework 4.7.2 ou version ultérieure et qui souhaitent conserver le comportement d’accessibilité hérité peuvent s’abonner à l’utilisation des fonctionnalités d’accessibilité héritées en affectant explicitement à ce commutateur AppContext la valeur `true` .

**Utilisation des couleurs définies par le système d’exploitation dans les thèmes à contraste élevé**

- La flèche déroulante de <xref:System.Windows.Forms.ToolStripDropDownButton> utilise désormais les couleurs définies par le système d’exploitation dans le thème à contraste élevé.
- Les contrôles <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> et <xref:System.Windows.Forms.CheckBox> dont le <xref:System.Windows.Forms.ButtonBase.FlatStyle> est défini avec la valeur <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> ou <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> utilisent désormais les couleurs définies par le système d’exploitation dans le thème à contraste élevé quand celui-ci est sélectionné. Avant, les couleurs du texte et de l’arrière-plan n’étaient pas contrastées et étaient difficiles à lire.
- Les contrôles à l’intérieur d’un <xref:System.Windows.Forms.GroupBox> dont la propriété <xref:System.Windows.Forms.Control.Enabled> a pour valeur `false` utilisent désormais les couleurs définies par le système d’exploitation dans le thème à contraste élevé.
- Les contrôles <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox> et <xref:System.Windows.Forms.ToolStripDropDownButton> ont un ratio contraste/luminosité accru dans le mode à contraste élevé.
- <xref:System.Windows.Forms.DataGridViewLinkCell> utilise par défaut les couleurs définies par le système d’exploitation en mode de contraste élevé pour la propriété <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor?displayProperty=nameWithType>.
REMARQUE : Les valeurs de certaines couleurs système à contraste élevé ont changé dans Windows 10. Windows Forms Framework est basé sur le framework Win32. Pour une expérience optimale, exécutez sur la dernière version de Windows et inscrivez-vous aux modifications les plus récentes du système d’exploitation en ajoutant un fichier app. manifest dans une application de test et en annulant le commentaire du code suivant :

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**Amélioration de la prise en charge du Narrateur**

- Le Narrateur annonce désormais la valeur de la propriété <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> quand il annonce le texte d’un <xref:System.Windows.Forms.ToolStripMenuItem>.
- Le Narrateur indique désormais quand un <xref:System.Windows.Forms.ToolStripMenuItem> a sa propriété <xref:System.Windows.Forms.Control.Enabled> définie sur `false`.
- Le Narrateur fournit désormais des commentaires sur l’état d’une case à cocher quand la propriété <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> est définie sur `true`.
- L’ordre de focus du mode balayage du narrateur est maintenant cohérent avec l’ordre visuel des contrôles dans la fenêtre de dialogue de téléchargement ClickOnce.

**Amélioration de la prise en charge de l’accessibilité DataGridView**

- Les lignes dans un <xref:System.Windows.Forms.DataGridView> peuvent désormais être triées à l’aide du clavier. Un utilisateur peut utiliser la touche F3 pour trier la colonne actuelle.
- Quand le <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> est défini sur <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, l’en-tête de colonne change de couleur pour indiquer la colonne actuelle quand l’utilisateur passe d’une cellule à l’autre de la ligne actuelle à l’aide de la touche Tab.
- La propriété <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Parent?displayProperty=nameWithType> retourne désormais le contrôle parent approprié.

**Amélioration des signaux visuels**

- Les contrôles <xref:System.Windows.Forms.RadioButton> et <xref:System.Windows.Forms.CheckBox> avec une propriété <xref:System.Windows.Forms.ButtonBase.Text> vide affichent désormais un indicateur de focus quand ils reçoivent le focus.

**Amélioration de la prise en charge de la grille de propriétés**

- Les éléments enfants du contrôle <xref:System.Windows.Forms.PropertyGrid> retournent désormais un `true` pour la propriété <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> uniquement quand un élément PropertyGrid est activé.
- Les éléments enfants du contrôle <xref:System.Windows.Forms.PropertyGrid> retournent désormais un `false` pour la propriété <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> uniquement quand un élément PropertyGrid peut être changé par l’utilisateur.
Pour une vue d’ensemble d’UI Automation, consultez la [Vue d’ensemble d’UI Automation](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</p>**Navigation au clavier améliorée**

- <xref:System.Windows.Forms.ToolStripButton>autorise désormais le focus quand il est contenu dans un <xref:System.Windows.Forms.ToolStripPanel> dont la propriété a la <xref:System.Windows.Forms.ToolStripPanel.TabStop> valeur `true` .

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Majeure       |
| Version | 4.7.2       |
| Type    | Reciblage |
