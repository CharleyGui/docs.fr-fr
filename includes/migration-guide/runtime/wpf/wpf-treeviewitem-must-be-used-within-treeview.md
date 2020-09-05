---
ms.openlocfilehash: e9f769af6d85403c2a6f085cbc3462cf549adae9
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497707"
---
### <a name="wpf-treeviewitem-must-be-used-within-a-treeview"></a>Les éléments TreeViewItem WPF doivent être utilisés dans un contrôle TreeView

#### <a name="details"></a>Détails

Une modification a été introduite dans 4.5, qui limite l’utilisation des éléments <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> en dehors d’un <xref:System.Windows.Controls.TreeView?displayProperty=fullName>. Cette restriction est applicable dans les cas suivants :<ul><li>L’objet visuel parent de <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> n’est pas un panneau. (Un <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> généré pour un <xref:System.Windows.Controls.TreeView?displayProperty=fullName> aura un panneau comme parent)</li><li>Le <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> est un descendant d’un <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> agissant comme « hôte des éléments » pour un contrôle de liste (ListBox, DataGrid, ListView, etc.). Il n’est pas nécessaire d’activer la virtualisation.</li><li>Le <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> peut faire défiler les éléments (<code>ScrollUnit=&quot;Item&quot;</code>).</li><li><code>VirtualizingStackPanel.MakeVisible(v)</code> est appelé pour faire défiler un élément <code>v</code> dans l’affichage. Vous pouvez faire ceci de manière explicite ou implicite de différentes façons. Le moyen le plus courant est de cliquer sur <code>v</code> pour lui donner le focus clavier.</li><li>La chaîne du parent visuel de <code>v</code> à <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> passe par <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName>.</li></ul>En d’autres termes, cela se produit quand un <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> est utilisé en dehors d’un <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, et que l’utilisateur clique sur un descendant du <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> pour l’afficher. Si le <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> n’a pas de descendant pouvant recevoir le focus, vous ne rencontrez jamais ce problème. Cela peut se produire quand un <xref:System.Windows.Controls.TreeViewItem?displayProperty=fullName> est la racine d’un DataTemplate. Une exception InvalidCastException est alors levée dans le cadre de WPF.

#### <a name="suggestion"></a>Suggestion

Un correctif sera mis à disposition pour résoudre ce problème.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
