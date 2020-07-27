---
title: Options de dimensionnement dans le contrôle DataGrid
description: Découvrez comment définir les lignes et les colonnes individuelles dans le contrôle DataGrid Windows Presentation Foundation pour ajuster la taille à leur contenu ou à des valeurs spécifiques.
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 0f10e385cbf18a26989614363ca6cd9f92bc83ec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164742"
---
# <a name="sizing-options-in-the-datagrid-control"></a>Options de dimensionnement dans le contrôle DataGrid
Différentes options sont disponibles pour contrôler la façon dont la <xref:System.Windows.Controls.DataGrid> taille est elle-même. <xref:System.Windows.Controls.DataGrid>, Et les lignes et colonnes individuelles dans le <xref:System.Windows.Controls.DataGrid> , peuvent être définies de façon à ce qu’elles soient redimensionnées automatiquement en fonction de leur contenu ou de valeurs spécifiques. Par défaut, le <xref:System.Windows.Controls.DataGrid> s’agrandit et diminue pour s’ajuster à la taille de son contenu.  
  
## <a name="sizing-the-datagrid"></a>Dimensionnement du DataGrid  
  
### <a name="cautions-when-using-automatic-sizing"></a>Précautions lors de l’utilisation du dimensionnement automatique  
 Par défaut, les <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> Propriétés et de <xref:System.Windows.Controls.DataGrid> ont la valeur <xref:System.Double.NaN?displayProperty=nameWithType> (" `Auto` " en XAML), et le <xref:System.Windows.Controls.DataGrid> s’ajuste à la taille de son contenu.  
  
 Lorsqu’il est placé à l’intérieur d’un conteneur qui ne restreint pas la taille de ses enfants, par exemple <xref:System.Windows.Controls.Canvas> ou <xref:System.Windows.Controls.StackPanel> , le <xref:System.Windows.Controls.DataGrid> s’étend au-delà des limites visibles du conteneur et les barres de défilement ne sont pas affichées. Cette condition a des implications en termes de convivialité et de performances.  
  
 Lorsqu’il est lié à un jeu de données, si le <xref:System.Windows.FrameworkElement.Height%2A> du <xref:System.Windows.Controls.DataGrid> n’est pas limité, il continue à ajouter une ligne pour chaque élément de données dans le jeu de données lié. Cela peut entraîner une augmentation de la taille du en <xref:System.Windows.Controls.DataGrid> dehors des limites visibles de votre application à mesure que des lignes sont ajoutées. <xref:System.Windows.Controls.DataGrid>Dans ce cas, le n’affiche pas de barres de défilement, car il <xref:System.Windows.FrameworkElement.Height%2A> continue à croître pour s’adapter aux nouvelles lignes.  
  
 Un objet est créé pour chaque ligne dans le <xref:System.Windows.Controls.DataGrid> . Si vous utilisez un jeu de données volumineux et que vous autorisez le <xref:System.Windows.Controls.DataGrid> à se Dimensionner automatiquement, la création d’un grand nombre d’objets peut affecter les performances de votre application.  
  
 Pour éviter ces problèmes lorsque vous travaillez avec des jeux de données volumineux, il est recommandé de définir spécifiquement le <xref:System.Windows.FrameworkElement.Height%2A> du <xref:System.Windows.Controls.DataGrid> ou de le placer dans un conteneur qui limitera son <xref:System.Windows.FrameworkElement.Height%2A> , tel qu’un <xref:System.Windows.Controls.Grid> . Lorsque le <xref:System.Windows.FrameworkElement.Height%2A> est limité, le <xref:System.Windows.Controls.DataGrid> crée uniquement les lignes qui tiennent dans son spécifié <xref:System.Windows.FrameworkElement.Height%2A> , et les recycle si nécessaire pour afficher les nouvelles données.  
  
### <a name="setting-the-datagrid-size"></a>Définition de la taille de DataGrid  
 <xref:System.Windows.Controls.DataGrid>Peut être défini pour une taille automatique dans les limites spécifiées, ou <xref:System.Windows.Controls.DataGrid> peut être défini sur une taille spécifique. Le tableau suivant présente les propriétés qui peuvent être définies pour contrôler la <xref:System.Windows.Controls.DataGrid> taille.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|Définit une hauteur spécifique pour <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|Définit la limite supérieure de la hauteur de <xref:System.Windows.Controls.DataGrid> . Le <xref:System.Windows.Controls.DataGrid> s’agrandit verticalement jusqu’à ce qu’il atteigne cette hauteur.|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|Définit la limite inférieure de la hauteur du <xref:System.Windows.Controls.DataGrid> . <xref:System.Windows.Controls.DataGrid>Est réduit verticalement jusqu’à ce qu’il atteigne cette hauteur.|  
|<xref:System.Windows.FrameworkElement.Width%2A>|Définit une largeur spécifique pour <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|Définit la limite supérieure pour la largeur de <xref:System.Windows.Controls.DataGrid> . Le <xref:System.Windows.Controls.DataGrid> s’agrandit horizontalement jusqu’à ce qu’il atteigne cette largeur.|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|Définit la limite inférieure pour la largeur de <xref:System.Windows.Controls.DataGrid> . Le <xref:System.Windows.Controls.DataGrid> s’agrandit horizontalement jusqu’à ce qu’il atteigne cette largeur.|  
  
## <a name="sizing-rows-and-row-headers"></a>Dimensionnement des lignes et des en-têtes de lignes  
  
### <a name="datagrid-rows"></a>Lignes DataGrid  
 Par défaut, <xref:System.Windows.Controls.DataGrid> la propriété d’une ligne <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Double.NaN?displayProperty=nameWithType> la valeur (" `Auto` " en XAML) et la hauteur de ligne s’étendra à la taille de son contenu. La hauteur de toutes les lignes dans <xref:System.Windows.Controls.DataGrid> peut être spécifiée en définissant la <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> propriété. Les utilisateurs peuvent modifier la hauteur de ligne en faisant glisser les séparateurs d’en-tête de ligne.  
  
### <a name="datagrid-row-headers"></a>En-têtes de lignes DataGrid  
 Pour afficher les en-têtes de lignes, la <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> propriété doit avoir la valeur <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> ou <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType> . Par défaut, les en-têtes de lignes sont affichés et ils se redimensionnent automatiquement en fonction de leur contenu. Les en-têtes de lignes peuvent avoir une largeur spécifique en définissant la <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> propriété.  
  
## <a name="sizing-columns-and-column-headers"></a>Dimensionnement des colonnes et des en-têtes de colonnes  
  
### <a name="datagrid-columns"></a>Colonnes DataGrid  
 <xref:System.Windows.Controls.DataGrid>Utilise des valeurs de <xref:System.Windows.Controls.DataGridLength> et de la <xref:System.Windows.Controls.DataGridLengthUnitType> structure pour spécifier des modes de dimensionnement absolus ou automatiques.  
  
 Le tableau suivant indique les valeurs fournies par la <xref:System.Windows.Controls.DataGridLengthUnitType> structure.  
  
|Nom|Description|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|Le mode de dimensionnement automatique par défaut redimensionne les <xref:System.Windows.Controls.DataGrid> colonnes en fonction du contenu des cellules et des en-têtes de colonnes.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|Le mode de dimensionnement automatique basé sur les cellules redimensionne les <xref:System.Windows.Controls.DataGrid> colonnes en fonction du contenu des cellules de la colonne, à l’exclusion des en-têtes de colonnes.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|Le mode de dimensionnement automatique basé sur l’en-tête redimensionne <xref:System.Windows.Controls.DataGrid> les colonnes en fonction du contenu des en-têtes de colonnes uniquement.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|Le mode de redimensionnement basé sur le pixel redimensionne les <xref:System.Windows.Controls.DataGrid> colonnes en fonction de la valeur numérique fournie.|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|Le mode de redimensionnement en étoile est utilisé pour distribuer l’espace disponible par proportions pondérées.<br /><br /> En XAML, les valeurs en étoile sont exprimées sous la forme n *, où n représente une valeur numérique. 1 \* équivaut à \* . Par exemple, si deux colonnes d’un <xref:System.Windows.Controls.DataGrid> ont des largeurs de largeur \* et 2 \* , la première colonne reçoit une partie de l’espace disponible et la deuxième colonne reçoit deux parties de l’espace disponible.|  
  
 La <xref:System.Windows.Controls.DataGridLengthConverter> classe peut être utilisée pour convertir des données entre valeurs numériques ou valeurs de chaîne et <xref:System.Windows.Controls.DataGridLength> valeurs.  
  
 Par défaut, la <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> propriété a la valeur <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A> et la <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> propriété a la valeur <xref:System.Windows.Controls.DataGridLength.Auto%2A> . Lorsque le mode de dimensionnement est défini sur <xref:System.Windows.Controls.DataGridLength.Auto%2A> ou <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A> , les colonnes s’étendent à la largeur de leur contenu visible le plus large. Lors du défilement, ces modes de dimensionnement entraînent le développement des colonnes si le contenu qui est plus grand que la taille de la colonne actuelle fait l’objet d’un défilement dans la vue. La colonne n’est pas réduite une fois que le contenu a été défilant hors de l’affichage.  
  
 Les colonnes de la <xref:System.Windows.Controls.DataGrid> peuvent également être définies pour une taille automatique uniquement dans les limites spécifiées, ou les colonnes peuvent être définies sur une taille spécifique. Le tableau suivant présente les propriétés qui peuvent être définies pour contrôler la taille des colonnes.  
  
|Propriété|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|Définit la limite supérieure de toutes les colonnes dans <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|Définit la limite supérieure pour une colonne individuelle. Remplace <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|Définit la limite inférieure de toutes les colonnes dans <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|Définit la limite inférieure pour une colonne individuelle. Remplace <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|Définit une largeur spécifique pour toutes les colonnes dans le <xref:System.Windows.Controls.DataGrid> .|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|Définit une largeur spécifique pour une colonne individuelle. Remplace <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>.|  
  
### <a name="datagrid-column-headers"></a>En-têtes de colonnes DataGrid  
 Par défaut, <xref:System.Windows.Controls.DataGrid> les en-têtes de colonnes sont affichés. Pour masquer les en-têtes de colonnes, la <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> propriété doit avoir la valeur <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> ou <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType> . Par défaut, lorsque des en-têtes de colonnes sont affichés, ils se redimensionnent automatiquement en fonction de leur contenu. Les en-têtes de colonnes peuvent recevoir une hauteur spécifique en définissant la <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> propriété.  
  
### <a name="resizing-with-the-mouse"></a>Redimensionnement avec la souris  
 Les utilisateurs peuvent redimensionner <xref:System.Windows.Controls.DataGrid> les lignes et les colonnes en faisant glisser les séparateurs d’en-têtes de lignes ou de colonnes. Le <xref:System.Windows.Controls.DataGrid> prend également en charge le redimensionnement automatique des lignes et des colonnes en double-cliquant sur le séparateur d’en-tête de ligne ou de colonne. Pour empêcher un utilisateur de redimensionner des colonnes particulières, affectez à la propriété la valeur <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> `false` pour les colonnes individuelles. Pour empêcher les utilisateurs de redimensionner toutes les colonnes, affectez à la propriété la valeur <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> `false` . Pour empêcher les utilisateurs de redimensionner toutes les lignes, affectez à la propriété la valeur <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> `false` .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>
