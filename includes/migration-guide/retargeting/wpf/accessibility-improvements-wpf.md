---
ms.openlocfilehash: 47d3829748deef2c7c3610816b8941bf88da7ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614590"
---
### <a name="accessibility-improvements-in-wpf"></a>Améliorations apportées aux fonctionnalités d’accessibilité dans WPF

#### <a name="details"></a>Détails

**Améliorations apportées au mode Contraste élevé**
<ul><li>Le focus pour le contrôle <xref:System.Windows.Controls.Expander> est désormais visible. Dans les versions précédentes du .NET Framework, ce n’était pas le cas.
-Le texte des <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.RadioButton> contrôles et lorsqu’ils sont sélectionnés est désormais plus facile à voir que dans les versions précédentes de .NET Framework.
-La bordure d’un désactivé <xref:System.Windows.Controls.ComboBox> est désormais de la même couleur que le texte désactivé. Dans les versions précédentes du .NET Framework, ce n’était pas le cas.
-Les boutons désactivés et ayant le focus utilisent désormais la bonne couleur de thème. Dans les versions précédentes du .NET Framework, ce n’était pas le cas.
-Le bouton déroulant est maintenant visible quand le <xref:System.Windows.Controls.ComboBox> style d’un contrôle a <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType> la valeur, dans les versions précédentes du .NET Framework, ce n’était pas le cas.
-La flèche d’indicateur de tri dans un <xref:System.Windows.Controls.DataGrid> contrôle utilise désormais des couleurs de thème. Dans les versions précédentes du .NET Framework, ce n’était pas le cas.
-Le style de lien hypertexte par défaut est désormais remplacé par la couleur de thème correcte au pointage de la souris. Dans les versions précédentes du .NET Framework, ce n’était pas le cas.
-Le focus clavier sur les cases d’option est maintenant visible. Dans les versions précédentes du .NET Framework, ce n’était pas le cas.
-La <xref:System.Windows.Controls.DataGrid> colonne de case à cocher du contrôle utilise désormais les couleurs attendues pour les commentaires du focus clavier. Dans les versions précédentes du .NET Framework, ce n’était pas le cas.
-les visuels du focus clavier sont désormais visibles sur <xref:System.Windows.Controls.ComboBox> les <xref:System.Windows.Controls.ListBox> contrôles et. Dans les versions précédentes du .NET Framework, ce n’était pas le cas.</p>
**Améliorations de l’interaction des lecteurs d’écran**
<ul><li>Les contrôles <xref:System.Windows.Controls.Expander> sont maintenant correctement annoncés comme groupes (développer/réduire) par les lecteurs d’écran.
Les contrôles - <xref:System.Windows.Controls.DataGridCell> sont maintenant correctement annoncés comme cellules de grille de données (version localisée) par les lecteurs d’écran.
-Les lecteurs d’écran annoncent à présent le nom d’un modifiable <xref:System.Windows.Controls.ComboBox> .
Les lecteurs d’écran n’annoncent plus &quot;aucun élément dans la vue&quot; pour décrire les contrôles - <xref:System.Windows.Controls.PasswordBox>.</p>
**Support prise** Les lecteurs d’écran tels que le narrateur aident les personnes à connaître le contenu de l’interface utilisateur d’une application, généralement en décrivant une partie de l’interface utilisateur qui se concentre actuellement, car c’est probablement l’élément le plus intéressant pour l’utilisateur. Toutefois, si un élément de l’interface utilisateur n’a pas le focus et qu’il change à l’écran, l’utilisateur peut passer à côté d’informations importantes s’il n’en est pas informé. Les régions dynamiques sont conçues pour résoudre ce problème. Un développeur peut les utiliser pour informer le lecteur d’écran ou tout autre client [UI Automation](~/docs/framework/ui-automation/ui-automation-overview.md) qu’un changement important a été apporté à un élément d’interface utilisateur. Le lecteur d’écran peut ensuite décider comment et quand informer l’utilisateur de cette modification. La propriété LiveSetting indique également au lecteur d’écran qu’il est important d’informer l’utilisateur du changement apporté à l’interface utilisateur.

#### <a name="suggestion"></a>Suggestion

**Comment accepter ou refuser ces modifications** Pour que l’application tire parti de ces modifications, elle doit s’exécuter sur le .NET Framework 4.7.1 ou version ultérieure. Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :

- Ciblez .NET Framework 4.7.1. Il s’agit de l’approche recommandée. Ces changements d’accessibilité sont activés par défaut sur les applications WPF qui ciblent le .NET Framework 4.7.1 ou ultérieur.
- Refusez les comportements d’accessibilité hérités en ajoutant le [commutateur AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier de configuration de l’application et en lui affectant la valeur `false`, comme dans l’exemple suivant.

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

Si votre application cible .NET Framework 4.7.1 ou une version ultérieure et que vous souhaitez conserver le comportement d’accessibilité hérité, choisissez d’utiliser les fonctionnalités d’accessibilité héritées en affectant explicitement à ce commutateur AppContext la valeur `true`.
Pour une vue d’ensemble d’UI Automation, consultez la [Vue d’ensemble d’UI Automation](~/docs/framework/ui-automation/ui-automation-overview.md).

| Nom    | Valeur       |
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
