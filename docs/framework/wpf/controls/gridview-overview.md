---
title: Vue d'ensemble de GridView
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 98bc7985172cabeab19469af4b4c21e13a6bce73
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181898"
---
# <a name="gridview-overview"></a>Vue d'ensemble de GridView
<xref:System.Windows.Controls.GridView>le mode vue est l’un des modes de vue pour un <xref:System.Windows.Controls.ListView> contrôle. La <xref:System.Windows.Controls.GridView> classe et ses classes de support vous permettent, à vous et à vos utilisateurs, de visualiser les collections d’objets dans une table qui utilise généralement des boutons comme en-têtes de colonne interactive. Ce sujet introduit <xref:System.Windows.Controls.GridView> la classe et décrit son utilisation.  

<a name="DefiningaListViewthatusesGridViewView"></a>
## <a name="what-is-a-gridview-view"></a>Qu’est-ce qu’un affichage de grille ou GridView ?  
 Le <xref:System.Windows.Controls.GridView> mode de vue affiche une liste d’éléments de données en liant les champs de données aux colonnes et en affichant un en-tête de colonne pour identifier le champ. Le <xref:System.Windows.Controls.GridView> style par défaut implémente les boutons en tant qu’en-têtes de colonne. En utilisant des boutons pour les en-têtes de colonne, vous pouvez implémenter d’importantes capacités d’interaction utilisateur ; par exemple, les utilisateurs peuvent <xref:System.Windows.Controls.GridView> cliquer sur l’en-tête de la colonne pour trier les données en fonction du contenu d’une colonne spécifique.  
  
> [!NOTE]
> Les commandes <xref:System.Windows.Controls.GridView> de bouton qui utilisent <xref:System.Windows.Controls.Primitives.ButtonBase>pour les en-têtes de colonne sont dérivées de .  
  
 L’illustration suivante <xref:System.Windows.Controls.GridView> montre <xref:System.Windows.Controls.ListView> une vue du contenu.  

 ![Capture d’écran qui montre la vue GridView du contenu ListView.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>les colonnes <xref:System.Windows.Controls.GridViewColumn> sont représentées par des objets, qui peuvent automatiquement tailler à leur contenu. En option, vous pouvez <xref:System.Windows.Controls.GridViewColumn> définir explicitement une largeur spécifique. Vous pouvez redimensionner les colonnes en faisant glisser la barre de redimensionnement entre les en-têtes de colonnes. Vous pouvez également ajouter dynamiquement, supprimer, remplacer et réorganiser des <xref:System.Windows.Controls.GridView>colonnes parce que cette fonctionnalité est intégrée dans . Toutefois, <xref:System.Windows.Controls.GridView> ne peut pas mettre à jour directement les données qu’il affiche.  
  
 L’exemple suivant montre <xref:System.Windows.Controls.GridView> comment définir un qui affiche les données des employés. Dans cet <xref:System.Windows.Controls.ListView> exemple, `EmployeeInfoDataSource` définit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>le comme le . Les définitions <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> de <xref:System.Windows.Controls.GridViewColumn> propriété `EmployeeInfoDataSource` du contenu de lier aux catégories de données.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L’illustration suivante montre la table créée par l’exemple précédent. Le contrôle GridView affiche les données d’un objet ItemsSource :

 ![Capture d’écran qui montre une listé avec la sortie GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>
## <a name="gridview-layout-and-style"></a>Disposition et style de GridView  
 Les cellules de colonne et <xref:System.Windows.Controls.GridViewColumn> l’en-tête de colonne d’un ont la même largeur. Par défaut, chaque colonne adapte sa largeur à son contenu. Si vous le souhaitez, vous pouvez définir une colonne sur une largeur fixe.  
  
 Le contenu des données connexes s’affiche sur des lignes horizontales. Par exemple, dans l’illustration précédente, le nom, le prénom et le numéro d’identification de chaque employé s’affichent en tant qu’ensemble parce qu’ils apparaissent dans une ligne horizontale.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>
### <a name="defining-and-styling-columns-in-a-gridview"></a>Définir et appliquer un style aux colonnes dans GridView  
 Lors de la définition du <xref:System.Windows.Controls.GridViewColumn>champ <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>de <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>données <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> à afficher dans un , utilisez le , , ou des propriétés. La <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriété a préséance sur l’une ou l’autre des propriétés du modèle.  
  
 Pour spécifier l’alignement <xref:System.Windows.Controls.GridView>du contenu <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>dans une colonne d’un , définir un . N’utilisez <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> pas <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> le <xref:System.Windows.Controls.ListView> et les propriétés <xref:System.Windows.Controls.GridView>pour le contenu qui est affiché en utilisant un .  
  
 Pour spécifier des propriétés de <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.GridViewColumn>modèle <xref:System.Windows.Controls.GridViewColumnHeader> et de style pour les en-têtes de colonne, utilisez le , , et les classes. Pour plus d’informations, consultez [Vue d’ensemble des modèles et styles d’en-tête de colonne GridView](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>
### <a name="adding-visual-elements-to-a-gridview"></a>Ajout d’éléments visuels à un affichage GridView  
 Pour ajouter des éléments <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.Button> visuels, tels <xref:System.Windows.Controls.GridView> que et des contrôles, à un mode de vue, utilisez des modèles ou des styles.  
  
 Si vous définissez explicitement un élément visuel comme un élément <xref:System.Windows.Controls.GridView>de données, il ne peut apparaître qu’une seule fois dans un . Cette limitation existe parce qu’un élément ne peut avoir qu’un seul parent et par conséquent, ne peut apparaître qu’une seule fois dans l’arborescence visuelle.  
  
<a name="StylingRowsinaGridViewView"></a>
### <a name="styling-rows-in-a-gridview"></a>Appliquer un style à des lignes dans un affichage GridView  
 Utilisez <xref:System.Windows.Controls.GridViewRowPresenter> le <xref:System.Windows.Controls.GridViewHeaderRowPresenter> et les classes pour formater et afficher les rangées d’un <xref:System.Windows.Controls.GridView>. Pour un exemple de la façon <xref:System.Windows.Controls.GridView> de style lignes dans un mode vue, voir [Style a Row in a ListView That Implements a GridView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Problèmes d’alignement lorsque vous utilisez ItemContainerStyle  
 Pour éviter les problèmes d’alignement entre les en-têtes de colonne et les cellules, ne définissez pas une propriété ou ne spécifiez pas un modèle qui affecte la largeur d’un élément dans un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Par exemple, ne <xref:System.Windows.FrameworkElement.Margin%2A> définissez pas <xref:System.Windows.Controls.ControlTemplate> la <xref:System.Windows.Controls.CheckBox> propriété <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> ou ne spécifiez pas un qui ajoute un à un qui est défini sur un <xref:System.Windows.Controls.ListView> contrôle. Au lieu de cela, spécifiez les propriétés et les modèles qui affectent la largeur de la colonne directement sur les classes qui définissent un <xref:System.Windows.Controls.GridView> mode de vue.  
  
 Par exemple, pour <xref:System.Windows.Controls.CheckBox> ajouter un <xref:System.Windows.Controls.GridView> aux lignes en <xref:System.Windows.Controls.CheckBox> mode <xref:System.Windows.DataTemplate>vue, ajouter <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> le <xref:System.Windows.DataTemplate>à un , puis définir la propriété à cela .  
  
<a name="InteractingwithaGridViewControl"></a>
## <a name="user-interactions-with-a-gridview"></a>Interactions utilisateur avec un affichage GridView  
 Lorsque vous <xref:System.Windows.Controls.GridView> utilisez un dans votre application, les utilisateurs <xref:System.Windows.Controls.GridView>peuvent interagir avec et modifier le formatage de la . Par exemple, les utilisateurs peuvent réorganiser les colonnes, redimensionner une colonne, sélectionner des éléments dans une table et faire défiler le contenu. Vous pouvez également définir un gestionnaire d’événements qui répond lorsqu’un utilisateur clique sur le bouton d’en-tête de colonne. Le gestionnaire d’événements peut effectuer des opérations <xref:System.Windows.Controls.GridView> comme le tri des données qui sont affichées dans le contenu d’une colonne.  
  
 La liste suivante traite plus en <xref:System.Windows.Controls.GridView> détail des capacités d’utilisation pour l’interaction avec l’utilisateur :  
  
- **Réorganiser les colonnes à l’aide de la méthode glisser-déplacer.**  
  
     Les utilisateurs peuvent réorganiser <xref:System.Windows.Controls.GridView> les colonnes dans un en appuyant sur le bouton de la souris gauche alors qu’il est sur une tête de colonne, puis glisser cette colonne à une nouvelle position. Lorsque l’utilisateur fait glisser l’en-tête de colonne, une version flottante de l’en-tête s’affiche ainsi qu’une ligne noire unie qui indique où insérer la colonne.  
  
     Si vous souhaitez modifier le style par défaut pour <xref:System.Windows.Controls.ControlTemplate> la <xref:System.Windows.Controls.GridViewColumnHeader> version flottante d’un en-tête, spécifiez un pour un type qui est déclenché lorsque la <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> propriété est définie à <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>. Pour plus d’informations, consultez [Créer un style pour un en-tête de colonne GridView déplacé](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Redimensionner une colonne selon son contenu.**  
  
     Les utilisateurs peuvent double-cliquer sur la barre de redimensionnement à droite d’un en-tête de colonne afin de redimensionner une colonne en fonction de son contenu.  
  
    > [!NOTE]
    > Vous pouvez <xref:System.Windows.Controls.GridViewColumn.Width%2A> définir `Double.NaN` la propriété pour produire le même effet.  
  
- **Sélectionner des éléments de lignes.**  
  
     Les utilisateurs peuvent sélectionner un <xref:System.Windows.Controls.GridView>ou plusieurs éléments dans un .  
  
     Si vous souhaitez <xref:System.Windows.Style> modifier l’élément sélectionné, voir [Déclencheurs d’utilisation pour les éléments sélectionnés de style dans une ListView](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Faire défiler pour afficher le contenu qui n’est pas initialement visible à l’écran.**  
  
     Si la taille <xref:System.Windows.Controls.GridView> de la n’est pas assez grande pour afficher tous les éléments, les utilisateurs <xref:System.Windows.Controls.ScrollViewer> peuvent faire défiler horizontalement ou verticalement en utilisant des barres de défilement, qui sont fournis par un contrôle. A <xref:System.Windows.Controls.Primitives.ScrollBar> est caché si tout le contenu est visible dans une direction spécifique. Les en-têtes de colonnes ne défilent pas avec une barre de défilement verticale. Ils défilent horizontalement.  
  
- **Interagir avec les colonnes en cliquant sur les boutons d’en-tête de colonne.**  
  
     Lorsque les utilisateurs cliquent sur un bouton d’en-tête de colonne, ils peuvent trier les données qui s’affichent dans la colonne si vous avez fourni un algorithme de tri.  
  
     Vous pouvez <xref:System.Windows.Controls.Primitives.ButtonBase.Click> gérer l’événement pour les boutons d’en-tête de colonne afin de fournir des fonctionnalités comme un algorithme de tri. Pour gérer <xref:System.Windows.Controls.Primitives.ButtonBase.Click> l’événement pour une tête de <xref:System.Windows.Controls.GridViewColumnHeader>colonne unique, définissez un gestionnaire d’événement sur le . Pour définir un gestionnaire d’événements qui gère l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> pour <xref:System.Windows.Controls.ListView> tous les en-têtes de colonne, placez le gestionnaire sur le contrôle.  
  
<a name="Obtaining_Other_Custom_Views"></a>
## <a name="obtaining-other-custom-views"></a>Obtention d’autres vues personnalisées  
 La <xref:System.Windows.Controls.GridView> classe, qui est <xref:System.Windows.Controls.ViewBase> dérivée de la classe abstraite, <xref:System.Windows.Controls.ListView> n’est qu’un des modes de vue possibles pour la classe. Vous pouvez créer d’autres vues personnalisées en <xref:System.Windows.Controls.ListView> tirant de la <xref:System.Windows.Controls.ViewBase> classe. Pour obtenir un exemple de mode d’affichage personnalisé, consultez [Créer un mode d’affichage personnalisé pour un ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>
## <a name="gridview-supporting-classes"></a>Classes de prise en charge pour GridView  
 Les classes suivantes <xref:System.Windows.Controls.GridView> prennent en charge le mode de vue.  
  
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
- [Sujets comment se passer](listview-how-to-topics.md)
