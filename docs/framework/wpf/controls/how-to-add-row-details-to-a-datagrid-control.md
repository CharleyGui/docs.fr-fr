---
title: 'Procédure : ajouter des détails de ligne à un contrôle DataGrid'
description: Découvrez comment personnaliser la présentation des données lorsque vous utilisez le contrôle DataGrid Windows Presentation Foundation en ajoutant une section de détails des lignes.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 8fd6b07f454681a0eed70d7a6208cfcc426dc920
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164952"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>Procédure : ajouter des détails de ligne à un contrôle DataGrid
Lorsque vous utilisez le <xref:System.Windows.Controls.DataGrid> contrôle, vous pouvez personnaliser la présentation des données en ajoutant une section de détails des lignes. L’ajout d’une section de détails de ligne vous permet de regrouper des données dans un modèle qui est éventuellement visible ou réduit. Par exemple, vous pouvez ajouter des détails de ligne à un <xref:System.Windows.Controls.DataGrid> qui présente uniquement un résumé des données de chaque ligne du <xref:System.Windows.Controls.DataGrid> , mais présente davantage de champs de données lorsque l’utilisateur sélectionne une ligne. Vous définissez le modèle pour la section de détails des lignes dans la <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> propriété. L’illustration suivante montre un exemple de section de détails de ligne.  
  
 ![DataGrid affiché avec détails de la ligne](./media/ndp-rowdetails.png "NDP_RowDetails")  
  
 Vous définissez le modèle de détails de ligne en tant que XAML inline ou en tant que ressource. Les deux approches sont présentées dans les procédures suivantes. Un modèle de données qui est ajouté en tant que ressource peut être utilisé dans tout le projet sans recréer le modèle. Un modèle de données ajouté en tant que code XAML inline est uniquement accessible à partir du contrôle dans lequel il est défini.  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>Pour afficher les détails des lignes à l’aide du code XAML inline  
  
1. Créez un <xref:System.Windows.Controls.DataGrid> qui affiche les données d’une source de données.  
  
2. Dans l'élément <xref:System.Windows.Controls.DataGrid>, ajoutez un élément <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>.  
  
3. Créez un <xref:System.Windows.DataTemplate> qui définit l’apparence de la section de détails des lignes.  
  
     Le code XAML suivant montre <xref:System.Windows.Controls.DataGrid> et comment définir le en <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> ligne. Le <xref:System.Windows.Controls.DataGrid> affiche trois valeurs dans chaque ligne et trois valeurs supplémentaires lorsque la ligne est sélectionnée.  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     Le code suivant montre la requête utilisée pour sélectionner les données qui sont affichées dans le <xref:System.Windows.Controls.DataGrid> . Dans cet exemple, la requête sélectionne des données à partir d’une entité qui contient des informations sur les clients.  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>Pour afficher les détails des lignes à l’aide d’une ressource  
  
1. Créez un <xref:System.Windows.Controls.DataGrid> qui affiche les données d’une source de données.  
  
2. Ajoutez un <xref:System.Windows.FrameworkElement.Resources%2A> élément à l’élément racine, tel qu’un <xref:System.Windows.Window> contrôle ou un <xref:System.Windows.Controls.Page> contrôle, ou ajoutez un <xref:System.Windows.Application.Resources%2A> élément à la <xref:System.Windows.Application> classe dans le fichier app. XAML (ou application. Xaml).  
  
3. Dans l’élément Resources, créez un <xref:System.Windows.DataTemplate> qui définit l’apparence de la section de détails des lignes.  
  
     Le code XAML suivant montre le <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> défini dans la <xref:System.Windows.Application> classe.  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. Sur le <xref:System.Windows.DataTemplate> , définissez la [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md) sur une valeur qui identifie de façon unique le modèle de données.  
  
5. Dans l' <xref:System.Windows.Controls.DataGrid> élément, affectez <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> à la propriété la ressource définie dans les étapes précédentes. Assignez la ressource en tant que ressource statique.  
  
     Le code XAML suivant montre la <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> propriété définie sur la ressource de l’exemple précédent.  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>Pour définir la visibilité et empêcher le défilement horizontal pour les détails de ligne  
  
1. Si nécessaire, affectez <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> une valeur à la propriété <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> .  
  
     Par défaut, la valeur est définie sur <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected> . Vous pouvez lui affecter <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> la valeur pour afficher les détails de toutes les lignes ou <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> pour masquer les détails de toutes les lignes.  
  
2. Si nécessaire, affectez à la propriété la valeur <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> `true` pour empêcher la section des détails des lignes de faire défiler horizontalement.
