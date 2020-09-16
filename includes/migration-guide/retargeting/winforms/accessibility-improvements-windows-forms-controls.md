---
ms.openlocfilehash: fa24c664e9f7cf6da78d0703c7ebb52c8ebbec20
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606955"
---
### <a name="accessibility-improvements-in-windows-forms-controls"></a>Améliorations apportées aux fonctionnalités d’accessibilité dans les contrôles Windows Forms

#### <a name="details"></a>Détails

Windows Forms améliore la façon dont il utilise les technologies d’accessibilité pour mieux répondre aux besoins de ses clients. Elles présentent notamment les changements suivants, à compter de .NET Framework 4.7.1 :

- Changements visant à améliorer l’affichage en mode Contraste élevé.
- Changements visant à améliorer l’expérience dans l’explorateur de propriétés. Améliorations apportées à l’explorateur de propriétés. Parmi celles-ci :
- Une meilleure navigation au clavier via les différentes fenêtres de sélection de liste déroulante.
- Une réduction des taquets de tabulation inutiles.
- Des rapports plus élaborés sur les types de contrôles.
- Un comportement amélioré du Narrateur.
- Changements visant à implémenter les modèles d’accessibilité de l’interface utilisateur manquants dans les contrôles.

#### <a name="suggestion"></a>Suggestion

**Comment accepter ou refuser ces modifications** Pour que l’application tire parti de ces modifications, elle doit s’exécuter sur le .NET Framework 4.7.1 ou version ultérieure. Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :

- Recompilez-la pour qu’elle cible le .NET Framework 4.7.1. Ces changements d’accessibilité sont activés par défaut sur les applications Windows Forms qui ciblent le .NET Framework 4.7.1 ou ultérieur.
- Refusez les comportements d’accessibilité hérités en ajoutant le [commutateur AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier app.config et en lui affectant la valeur `false`, comme dans l’exemple suivant.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

Si votre application cible .NET Framework 4.7.1 ou une version ultérieure et que vous souhaitez conserver le comportement d’accessibilité hérité, choisissez d’utiliser les fonctionnalités d’accessibilité héritées en affectant explicitement à ce commutateur AppContext la valeur `true`.<p/>Pour une vue d’ensemble d’UI Automation, consultez la [Vue d’ensemble d’UI Automation](~/docs/framework/ui-automation/ui-automation-overview.md).<p/>**Ajout de la prise en charge des modèles et propriétés UI Automation**<br/>Les clients d’accessibilité peuvent tirer parti des nouvelles fonctionnalités d’accessibilité WinForms à l’aide de modèles d’appel courants décrits publiquement. Ces modèles ne sont pas spécifiques à WinForms. Par exemple, les clients d’accessibilité peuvent appeler la méthode QueryInterface sur l’interface IAccessible (MAAS) pour obtenir une interface IServiceProvider. Si cette interface est disponible, les clients peuvent utiliser sa méthode QueryService pour demander une interface IAccessibleEx. Pour plus d’informations, consultez [Utilisation d’IAccessibleEx à partir d’un client](/windows/desktop/WinAuto/using-iaccessibleex-from-a-client). À compter de .NET Framework 4.7.1, IServiceProvider et [IAccessibleEx](/windows/desktop/WinAuto/iaccessibleex) (le cas échéant) sont disponibles pour les objets d’accessibilité WinForms.<p/>.NET Framework 4.7.1 ajoute la prise en charge des modèles et des propriétés UI Automation suivants :

- Les contrôles <xref:System.Windows.Forms.ToolStripSplitButton> et <xref:System.Windows.Forms.ComboBox> prennent en charge le [modèle Développer/Réduire](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
- Le contrôle <xref:System.Windows.Forms.ToolStripMenuItem> a une valeur de propriété [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) égale à <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType>.
- Le contrôle <xref:System.Windows.Forms.ToolStripItem> prend en charge la propriété <xref:System.Windows.Automation.AutomationElement.NameProperty> et le [modèle Développer/Réduire](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
- Le contrôle <xref:System.Windows.Forms.ToolStripDropDownItem> prend en charge <xref:System.Windows.Forms.AccessibleEvents> indiquant StateChange et NameChange quand la liste déroulante est développée ou réduite.
- Le contrôle <xref:System.Windows.Forms.ToolStripDropDownButton> a une valeur de propriété [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) égale à <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType>.
- Le contrôle <xref:System.Windows.Forms.DataGridViewCheckBoxCell> prend en charge <xref:System.Windows.Automation.TogglePattern>.
- Les contrôles <xref:System.Windows.Forms.NumericUpDown> et <xref:System.Windows.Forms.DomainUpDown> prennent en charge la propriété <xref:System.Windows.Automation.AutomationElement.NameProperty> et ont un [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md) égal à <xref:System.Windows.Automation.ControlType.Spinner?displayProperty=nameWithType>.</p>
**Améliorations apportées au contrôle PropertyGrid** Le .NET Framework 4.7.1 ajoute les améliorations suivantes au contrôle PropertyBrowser :

- Le bouton **Détails**, qui se trouve dans la boîte de dialogue d’erreur qui s’affiche quand l’utilisateur entre une valeur incorrecte dans le contrôle <xref:System.Windows.Forms.PropertyGrid>, prend en charge le [modèle Développer/Réduire](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md), les notifications de changement de nom et d’état, et une propriété [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) avec la valeur <xref:System.Windows.Automation.ControlType.MenuItem?displayProperty=nameWithType>.
- Le volet de messages, qui s’affiche quand le bouton **Détails** de la boîte de dialogue d’erreur est développé, est désormais accessible au moyen du clavier et permet au Narrateur d’annoncer le contenu du message d’erreur.
- Le <xref:System.Windows.Forms.AccessibleRole> des lignes dans le contrôle <xref:System.Windows.Forms.PropertyGrid> est passé de &quot;Row&quot; à &quot;Cell&quot;. La cellule est mappée au ControlType UIA &quot;DataItem&quot;, ce qui lui permet de prendre en charge les raccourcis clavier appropriés et les annonces du Narrateur.
- Les lignes du contrôle <xref:System.Windows.Forms.PropertyGrid> qui représentent les éléments d’en-tête quand le contrôle <xref:System.Windows.Forms.PropertyGrid> a une propriété <xref:System.Windows.Forms.PropertyGrid.PropertySort> dont la valeur est <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> ont une valeur de propriété [ControlType](~/docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md) égale à <xref:System.Windows.Automation.ControlType.Button?displayProperty=nameWithType>.
- Les lignes du contrôle <xref:System.Windows.Forms.PropertyGrid> qui représentent les éléments d’en-tête quand le contrôle <xref:System.Windows.Forms.PropertyGrid> a une propriété <xref:System.Windows.Forms.PropertyGrid.PropertySort> dont la valeur est <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> prennent en charge le [modèle Développer/Réduire](~/docs/framework/ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
- Navigation au clavier améliorée entre la grille et de la barre d’outils située au-dessus. Le fait d’appuyer sur &quot;Maj+Tab&quot; sélectionne désormais le premier bouton de la barre d’outils, et non la barre d’outils entière.
- Les contrôles <xref:System.Windows.Forms.PropertyGrid> affichés en mode Contraste élevé dessinent désormais un rectangle de focus autour du bouton de barre d’outils qui correspond à la valeur de propriété <xref:System.Windows.Forms.PropertyGrid.PropertySort> actuelle.
- Les contrôles <xref:System.Windows.Forms.PropertyGrid> affichés en mode Contraste élevé et dont la propriété <xref:System.Windows.Forms.PropertyGrid.PropertySort> est définie avec la valeur <xref:System.Windows.Forms.PropertySort.Categorized?displayProperty=nameWithType> affichent désormais l’arrière-plan des en-têtes de catégorie dans une couleur très contrastée.
- Les contrôles <xref:System.Windows.Forms.PropertyGrid> permettent de mieux distinguer les éléments de barre d’outils ayant le focus de ceux qui indiquent la valeur actuelle de la propriété <xref:System.Windows.Forms.PropertyGrid.PropertySort>. Ce correctif se compose de deux changements : l’un visant le mode Contraste élevé et l’autre les scénarios n’utilisant pas ce mode.
- Les éléments de barre d’outils du contrôle <xref:System.Windows.Forms.PropertyGrid>, qui indiquent la valeur actuelle de la propriété <xref:System.Windows.Forms.PropertyGrid.PropertySort>, prennent en charge <xref:System.Windows.Automation.TogglePattern>.
- Prise en charge améliorée du Narrateur pour distinguer l’alignement sélectionné dans le sélecteur d’alignement.
- Quand un contrôle <xref:System.Windows.Forms.PropertyGrid> vide est affiché sur un formulaire, il reçoit désormais le focus. Ce n’était pas le cas avant.

**Utilisation des couleurs définies par le système d’exploitation dans les thèmes à contraste élevé**

- Les contrôles <xref:System.Windows.Forms.Button> et <xref:System.Windows.Forms.CheckBox> dont la propriété <xref:System.Windows.Forms.ButtonBase.FlatStyle> est définie avec la valeur <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType>, le style par défaut, utilisent désormais les couleurs définies par le système d’exploitation dans le thème à contraste élevé quand celui-ci est sélectionné. Avant, les couleurs du texte et de l’arrière-plan n’étaient pas contrastées et étaient difficiles à lire.
- Les contrôles <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, <xref:System.Windows.Forms.Label>, <xref:System.Windows.Forms.LinkLabel> et <xref:System.Windows.Forms.GroupBox> dont la propriété <xref:System.Windows.Forms.Control.Enabled> est définie avec la valeur **false** utilisaient une couleur ombrée pour afficher le texte dans les thèmes à contraste élevé, ce qui aboutissait à un faible contraste par rapport à l’arrière-plan. Ces contrôles utilisent à présent la couleur &quot;Texte désactivé&quot; définie par le système d’exploitation. Ce correctif s’applique aux contrôles dont la propriété `FlatStyle` est définie avec une valeur autre que <xref:System.Windows.Forms.FlatStyle.System?displayProperty=nameWithType>. Ces derniers contrôles sont affichés par le système d’exploitation.
- <xref:System.Windows.Forms.DataGridView> affiche maintenant un rectangle visible autour du contenu de la cellule qui a le focus. Ce rectangle était invisible dans certains thèmes à contraste élevé.
- Les contrôles <xref:System.Windows.Forms.ToolStripMenuItem> dont la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled> a la valeur **false** utilisent maintenant la couleur &quot;Texte désactivé&quot; définie par le système d’exploitation.
- Les contrôles <xref:System.Windows.Forms.ToolStripMenuItem> dont la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Checked> a la valeur **true** affichent maintenant la coche associée dans une couleur système contrastée.  Avant, la couleur de la coche n’était pas suffisamment contrastée et était invisible dans les thèmes à contraste élevé.
REMARQUE : Les valeurs de certaines couleurs système à contraste élevé ont changé dans Windows 10. Windows Forms Framework est basé sur le framework Win32. Pour une expérience optimale, exécutez sur la dernière version de Windows et inscrivez-vous aux modifications les plus récentes du système d’exploitation en ajoutant un fichier app. manifest dans une application de test et en annulant le commentaire du code suivant :

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

**Navigation au clavier améliorée**

- Quand la propriété <xref:System.Windows.Forms.ComboBox.DropDownStyle> d’un contrôle <xref:System.Windows.Forms.ComboBox> a la valeur <xref:System.Windows.Forms.ComboBoxStyle.DropDownList?displayProperty=nameWithType> et qu’il s’agit du premier contrôle dans l’ordre de tabulation sur le formulaire, un rectangle de focus apparaît désormais quand le formulaire parent est ouvert à l’aide du clavier. Avant ce changement, le focus clavier était sur ce contrôle, mais aucun indicateur de focus n’était affiché.

**Amélioration de la prise en charge du Narrateur**

- Le contrôle <xref:System.Windows.Forms.MonthCalendar> prend désormais en charge les technologies d’assistance pour accéder au contrôle, notamment la possibilité pour le Narrateur de lire la valeur du contrôle, ce qui n’était pas possible avant.

- Le contrôle <xref:System.Windows.Forms.CheckedListBox> avertit désormais le Narrateur quand une propriété <xref:System.Windows.Forms.CheckBox.CheckState?displayProperty=nameWithType> change. Le Narrateur ne recevait aucune notification, et les utilisateurs n’étaient pas informés de la mise à jour de la propriété <xref:System.Windows.Forms.CheckBox.CheckState>.
- Le contrôle <xref:System.Windows.Forms.LinkLabel> notifie le Narrateur du texte présent dans le contrôle de manière différente. Avant, le Narrateur annonçait ce texte à deux reprises et lisait les symboles &quot;&amp;&quot; comme du texte réel, alors qu’ils n’étaient pas visibles. Le texte en double a été supprimé des annonces du Narrateur, ainsi que les symboles &quot;&amp;&quot; inutiles.
- Les types de contrôle <xref:System.Windows.Forms.DataGridViewCell> signalent désormais correctement l’état en lecture seule au Narrateur et à d’autres technologies d’assistance.
- Le Narrateur peut désormais lire le menu système des fenêtres enfants dans les applications [Multiple-Document Interface]~/docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md).
- Le Narrateur peut désormais lire les contrôles <xref:System.Windows.Forms.ToolStripMenuItem> dont la propriété <xref:System.Windows.Forms.ToolStripItem.Enabled?displayProperty=nameWithType> a la valeur **false**. Avant, le Narrateur ne pouvait pas lire le contenu des éléments de menu désactivés.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Majeure       |
| Version | 4.8         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.ToolStripDropDownButton.CreateAccessibilityInstance?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownAccessibleObject.Name?displayProperty=nameWithType>
- [MonthCalendar.AccessibilityObject](xref:System.Windows.Forms.Control.AccessibilityObject)
