---
ms.openlocfilehash: 895d09e4ec39bd4a92ed1f4910da80474334d99b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496245"
---
### <a name="accessibility-improvements-in-wpf"></a>Améliorations apportées aux fonctionnalités d’accessibilité dans WPF

#### <a name="details"></a>Détails

**Améliorations apportées au mode Contraste élevé**

- Le focus pour le contrôle <xref:System.Windows.Controls.Expander> est désormais visible. Dans les versions précédentes de .NET Framework, ce n’était pas le tout.
- Quand les contrôles <xref:System.Windows.Controls.CheckBox> et <xref:System.Windows.Controls.RadioButton> sont sélectionnés, le texte qu’ils contiennent est plus facile à voir que dans les versions précédentes du .NET Framework.
- La bordure d’un <xref:System.Windows.Controls.ComboBox> désactivé est désormais de la même couleur que le texte désactivé. Dans les versions précédentes de .NET Framework, ce n’était pas le tout.
- Les boutons désactivés et ceux avec le focus utilisent désormais la bonne couleur de thème. Dans les versions précédentes de .NET Framework, ils ne l’ont pas fait.
- Le bouton déroulant est maintenant visible quand le <xref:System.Windows.Controls.ComboBox> style d’un contrôle a la valeur <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType> . Dans les versions précédentes de .NET Framework, ce n’était pas le tout.
- La flèche d’indicateur de tri dans un contrôle <xref:System.Windows.Controls.DataGrid> utilise désormais les couleurs de thème. Dans les versions précédentes de .NET Framework, ce n’était pas le fait.
- Le style de lien hypertexte par défaut utilise désormais la bonne couleur de thème quand l’utilisateur pointe dessus avec la souris. Dans les versions précédentes de .NET Framework, ce n’était pas le fait.
- Le focus clavier sur les boutons radio est désormais visible. Dans les versions précédentes de .NET Framework, ce n’était pas le tout.
- La colonne de cases à cocher du contrôle <xref:System.Windows.Controls.DataGrid> utilise désormais les couleurs attendues pour le focus clavier. Dans les versions précédentes de .NET Framework, ce n’était pas le fait.
- Les visuels du focus clavier sont désormais visibles sur les contrôles <xref:System.Windows.Controls.ComboBox> et <xref:System.Windows.Controls.ListBox>. Dans les versions précédentes de .NET Framework, ce n’était pas le tout.

**Améliorations apportées à l’interaction avec le lecteur d’écran**

- Les contrôles <xref:System.Windows.Controls.Expander> sont maintenant correctement annoncés comme groupes (développer/réduire) par les lecteurs d’écran.
- Les contrôles <xref:System.Windows.Controls.DataGridCell> sont maintenant correctement annoncés comme cellules de grille de données (version localisée) par les lecteurs d’écran.
- Les lecteurs d’écran annoncent désormais le nom d’un <xref:System.Windows.Controls.ComboBox> modifiable.
- <xref:System.Windows.Controls.PasswordBox> les contrôles ne sont plus annoncés comme « aucun élément dans la vue » par les lecteurs d’écran.

**Prise en charge des régions dynamiques**

Les lecteurs d’écran, tels que narrateur, aident les utilisateurs à comprendre l’interface utilisateur d’une application, généralement en décrivant l’élément d’interface utilisateur qui a actuellement le focus. Toutefois, si un élément de l’interface utilisateur n’a pas le focus et qu’il change à l’écran, l’utilisateur peut passer à côté d’informations importantes s’il n’en est pas informé. Les régions dynamiques sont conçues pour résoudre ce problème. Un développeur peut les utiliser pour informer le lecteur d’écran ou tout autre client [UI Automation](~/docs/framework/ui-automation/ui-automation-overview.md) qu’un changement important a été apporté à un élément d’interface utilisateur. Le lecteur d’écran peut ensuite décider comment et quand informer l’utilisateur de cette modification. La propriété LiveSetting indique également au lecteur d’écran qu’il est important d’informer l’utilisateur du changement apporté à l’interface utilisateur.

#### <a name="suggestion"></a>Suggestion

**Accepter ou refuser ces modifications**

Pour que l’application tire parti de ces modifications, elle doit s’exécuter sur .NET Framework 4.7.1 ou version ultérieure. Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :

- Ciblez .NET Framework 4.7.1. Il s’agit de l’approche recommandée. Ces changements d’accessibilité sont activés par défaut sur les applications WPF qui ciblent .NET Framework 4.7.1 ou version ultérieure.
- Refusez les comportements d’accessibilité hérités en ajoutant le [commutateur AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier de configuration de l’application et en lui affectant la valeur `false`, comme dans l’exemple suivant.

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
    </startup>
    <runtime>
      <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
    </runtime>
  </configuration>
  ```

Les applications qui ciblent .NET Framework 4.7.1 ou version ultérieure et souhaitent conserver le comportement d’accessibilité hérité peuvent s’abonner à l’utilisation des fonctionnalités d’accessibilité héritées en définissant explicitement ce commutateur AppContext sur `true` .
Pour obtenir une vue d’ensemble d’UI Automation, consultez [vue d’ensemble d’UI Automation](~/docs/framework/ui-automation/ui-automation-overview.md).

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Majeure       |
| Version | 4.7.1       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting(System.Windows.DependencyObject,System.Windows.Automation.AutomationLiveSetting)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting(System.Windows.DependencyObject)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore?displayProperty=nameWithType>
