---
title: Optimiser les performances des contrôles
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: d02fde7076cd6a24fdfb171ed54161b20f3d465e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746731"
---
# <a name="optimizing-performance-controls"></a>Optimisation des performances : contrôles

Windows Presentation Foundation (WPF) comprend un grand nombre des composants d’interface utilisateur (IU) communs qui sont utilisés dans la plupart des applications Windows. Cette rubrique présente des techniques destinées à améliorer les performances de votre interface utilisateur.

## <a name="displaying-large-data-sets"></a>Affichage de jeux de données volumineux

Les contrôles WPF tels que les <xref:System.Windows.Controls.ListView> et <xref:System.Windows.Controls.ComboBox> sont utilisés pour afficher des listes d’éléments dans une application. Si la liste à afficher est longue, les performances de l’application risquent de s’en être affectées. Cela s’explique par le fait que le système de disposition standard crée un conteneur de disposition pour chaque élément associé au contrôle de liste, puis calcule la taille et la position de sa disposition. En règle générale, vous n’avez pas besoin d’afficher tous les éléments en même temps ; il suffit en effet de n’en afficher qu’une partie et l’utilisateur parcourt la liste. Dans ce cas, il est judicieux d’utiliser la *virtualisation* de l’interface utilisateur : la génération du conteneur d’élément et le calcul de disposition associé d’un élément sont alors différés jusqu’à ce que cet élément soit visible.

La virtualisation de l’interface utilisateur est un aspect important des contrôles de liste. Il ne faut pas confondre la virtualisation de l’interface utilisateur et la virtualisation des données. La virtualisation de l’interface utilisateur ne stocke en mémoire que les éléments visibles, mais dans un scénario de liaison de données, elle stocke en mémoire l’ensemble de la structure de données. En revanche, dans le cas de la virtualisation des données, seuls sont stockées en mémoire les éléments de données qui sont visibles à l’écran.

Par défaut, la virtualisation de l’interface utilisateur est activée pour les contrôles <xref:System.Windows.Controls.ListView> et <xref:System.Windows.Controls.ListBox> lorsque leurs éléments de liste sont liés aux données. <xref:System.Windows.Controls.TreeView> la virtualisation peut être activée en affectant à la propriété jointe <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> la valeur `true`. Si vous souhaitez activer la virtualisation de l’interface utilisateur pour les contrôles personnalisés qui dérivent de <xref:System.Windows.Controls.ItemsControl> ou de contrôles d’élément existants qui utilisent la classe <xref:System.Windows.Controls.StackPanel>, tels que <xref:System.Windows.Controls.ComboBox>, vous pouvez définir la <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> sur <xref:System.Windows.Controls.VirtualizingStackPanel> et définir <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> sur `true`. Vous risquez malheureusement de désactiver la virtualisation de l’interface utilisateur pour ces contrôles sans vous en rendre compte. Voici la liste des situations qui entraînent la désactivation de la virtualisation de l’interface utilisateur :

- Les conteneurs d’éléments sont ajoutés directement au <xref:System.Windows.Controls.ItemsControl>. Par exemple, si une application ajoute explicitement des objets <xref:System.Windows.Controls.ListBoxItem> à un <xref:System.Windows.Controls.ListBox>, le <xref:System.Windows.Controls.ListBox> ne virtualise pas les objets <xref:System.Windows.Controls.ListBoxItem>.

- Les conteneurs d’éléments dans le <xref:System.Windows.Controls.ItemsControl> sont de types différents. Par exemple, un <xref:System.Windows.Controls.Menu> qui utilise des objets <xref:System.Windows.Controls.Separator> ne peut pas implémenter le recyclage d’éléments, car le <xref:System.Windows.Controls.Menu> contient des objets de type <xref:System.Windows.Controls.Separator> et <xref:System.Windows.Controls.MenuItem>.

- La définition de <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> sur `false`.

- La définition de <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> sur `false`.

Au moment de virtualiser des conteneurs d’éléments, il est important de déterminer si des informations d’état supplémentaire sont associées à un conteneur d’élément qui appartient à l’élément. Si tel est le cas, vous devez enregistrer l’état supplémentaire. Par exemple, vous pouvez avoir un élément contenu dans un contrôle <xref:System.Windows.Controls.Expander> et l’État <xref:System.Windows.Controls.Expander.IsExpanded%2A> est lié au conteneur de l’élément, et non à l’élément lui-même. Lorsque le conteneur est réutilisé pour un nouvel élément, la valeur actuelle de <xref:System.Windows.Controls.Expander.IsExpanded%2A> est utilisée pour le nouvel élément. En outre, l’ancien élément perd la valeur de <xref:System.Windows.Controls.Expander.IsExpanded%2A> correcte.

Actuellement, aucun contrôle WPF n’offre une prise en charge intégrée de la virtualisation des données.

## <a name="container-recycling"></a>Recyclage de conteneurs

Une optimisation de la virtualisation de l’interface utilisateur ajoutée à la .NET Framework 3,5 SP1 pour les contrôles qui héritent de <xref:System.Windows.Controls.ItemsControl> est le *recyclage de conteneurs,* qui peut également améliorer les performances de défilement. Lorsqu’un <xref:System.Windows.Controls.ItemsControl> qui utilise la virtualisation de l’interface utilisateur est rempli, il crée un conteneur d’élément pour chaque élément qui fait défiler l’affichage et détruit le conteneur d’élément pour chaque élément qui défile hors de l’affichage. Le *recyclage de conteneurs* permet au contrôle de réutiliser les conteneurs d’éléments existants pour différents éléments de données, de sorte que les conteneurs d’éléments ne sont pas créés et détruits en permanence lorsque l’utilisateur fait défiler le <xref:System.Windows.Controls.ItemsControl>. Vous pouvez choisir d’activer le recyclage d’éléments en affectant à la propriété jointe <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> la valeur <xref:System.Windows.Controls.VirtualizationMode.Recycling>.

Tout <xref:System.Windows.Controls.ItemsControl> qui prend en charge la virtualisation peut utiliser le recyclage de conteneurs. Pour obtenir un exemple d’activation du recyclage de conteneurs sur une <xref:System.Windows.Controls.ListBox>, consultez [améliorer les performances de défilement d’une zone de liste](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).

## <a name="supporting-bidirectional-virtualization"></a>Prise en charge de la virtualisation bidirectionnelle

<xref:System.Windows.Controls.VirtualizingStackPanel> offre une prise en charge intégrée de la virtualisation de l’interface utilisateur dans une seule direction, horizontalement ou verticalement. Si vous souhaitez utiliser la virtualisation bidirectionnelle pour vos contrôles, vous devez implémenter un panneau personnalisé qui étend la classe <xref:System.Windows.Controls.VirtualizingStackPanel>. La classe <xref:System.Windows.Controls.VirtualizingStackPanel> expose des méthodes virtuelles telles que <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>et <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Ces méthodes virtuelles vous permettent de détecter une modification dans la partie visible d’une liste et de la gérer en conséquence.

## <a name="optimizing-templates"></a>Optimisation des modèles

L’arborescence d’éléments visuels contient tous les éléments visuels d’une application. Elle contient non seulement les objets directement créés, mais aussi les objets résultant d’une expansion de modèle. Par exemple, lorsque vous créez un <xref:System.Windows.Controls.Button>, vous recevez également des objets <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> et <xref:System.Windows.Controls.ContentPresenter> dans l’arborescence d’éléments visuels. Si vous n’avez pas optimisé vos modèles de contrôle, vous risquez de créer de nombreux objets superflus dans l’arborescence visuelle. Pour plus d’informations sur l’arborescence d’éléments visuels, consultez [Vue d’ensemble du rendu graphique de WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md).

## <a name="deferred-scrolling"></a>Défilement différé

Par défaut, quand l’utilisateur fait glisser le curseur d’une barre de défilement, l’affichage du contenu est mis à jour en permanence. Si le défilement est lent dans votre contrôle, envisagez d’utiliser le défilement différé. Le contenu n’est alors mis à jour qu’à partir du moment où l’utilisateur arrête de faire glisser le curseur.

Pour implémenter le défilement différé, affectez à la propriété <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> la valeur `true`. <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> est une propriété jointe qui peut être définie sur <xref:System.Windows.Controls.ScrollViewer> et tout contrôle ayant un <xref:System.Windows.Controls.ScrollViewer> dans son modèle de contrôle.

## <a name="controls-that-implement-performance-features"></a>Contrôles qui implémentent des fonctionnalités de performances

Le tableau suivant répertorie les contrôles communs d’affichage de données et leur prise en charge des fonctionnalités de performances. Pour plus d’informations sur l’activation de ces fonctionnalités, consultez les sections précédentes.

|Contrôle|Virtualisation|Recyclage de conteneurs|Défilement différé|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|Peut être activé|Peut être activé|Peut être activé|
|<xref:System.Windows.Controls.ContextMenu>|Peut être activé|Peut être activé|Peut être activé|
|<xref:System.Windows.Controls.DocumentViewer>|Non disponible|Non disponible|Peut être activé|
|<xref:System.Windows.Controls.ListBox>|Default|Peut être activé|Peut être activé|
|<xref:System.Windows.Controls.ListView>|Default|Peut être activé|Peut être activé|
|<xref:System.Windows.Controls.TreeView>|Peut être activé|Peut être activé|Peut être activé|
|<xref:System.Windows.Controls.ToolBar>|Non disponible|Non disponible|Peut être activé|

> [!NOTE]
> Pour obtenir un exemple illustrant comment activer la virtualisation et le recyclage de conteneurs sur une <xref:System.Windows.Controls.TreeView>, consultez [améliorer les performances d’un contrôle TreeView](../controls/how-to-improve-the-performance-of-a-treeview.md).

## <a name="see-also"></a>Voir aussi

- [Disposition](layout.md)
- [Disposition et conception](optimizing-performance-layout-and-design.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Contrôles](../controls/index.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Procédure pas à pas : mise en cache de données d’application dans une application WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
