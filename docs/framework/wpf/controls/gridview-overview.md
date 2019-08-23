---
title: Vue d'ensemble de GridView
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 6da556296679de1161f609a7731c6fbf14e94730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966467"
---
# <a name="gridview-overview"></a>Vue d'ensemble de GridView
<xref:System.Windows.Controls.GridView>le mode d’affichage est l’un des modes d' <xref:System.Windows.Controls.ListView> affichage d’un contrôle. La <xref:System.Windows.Controls.GridView> classe et ses classes de prise en charge permettent à vous et à vos utilisateurs d’afficher des collections d’éléments dans une table qui utilise généralement des boutons comme en-têtes de colonnes interactifs. Cette rubrique présente la <xref:System.Windows.Controls.GridView> classe et décrit son utilisation.  

<a name="DefiningaListViewthatusesGridViewView"></a>   
## <a name="what-is-a-gridview-view"></a>Qu’est-ce qu’un affichage de grille ou GridView ?  
 Le <xref:System.Windows.Controls.GridView> mode d’affichage affiche une liste d’éléments de données en liant les champs de données aux colonnes et en affichant un en-tête de colonne pour identifier le champ. Le style <xref:System.Windows.Controls.GridView> par défaut implémente des boutons comme en-têtes de colonnes. En utilisant des boutons pour les en-têtes de colonnes, vous pouvez implémenter des fonctionnalités d’interaction utilisateur importantes. par exemple, les utilisateurs peuvent cliquer sur l’en- <xref:System.Windows.Controls.GridView> tête de colonne pour trier les données en fonction du contenu d’une colonne spécifique.  
  
> [!NOTE]
> Les contrôles bouton que <xref:System.Windows.Controls.GridView> utilise pour les en-têtes de colonnes <xref:System.Windows.Controls.Primitives.ButtonBase>sont dérivés de.  
  
 L’illustration suivante montre une <xref:System.Windows.Controls.GridView> vue du <xref:System.Windows.Controls.ListView> contenu.  
    
 ![Capture d’écran montrant la vue GridView du contenu ListView.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>les colonnes sont représentées par <xref:System.Windows.Controls.GridViewColumn> des objets, qui peuvent être automatiquement redimensionnés en fonction de leur contenu. Si vous le souhaitez, vous pouvez affecter <xref:System.Windows.Controls.GridViewColumn> explicitement à une largeur spécifique. Vous pouvez redimensionner les colonnes en faisant glisser la barre de redimensionnement entre les en-têtes de colonnes. Vous pouvez également ajouter, supprimer, remplacer et réorganiser des colonnes dynamiquement, car cette fonctionnalité est intégrée <xref:System.Windows.Controls.GridView>à. Toutefois, <xref:System.Windows.Controls.GridView> ne peut pas mettre à jour directement les données qu’il affiche.  
  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.GridView> qui affiche les données des employés. Dans cet exemple, <xref:System.Windows.Controls.ListView> définit le `EmployeeInfoDataSource` comme <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Définitions de propriétés de <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> lier <xref:System.Windows.Controls.GridViewColumn> du contenu `EmployeeInfoDataSource` à des catégories de données.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L’illustration suivante montre la table créée par l’exemple précédent. Le contrôle GridView affiche les données d’un objet ItemsSource:
    
 ![Capture d’écran montrant une sortie de contrôle ListView avec GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>   
## <a name="gridview-layout-and-style"></a>Disposition et style de GridView  
 Les cellules de colonne et l’en-tête <xref:System.Windows.Controls.GridViewColumn> de colonne d’un ont la même largeur. Par défaut, chaque colonne adapte sa largeur à son contenu. Si vous le souhaitez, vous pouvez définir une colonne sur une largeur fixe.  
  
 Le contenu des données connexes s’affiche sur des lignes horizontales. Par exemple, dans l’illustration précédente, le nom, le prénom et le numéro d’identification de chaque employé s’affichent en tant qu’ensemble parce qu’ils apparaissent dans une ligne horizontale.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>   
### <a name="defining-and-styling-columns-in-a-gridview"></a>Définir et appliquer un style aux colonnes dans GridView  
 Quand vous définissez le champ de données à afficher <xref:System.Windows.Controls.GridViewColumn>dans un, <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>utilisez <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>les propriétés <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> , ou. La <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriété est prioritaire sur l’une ou l’autre des propriétés de modèle.  
  
 Pour spécifier l’alignement du contenu dans une colonne d’un <xref:System.Windows.Controls.GridView>, définissez un <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>. N’utilisez pas les <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> propriétés <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> et pour <xref:System.Windows.Controls.ListView> le contenu qui s’affiche à l' <xref:System.Windows.Controls.GridView>aide d’un.  
  
 Pour spécifier des propriétés de style et de modèle pour les en- <xref:System.Windows.Controls.GridView>têtes <xref:System.Windows.Controls.GridViewColumn>de colonnes <xref:System.Windows.Controls.GridViewColumnHeader> , utilisez les classes, et. Pour plus d’informations, consultez [Vue d’ensemble des modèles et styles d’en-tête de colonne GridView](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>   
### <a name="adding-visual-elements-to-a-gridview"></a>Ajout d’éléments visuels à un affichage GridView  
 Pour ajouter des éléments visuels, tels <xref:System.Windows.Controls.CheckBox> que <xref:System.Windows.Controls.Button> les contrôles et, <xref:System.Windows.Controls.GridView> à un mode d’affichage, utilisez des modèles ou des styles.  
  
 Si vous définissez explicitement un élément visuel en tant qu’élément de données, il ne peut apparaître qu’une <xref:System.Windows.Controls.GridView>seule fois dans un. Cette limitation existe parce qu’un élément ne peut avoir qu’un seul parent et par conséquent, ne peut apparaître qu’une seule fois dans l’arborescence visuelle.  
  
<a name="StylingRowsinaGridViewView"></a>   
### <a name="styling-rows-in-a-gridview"></a>Appliquer un style à des lignes dans un affichage GridView  
 Utilisez les <xref:System.Windows.Controls.GridViewRowPresenter> classes <xref:System.Windows.Controls.GridViewHeaderRowPresenter> et pour mettre en forme et afficher les lignes <xref:System.Windows.Controls.GridView>d’un. Pour obtenir un exemple de style de lignes dans un <xref:System.Windows.Controls.GridView> mode d’affichage, consultez [appliquer un style à une ligne dans un ListView implémentant un GridView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>   
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Problèmes d’alignement lorsque vous utilisez ItemContainerStyle  
 Pour éviter les problèmes d’alignement entre les en-têtes de colonnes et les cellules, ne définissez pas une propriété ou spécifiez un modèle qui affecte <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>la largeur d’un élément dans un. Par exemple, ne définissez pas la <xref:System.Windows.FrameworkElement.Margin%2A> propriété ou spécifiez <xref:System.Windows.Controls.ControlTemplate> un qui ajoute <xref:System.Windows.Controls.CheckBox> un à <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> un défini sur un <xref:System.Windows.Controls.ListView> contrôle. Au lieu de cela, spécifiez les propriétés et les modèles qui affectent directement la largeur <xref:System.Windows.Controls.GridView> de colonne sur les classes qui définissent un mode d’affichage.  
  
 Par exemple, pour ajouter un <xref:System.Windows.Controls.CheckBox> aux lignes en <xref:System.Windows.Controls.GridView> mode <xref:System.Windows.Controls.CheckBox> affichage, ajoutez à un <xref:System.Windows.DataTemplate>, puis affectez à <xref:System.Windows.DataTemplate>la propriété <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> la valeur.  
  
<a name="InteractingwithaGridViewControl"></a>   
## <a name="user-interactions-with-a-gridview"></a>Interactions utilisateur avec un affichage GridView  
 Lorsque vous utilisez un <xref:System.Windows.Controls.GridView> dans votre application, les utilisateurs peuvent interagir avec et modifier la mise en forme <xref:System.Windows.Controls.GridView>du. Par exemple, les utilisateurs peuvent réorganiser les colonnes, redimensionner une colonne, sélectionner des éléments dans une table et faire défiler le contenu. Vous pouvez également définir un gestionnaire d’événements qui répond lorsqu’un utilisateur clique sur le bouton d’en-tête de colonne. Le gestionnaire d’événements peut effectuer des opérations telles que le tri des données affichées <xref:System.Windows.Controls.GridView> dans le en fonction du contenu d’une colonne.  
  
 La liste suivante décrit plus en détail les fonctionnalités de l’utilisation <xref:System.Windows.Controls.GridView> de pour l’interaction avec l’utilisateur:  
  
- **Réorganiser les colonnes à l’aide de la méthode glisser-déplacer.**  
  
     Les utilisateurs peuvent réorganiser les colonnes <xref:System.Windows.Controls.GridView> d’un en appuyant sur le bouton gauche de la souris lorsqu’il se trouve sur un en-tête de colonne, puis en faisant glisser cette colonne vers une nouvelle position. Lorsque l’utilisateur fait glisser l’en-tête de colonne, une version flottante de l’en-tête s’affiche ainsi qu’une ligne noire unie qui indique où insérer la colonne.  
  
     Si vous souhaitez modifier le style par défaut pour la version flottante d’un en-tête <xref:System.Windows.Controls.ControlTemplate> , spécifiez un pour un <xref:System.Windows.Controls.GridViewColumnHeader> type qui est <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> déclenché lorsque <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>la propriété a la valeur. Pour plus d’informations, consultez [Créer un style pour un en-tête de colonne GridView déplacé](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Redimensionner une colonne selon son contenu.**  
  
     Les utilisateurs peuvent double-cliquer sur la barre de redimensionnement à droite d’un en-tête de colonne afin de redimensionner une colonne en fonction de son contenu.  
  
    > [!NOTE]
    > Vous pouvez affecter à <xref:System.Windows.Controls.GridViewColumn.Width%2A> la `Double.NaN` propriété la valeur pour produire le même effet.  
  
- **Sélectionner des éléments de lignes.**  
  
     Les utilisateurs peuvent sélectionner un ou plusieurs éléments dans <xref:System.Windows.Controls.GridView>un.  
  
     Si vous souhaitez modifier le <xref:System.Windows.Style> d’un élément sélectionné, consultez utiliser des déclencheurs [pour appliquer un style aux éléments sélectionnés d’un ListView](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Faire défiler pour afficher le contenu qui n’est pas initialement visible à l’écran.**  
  
     Si la taille du <xref:System.Windows.Controls.GridView> n’est pas assez grande pour afficher tous les éléments, les utilisateurs peuvent faire défiler horizontalement ou verticalement en utilisant des barres de défilement, qui sont fournies par un <xref:System.Windows.Controls.ScrollViewer> contrôle. Un <xref:System.Windows.Controls.Primitives.ScrollBar> est masqué si tout le contenu est visible dans une direction spécifique. Les en-têtes de colonnes ne défilent pas avec une barre de défilement verticale. Ils défilent horizontalement.  
  
- **Interagir avec les colonnes en cliquant sur les boutons d’en-tête de colonne.**  
  
     Lorsque les utilisateurs cliquent sur un bouton d’en-tête de colonne, ils peuvent trier les données qui s’affichent dans la colonne si vous avez fourni un algorithme de tri.  
  
     Vous pouvez gérer l' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement pour les boutons d’en-tête de colonne afin de fournir des fonctionnalités telles qu’un algorithme de tri. Pour gérer l' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement pour un en-tête de colonne unique, définissez un gestionnaire <xref:System.Windows.Controls.GridViewColumnHeader>d’événements sur. Pour définir un gestionnaire d’événements qui gère <xref:System.Windows.Controls.Primitives.ButtonBase.Click> l’événement pour tous les en-têtes de colonnes, définissez <xref:System.Windows.Controls.ListView> le gestionnaire sur le contrôle.  
  
<a name="Obtaining_Other_Custom_Views"></a>   
## <a name="obtaining-other-custom-views"></a>Obtention d’autres vues personnalisées  
 La <xref:System.Windows.Controls.GridView> classe, dérivée de la <xref:System.Windows.Controls.ViewBase> classe abstraite, n’est qu’un des modes d’affichage possibles pour <xref:System.Windows.Controls.ListView> la classe. Vous pouvez créer d’autres vues personnalisées pour <xref:System.Windows.Controls.ListView> en dérivant de la <xref:System.Windows.Controls.ViewBase> classe. Pour obtenir un exemple de mode d’affichage personnalisé, consultez [Créer un mode d’affichage personnalisé pour un ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>   
## <a name="gridview-supporting-classes"></a>Classes de prise en charge pour GridView  
 Les classes suivantes prennent en <xref:System.Windows.Controls.GridView> charge le mode d’affichage.  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Controls.GridViewColumn>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.ViewBase>
- [Vue d’ensemble de ListView](listview-overview.md)
- [Trier une colonne GridView lors d’un clic sur un en-tête](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Rubriques de guide pratique](listview-how-to-topics.md)
