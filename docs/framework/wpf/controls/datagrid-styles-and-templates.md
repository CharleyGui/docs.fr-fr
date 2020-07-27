---
title: Styles et modèles DataGrid
description: En savoir plus sur les styles et les modèles pour le contrôle DataGrid Windows Presentation Foundation. Modifiez le ControlTemplate pour attribuer une apparence unique au contrôle.
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
ms.openlocfilehash: dd526ec64d5077dad58f31c004f47e63c57ec9de
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168335"
---
# <a name="datagrid-styles-and-templates"></a>Styles et modèles DataGrid
Cette rubrique décrit les styles et les modèles pour le <xref:System.Windows.Controls.DataGrid> contrôle. Vous pouvez modifier la valeur par défaut <xref:System.Windows.Controls.ControlTemplate> pour que le contrôle donne une apparence unique. Pour plus d’informations, consultez [créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md).  
  
## <a name="datagrid-parts"></a>Composants DataGrid  
 Le tableau suivant répertorie les parties nommées du <xref:System.Windows.Controls.DataGrid> contrôle.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|Ligne qui contient les en-têtes de colonnes.|  
  
 Lorsque vous créez un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.DataGrid> , votre modèle peut contenir un <xref:System.Windows.Controls.ItemsPresenter> dans un <xref:System.Windows.Controls.ScrollViewer> . (Le <xref:System.Windows.Controls.ItemsPresenter> affiche chaque élément dans <xref:System.Windows.Controls.DataGrid> ; le <xref:System.Windows.Controls.ScrollViewer> permet de faire défiler le contrôle).  Si le <xref:System.Windows.Controls.ItemsPresenter> n’est pas l’enfant direct de <xref:System.Windows.Controls.ScrollViewer> , vous devez fournir le <xref:System.Windows.Controls.ItemsPresenter> nom, `ItemsPresenter` .  
  
 Le modèle par défaut pour le <xref:System.Windows.Controls.DataGrid> contient un <xref:System.Windows.Controls.ScrollViewer> contrôle. Pour plus d’informations sur les composants définis par le <xref:System.Windows.Controls.ScrollViewer> , consultez [styles et modèles ScrollViewer](scrollviewer-styles-and-templates.md).  
  
## <a name="datagrid-states"></a>États de DataGrid  
 Le tableau suivant répertorie les États visuels du <xref:System.Windows.Controls.DataGrid> contrôle.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|Désactivé|CommonStates|Le contrôle est désactivé.|  
|InvalidFocused|ValidationStates|Le contrôle n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle est valide.|  
  
## <a name="datagridcell-parts"></a>Parties de DataGridCell  
 L' <xref:System.Windows.Controls.DataGridCell> élément n’a pas de parties nommées.  
  
## <a name="datagridcell-states"></a>États de DataGridCell  
 Le tableau suivant répertorie les États visuels de l' <xref:System.Windows.Controls.DataGridCell> élément.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur la cellule.|  
|Avec focus|FocusStates|La cellule a le focus.|  
|Sans focus|FocusStates|La cellule n’a pas le focus|  
|Actuel|CurrentStates|La cellule est la cellule active.|  
|Normal|CurrentStates|La cellule n’est pas la cellule active.|  
|Afficher|InteractionStates|La cellule est en mode d’affichage.|  
|Modification|InteractionStates|La cellule est en mode édition.|  
|Volumes sélectionnés|SelectionStates|La cellule est sélectionnée.|  
|Non sélectionné|SelectionStates|La cellule n’est pas sélectionnée.|  
|InvalidFocused|ValidationStates|La cellule n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|La cellule n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|La cellule est valide.|  
  
## <a name="datagridrow-parts"></a>Composants de DataGridRow  
 L' <xref:System.Windows.Controls.DataGridRow> élément n’a pas de parties nommées.  
  
## <a name="datagridrow-states"></a>États de DataGridRow  
 Le tableau suivant répertorie les États visuels de l' <xref:System.Windows.Controls.DataGridRow> élément.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur la ligne.|  
|MouseOver_Editing|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est en mode édition.|  
|MouseOver_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est sélectionnée.|  
|MouseOver_Unfocused_Editing|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est en mode édition et n’a pas le focus.|  
|MouseOver_Unfocused_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est sélectionnée et n’a pas le focus.|  
|Normal_AlternatingRow|CommonStates|La ligne est une ligne en alternance.|  
|Normal_Editing|CommonStates|La ligne est en mode édition.|  
|Normal_Selected|CommonStates|La ligne est sélectionnée.|  
|Unfocused_Editing|CommonStates|La ligne est en mode édition et n’a pas le focus.|  
|Unfocused_Selected|CommonStates|La ligne est sélectionnée et n’a pas le focus.|  
|InvalidFocused|ValidationStates|Le contrôle n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle est valide.|  
  
## <a name="datagridrowheader-parts"></a>Composants DataGridRowHeader  
 Le tableau suivant répertorie les parties nommées de l' <xref:System.Windows.Controls.Primitives.DataGridRowHeader> élément.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Élément utilisé pour redimensionner l’en-tête de ligne à partir du haut.|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Élément utilisé pour redimensionner l’en-tête de ligne à partir du bas.|  
  
## <a name="datagridrowheader-states"></a>États DataGridRowHeader  
 Le tableau suivant répertorie les États visuels de l' <xref:System.Windows.Controls.Primitives.DataGridRowHeader> élément.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de la souris est positionné sur la ligne.|  
|MouseOver_CurrentRow|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est la ligne actuelle.|  
|MouseOver_CurrentRow_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne, et la ligne est active et sélectionnée.|  
|MouseOver_EditingRow|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est en mode édition.|  
|MouseOver_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne et la ligne est sélectionnée.|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est active et sélectionnée et n’a pas le focus.|  
|MouseOver_Unfocused_EditingRow|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est en mode édition et n’a pas le focus.|  
|MouseOver_Unfocused_Selected|CommonStates|Le pointeur de la souris est positionné sur la ligne, la ligne est sélectionnée et n’a pas le focus.|  
|Normal_CurrentRow|CommonStates|La ligne est la ligne actuelle.|  
|Normal_CurrentRow_Selected|CommonStates|La ligne est la ligne actuelle et est sélectionnée.|  
|Normal_EditingRow|CommonStates|La ligne est en mode édition.|  
|Normal_Selected|CommonStates|La ligne est sélectionnée.|  
|Unfocused_CurrentRow_Selected|CommonStates|La ligne est la ligne actuelle, est sélectionnée et n’a pas le focus.|  
|Unfocused_EditingRow|CommonStates|La ligne est en mode édition et n’a pas le focus.|  
|Unfocused_Selected|CommonStates|La ligne est sélectionnée et n’a pas le focus.|  
|InvalidFocused|ValidationStates|Le contrôle n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle est valide.|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>Composants DataGridColumnHeadersPresenter  
 Le tableau suivant répertorie les parties nommées de l' <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> élément.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|Espace réservé pour les en-têtes de colonnes.|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>États DataGridColumnHeadersPresenter  
 Le tableau suivant répertorie les États visuels de l' <xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> élément.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|InvalidFocused|ValidationStates|La cellule n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|La cellule n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|La cellule est valide.|  
  
## <a name="datagridcolumnheader-parts"></a>Composants DataGridColumnHeader  
 Le tableau suivant répertorie les parties nommées de l' <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> élément.  
  
|Élément|Type|Description|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Élément utilisé pour redimensionner l’en-tête de colonne à partir de la gauche.|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|Élément utilisé pour redimensionner l’en-tête de colonne à partir de la droite.|  
  
## <a name="datagridcolumnheader-states"></a>États DataGridColumnHeader  
 Le tableau suivant répertorie les États visuels de l' <xref:System.Windows.Controls.Primitives.DataGridColumnHeader> élément.  
  
|Nom VisualState|Nom VisualStateGroup|Description|  
|-|-|-|  
|Normal|CommonStates|État par défaut.|  
|MouseOver|CommonStates|Le pointeur de souris est positionné sur le contrôle.|  
|Appuyé|CommonStates|Le contrôle est enfoncé.|  
|SortAscending|SortStates|La colonne est triée dans l’ordre croissant.|  
|SortDescending|SortStates|La colonne est triée par ordre décroissant.|  
|Non trié|SortStates|La colonne n’est pas triée.|  
|InvalidFocused|ValidationStates|Le contrôle n’est pas valide et a le focus.|  
|InvalidUnfocused|ValidationStates|Le contrôle n’est pas valide et n’a pas le focus.|  
|Valide|ValidationStates|Le contrôle est valide.|  
  
## <a name="datagrid-controltemplate-example"></a>Exemple de ControlTemplate DataGrid  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.ControlTemplate> pour le <xref:System.Windows.Controls.DataGrid> contrôle et ses types associés.  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 L’exemple précédent utilise une ou plusieurs des ressources suivantes.  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Pour voir l’exemple complet, consultez [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating) (Exemple de style avec ControlTemplates).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Styles et modèles Control](control-styles-and-templates.md)
- [Personnalisation des contrôles](control-customization.md)
- [Application d'un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Créer un modèle pour un contrôle](../../../desktop-wpf/themes/how-to-create-apply-template.md)
