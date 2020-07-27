---
title: Vue d'ensemble de GridView
description: En savoir plus sur les styles et les modèles pour le contrôle ListView Windows Presentation Foundation. Modifiez le ControlTemplate pour attribuer une apparence unique au contrôle.
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 02a2182ef1fc893107e434f431b9fbe0b3fbcd08
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165921"
---
# <a name="gridview-overview"></a>Vue d'ensemble de GridView
<xref:System.Windows.Controls.GridView>le mode d’affichage est l’un des modes d’affichage d’un <xref:System.Windows.Controls.ListView> contrôle. La <xref:System.Windows.Controls.GridView> classe et ses classes de prise en charge permettent à vous et à vos utilisateurs d’afficher des collections d’éléments dans une table qui utilise généralement des boutons comme en-têtes de colonnes interactifs. Cette rubrique présente la <xref:System.Windows.Controls.GridView> classe et décrit son utilisation.  

<a name="DefiningaListViewthatusesGridViewView"></a>
## <a name="what-is-a-gridview-view"></a>Qu’est-ce qu’un affichage de grille ou GridView ?  
 Le <xref:System.Windows.Controls.GridView> mode d’affichage affiche une liste d’éléments de données en liant les champs de données aux colonnes et en affichant un en-tête de colonne pour identifier le champ. Le style par défaut <xref:System.Windows.Controls.GridView> implémente des boutons comme en-têtes de colonnes. En utilisant des boutons pour les en-têtes de colonnes, vous pouvez implémenter des fonctionnalités d’interaction utilisateur importantes. par exemple, les utilisateurs peuvent cliquer sur l’en-tête de colonne pour trier <xref:System.Windows.Controls.GridView> les données en fonction du contenu d’une colonne spécifique.  
  
> [!NOTE]
> Les contrôles bouton que <xref:System.Windows.Controls.GridView> utilise pour les en-têtes de colonnes sont dérivés de <xref:System.Windows.Controls.Primitives.ButtonBase> .  
  
 L’illustration suivante montre une <xref:System.Windows.Controls.GridView> vue du <xref:System.Windows.Controls.ListView> contenu.  

 ![Capture d’écran montrant la vue GridView du contenu ListView.](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>les colonnes sont représentées par des <xref:System.Windows.Controls.GridViewColumn> objets, qui peuvent être automatiquement redimensionnés en fonction de leur contenu. Si vous le souhaitez, vous pouvez affecter explicitement <xref:System.Windows.Controls.GridViewColumn> à une largeur spécifique. Vous pouvez redimensionner les colonnes en faisant glisser la barre de redimensionnement entre les en-têtes de colonnes. Vous pouvez également ajouter, supprimer, remplacer et réorganiser des colonnes dynamiquement, car cette fonctionnalité est intégrée à <xref:System.Windows.Controls.GridView> . Toutefois, <xref:System.Windows.Controls.GridView> ne peut pas mettre à jour directement les données qu’il affiche.  
  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.GridView> qui affiche les données des employés. Dans cet exemple, <xref:System.Windows.Controls.ListView> définit le `EmployeeInfoDataSource` comme <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> . Définitions de propriétés de <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> lier du <xref:System.Windows.Controls.GridViewColumn> contenu à des `EmployeeInfoDataSource` catégories de données.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 L’illustration suivante montre la table créée par l’exemple précédent. Le contrôle GridView affiche les données d’un objet ItemsSource :

 ![Capture d’écran montrant une sortie de contrôle ListView avec GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>
## <a name="gridview-layout-and-style"></a>Disposition et style de GridView  
 Les cellules de colonne et l’en-tête de colonne d’un <xref:System.Windows.Controls.GridViewColumn> ont la même largeur. Par défaut, chaque colonne adapte sa largeur à son contenu. Si vous le souhaitez, vous pouvez définir une colonne sur une largeur fixe.  
  
 Le contenu des données connexes s’affiche sur des lignes horizontales. Par exemple, dans l’illustration précédente, le nom, le prénom et le numéro d’identification de chaque employé s’affichent en tant qu’ensemble parce qu’ils apparaissent dans une ligne horizontale.  
  
<a name="DefiningandStylingColumnsinaGridView"></a>
### <a name="defining-and-styling-columns-in-a-gridview"></a>Définir et appliquer un style aux colonnes dans GridView  
 Quand vous définissez le champ de données à afficher dans un <xref:System.Windows.Controls.GridViewColumn> , utilisez les <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> Propriétés, ou <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> . La <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> propriété est prioritaire sur l’une ou l’autre des propriétés de modèle.  
  
 Pour spécifier l’alignement du contenu dans une colonne d’un <xref:System.Windows.Controls.GridView> , définissez un <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> . N’utilisez pas les <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> Propriétés et pour <xref:System.Windows.Controls.ListView> le contenu qui s’affiche à l’aide d’un <xref:System.Windows.Controls.GridView> .  
  
 Pour spécifier des propriétés de style et de modèle pour les en-têtes de colonnes, utilisez les <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.GridViewColumn> classes, et <xref:System.Windows.Controls.GridViewColumnHeader> . Pour plus d’informations, consultez [Vue d’ensemble des modèles et styles d’en-tête de colonne GridView](gridview-column-header-styles-and-templates-overview.md).  
  
<a name="AddingVisualElementstoaGridViewView"></a>
### <a name="adding-visual-elements-to-a-gridview"></a>Ajout d’éléments visuels à un affichage GridView  
 Pour ajouter des éléments visuels, tels que <xref:System.Windows.Controls.CheckBox> les <xref:System.Windows.Controls.Button> contrôles et, à un mode d' <xref:System.Windows.Controls.GridView> affichage, utilisez des modèles ou des styles.  
  
 Si vous définissez explicitement un élément visuel en tant qu’élément de données, il ne peut apparaître qu’une seule fois dans un <xref:System.Windows.Controls.GridView> . Cette limitation existe parce qu’un élément ne peut avoir qu’un seul parent et par conséquent, ne peut apparaître qu’une seule fois dans l’arborescence visuelle.  
  
<a name="StylingRowsinaGridViewView"></a>
### <a name="styling-rows-in-a-gridview"></a>Appliquer un style à des lignes dans un affichage GridView  
 Utilisez les <xref:System.Windows.Controls.GridViewRowPresenter> <xref:System.Windows.Controls.GridViewHeaderRowPresenter> classes et pour mettre en forme et afficher les lignes d’un <xref:System.Windows.Controls.GridView> . Pour obtenir un exemple de style de lignes dans un <xref:System.Windows.Controls.GridView> mode d’affichage, consultez [appliquer un style à une ligne dans un ListView implémentant un GridView](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md).  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>Problèmes d’alignement lorsque vous utilisez ItemContainerStyle  
 Pour éviter les problèmes d’alignement entre les en-têtes de colonnes et les cellules, ne définissez pas une propriété ou spécifiez un modèle qui affecte la largeur d’un élément dans un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> . Par exemple, ne définissez pas la <xref:System.Windows.FrameworkElement.Margin%2A> propriété ou spécifiez un <xref:System.Windows.Controls.ControlTemplate> qui ajoute un <xref:System.Windows.Controls.CheckBox> à un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> défini sur un <xref:System.Windows.Controls.ListView> contrôle. Au lieu de cela, spécifiez les propriétés et les modèles qui affectent directement la largeur de colonne sur les classes qui définissent un <xref:System.Windows.Controls.GridView> mode d’affichage.  
  
 Par exemple, pour ajouter un <xref:System.Windows.Controls.CheckBox> aux lignes en <xref:System.Windows.Controls.GridView> mode affichage, ajoutez <xref:System.Windows.Controls.CheckBox> à un, puis <xref:System.Windows.DataTemplate> affectez à la propriété la valeur <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> <xref:System.Windows.DataTemplate> .  
  
<a name="InteractingwithaGridViewControl"></a>
## <a name="user-interactions-with-a-gridview"></a>Interactions utilisateur avec un affichage GridView  
 Lorsque vous utilisez un <xref:System.Windows.Controls.GridView> dans votre application, les utilisateurs peuvent interagir avec et modifier la mise en forme du <xref:System.Windows.Controls.GridView> . Par exemple, les utilisateurs peuvent réorganiser les colonnes, redimensionner une colonne, sélectionner des éléments dans une table et faire défiler le contenu. Vous pouvez également définir un gestionnaire d’événements qui répond lorsqu’un utilisateur clique sur le bouton d’en-tête de colonne. Le gestionnaire d’événements peut effectuer des opérations telles que le tri des données affichées dans le en <xref:System.Windows.Controls.GridView> fonction du contenu d’une colonne.  
  
 La liste suivante décrit plus en détail les fonctionnalités de l’utilisation <xref:System.Windows.Controls.GridView> de pour l’interaction avec l’utilisateur :  
  
- **Réorganiser les colonnes à l’aide de la méthode glisser-déplacer.**  
  
     Les utilisateurs peuvent réorganiser les colonnes d’un <xref:System.Windows.Controls.GridView> en appuyant sur le bouton gauche de la souris lorsqu’il se trouve sur un en-tête de colonne, puis en faisant glisser cette colonne vers une nouvelle position. Lorsque l’utilisateur fait glisser l’en-tête de colonne, une version flottante de l’en-tête s’affiche ainsi qu’une ligne noire unie qui indique où insérer la colonne.  
  
     Si vous souhaitez modifier le style par défaut pour la version flottante d’un en-tête, spécifiez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.GridViewColumnHeader> type qui est déclenché lorsque la <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> propriété a la valeur <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating> . Pour plus d’informations, consultez [Créer un style pour un en-tête de colonne GridView déplacé](how-to-create-a-style-for-a-dragged-gridview-column-header.md).  
  
- **Redimensionner une colonne selon son contenu.**  
  
     Les utilisateurs peuvent double-cliquer sur la barre de redimensionnement à droite d’un en-tête de colonne afin de redimensionner une colonne en fonction de son contenu.  
  
    > [!NOTE]
    > Vous pouvez affecter à la propriété la valeur <xref:System.Windows.Controls.GridViewColumn.Width%2A> `Double.NaN` pour produire le même effet.  
  
- **Sélectionner des éléments de lignes.**  
  
     Les utilisateurs peuvent sélectionner un ou plusieurs éléments dans un <xref:System.Windows.Controls.GridView> .  
  
     Si vous souhaitez modifier le <xref:System.Windows.Style> d’un élément sélectionné, consultez [utiliser des déclencheurs pour appliquer un style aux éléments sélectionnés d’un ListView](how-to-use-triggers-to-style-selected-items-in-a-listview.md).  
  
- **Faire défiler pour afficher le contenu qui n’est pas initialement visible à l’écran.**  
  
     Si la taille du <xref:System.Windows.Controls.GridView> n’est pas assez grande pour afficher tous les éléments, les utilisateurs peuvent faire défiler horizontalement ou verticalement en utilisant des barres de défilement, qui sont fournies par un <xref:System.Windows.Controls.ScrollViewer> contrôle. Un <xref:System.Windows.Controls.Primitives.ScrollBar> est masqué si tout le contenu est visible dans une direction spécifique. Les en-têtes de colonnes ne défilent pas avec une barre de défilement verticale. Ils défilent horizontalement.  
  
- **Interagir avec les colonnes en cliquant sur les boutons d’en-tête de colonne.**  
  
     Lorsque les utilisateurs cliquent sur un bouton d’en-tête de colonne, ils peuvent trier les données qui s’affichent dans la colonne si vous avez fourni un algorithme de tri.  
  
     Vous pouvez gérer l' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement pour les boutons d’en-tête de colonne afin de fournir des fonctionnalités telles qu’un algorithme de tri. Pour gérer l' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement pour un en-tête de colonne unique, définissez un gestionnaire d’événements sur <xref:System.Windows.Controls.GridViewColumnHeader> . Pour définir un gestionnaire d’événements qui gère l' <xref:System.Windows.Controls.Primitives.ButtonBase.Click> événement pour tous les en-têtes de colonnes, définissez le gestionnaire sur le <xref:System.Windows.Controls.ListView> contrôle.  
  
<a name="Obtaining_Other_Custom_Views"></a>
## <a name="obtaining-other-custom-views"></a>Obtention d’autres vues personnalisées  
 La <xref:System.Windows.Controls.GridView> classe, dérivée de la <xref:System.Windows.Controls.ViewBase> classe abstraite, n’est qu’un des modes d’affichage possibles pour la <xref:System.Windows.Controls.ListView> classe. Vous pouvez créer d’autres vues personnalisées pour <xref:System.Windows.Controls.ListView> en dérivant de la <xref:System.Windows.Controls.ViewBase> classe. Pour obtenir un exemple de mode d’affichage personnalisé, consultez [Créer un mode d’affichage personnalisé pour un ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="GridViewSupportingClasses"></a>
## <a name="gridview-supporting-classes"></a>Classes de prise en charge pour GridView  
 Les classes suivantes prennent en charge le <xref:System.Windows.Controls.GridView> mode d’affichage.  
  
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
- [Vue d'ensemble de ListView](listview-overview.md)
- [Trier une colonne GridView lors d’un clic sur un en-tête](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [Rubriques Comment](listview-how-to-topics.md)
