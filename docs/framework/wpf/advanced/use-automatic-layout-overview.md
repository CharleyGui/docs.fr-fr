---
title: Vue d'ensemble de l'utilisation de la disposition automatique
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 2fe473da3eeabef3852e3003e61b3b9604332855
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291272"
---
# <a name="use-automatic-layout-overview"></a>Vue d'ensemble de l'utilisation de la disposition automatique

Cette rubrique présente les instructions permettant aux développeurs d’écrire des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] avec des interfaces utilisateur localisables. Dans le passé, la localisation d’une interface utilisateur était un processus fastidieux. Chaque langue pour laquelle l’interface utilisateur a été adaptée a nécessité un réglage pixel par pixel. Aujourd’hui, avec les normes de conception et de codage appropriées, les interfaces utilisateur peuvent être créées afin que les localiseurs aient moins de redimensionnement et de repositionnement. L’approche consistant à écrire des applications qui peuvent être plus facilement redimensionnées et repositionnées est appelée disposition automatique et peut être obtenue à l’aide de la conception d’application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a>Avantages de l’utilisation de la disposition automatique

Étant donné que le système de présentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est puissant et flexible, il offre la possibilité de mettre en forme les éléments d’une application qui peuvent être ajustés en fonction des besoins des différentes langues. La liste suivante souligne quelques-uns des avantages de la disposition automatique.

- L’interface utilisateur s’affiche correctement dans n’importe quelle langue.

- Réduit le besoin de réajuster la position et la taille des contrôles une fois le texte traduit.

- Réduit le besoin de réajuster la taille de la fenêtre.

- La disposition de l’interface utilisateur s’affiche correctement dans n’importe quelle langue.

- La localisation peut se trouver réduite à sa plus simple expression, à savoir la traduction d’une chaîne.

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a>Disposition automatique et contrôles

La disposition automatique permet à une application d’ajuster automatiquement la taille d’un contrôle. Par exemple, un contrôle peut changer pour accommoder la longueur d’une chaîne. Cette fonctionnalité permet aux responsables de la localisation de traduire la chaîne sans devoir redimensionner le contrôle pour que le texte traduit s’ajuste. L’exemple suivant crée un bouton avec un contenu en anglais.

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

Dans l’exemple, il vous suffit de changer le texte pour que le bouton soit en espagnol. Par exemple :

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

Le graphique suivant montre la sortie des exemples de code :

![Même bouton avec le texte dans différentes langues](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a>Disposition automatique et normes de codage

L’utilisation de l’approche de mise en page automatique requiert un ensemble de règles et de normes de codage et de conception pour produire une interface utilisateur entièrement localisable. Les indications suivantes vont simplifier le codage de votre disposition automatique.

**N’utilisez pas de positions absolues**

- N’utilisez pas <xref:System.Windows.Controls.Canvas>, car il positionne les éléments de manière absolue.

- Utilisez <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> et <xref:System.Windows.Controls.Grid> pour positionner les contrôles.

Pour plus d’informations sur les différents types de panneaux, consultez [vue d’ensemble des panneaux](../controls/panels-overview.md).

**Ne pas définir une taille fixe pour une fenêtre**

- Utilisez <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>. Exemple :

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**Ajouter un <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- Ajoutez un <xref:System.Windows.FrameworkElement.FlowDirection%2A> à l’élément racine de votre application.

  WPF offre un moyen pratique de prendre en charge les dispositions horizontales, bidirectionnelles et verticales. Dans Presentation Framework, la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> peut être utilisée pour définir la disposition. Les modèles de sens du déroulement sont les suivants :

  - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) : disposition horizontale pour le latin, Asie de l’est, et ainsi de suite.

  - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) : bidirectionnel pour l’arabe, l’hébreu, etc.

**Utiliser des polices composites à la place des polices physiques**

- Avec les polices composites, la propriété <xref:System.Windows.Controls.Control.FontFamily%2A> n’a pas besoin d’être localisée.

- Les développeurs peuvent utiliser l’une des polices suivantes ou créer la leur.

  - Interface utilisateur globale
  - Sans Serif global
  - Serif global

**Ajouter XML : lang**

- Ajoutez l’attribut `xml:lang` dans l’élément racine de votre interface utilisateur, tel que `xml:lang="en-US"` pour une application en anglais.

- Étant donné que les polices composites utilisent `xml:lang` pour déterminer la police à utiliser, définissez cette propriété pour prendre en charge les scénarios multilingues.

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a>Disposition automatique et grilles

L’élément <xref:System.Windows.Controls.Grid>, est utile pour la disposition automatique, car il permet à un développeur de positionner des éléments. Un contrôle <xref:System.Windows.Controls.Grid> est en charge de la distribution de l’espace disponible parmi ses éléments enfants, à l’aide d’une disposition de colonne et de ligne. Les éléments d’interface utilisateur peuvent s’étendre sur plusieurs cellules et il est possible d’avoir des grilles dans des grilles. Les grilles sont utiles car elles vous permettent de créer et de positionner une interface utilisateur complexe. L’exemple suivant illustre l’utilisation d’une grille pour positionner des boutons et du texte. Notez que la hauteur et la largeur des cellules sont définies sur <xref:System.Windows.GridUnitType.Auto> ; par conséquent, la cellule qui contient le bouton avec une image s’ajuste pour correspondre à l’image.

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

Le graphique suivant montre la grille produite par le code précédent.

Grille ![exemple]de grille(./media/glob-grid.png "glob_grid")

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Disposition automatique et grilles avec la propriété IsSharedSizeScope

Un élément <xref:System.Windows.Controls.Grid> est utile dans les applications localisables pour créer des contrôles qui s’ajustent pour s’adapter au contenu. Cependant, il peut parfois être nécessaire que les contrôles conservent une taille particulière quel que soit le contenu. Par exemple, pour les boutons « OK », « Annuler » et « Parcourir », vous n’avez probablement pas besoin que les boutons s’adaptent à la taille du contenu. Dans ce cas, la propriété jointe <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> est utile pour partager le même dimensionnement entre plusieurs éléments de grille. L’exemple suivant montre comment partager des données de dimensionnement de colonne et de ligne entre plusieurs éléments <xref:System.Windows.Controls.Grid>.

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> Pour obtenir l’exemple de code complet, consultez [partager des propriétés de dimensionnement entre grilles](../controls/how-to-share-sizing-properties-between-grids.md).

## <a name="see-also"></a>Voir aussi

- [Globalisation pour WPF](globalization-for-wpf.md)
- [Utiliser la disposition automatique pour créer un bouton](how-to-use-automatic-layout-to-create-a-button.md)
- [Utiliser une grille pour la disposition automatique](how-to-use-a-grid-for-automatic-layout.md)
