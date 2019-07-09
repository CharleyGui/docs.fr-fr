---
title: Vue d'ensemble de l'utilisation de la disposition automatique
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: d4a0fd819d08fdd936dd1ef35e8cd8c00947f9e0
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662686"
---
# <a name="use-automatic-layout-overview"></a>Vue d'ensemble de l'utilisation de la disposition automatique

Cette rubrique présente des instructions pour les développeurs sur la façon d’écrire [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications localisables [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]. Dans le passé, la localisation d’une interface utilisateur a été beaucoup de temps. Chaque langue de l’interface utilisateur était adaptée nécessitait un réglage de pixel par pixel. Aujourd'hui, grâce à la conception et des normes de codage, de droite [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] peut être construite afin que les traducteurs aient moins de redimensionnement et de repositionnement. L’approche à écrire des applications qui peuvent être plus facilement redimensionnées et repositionnées est appelée à la disposition automatique et peut être obtenue en utilisant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] design de l’application.

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a>Avantages de l’utilisation de la disposition automatique

Étant donné que le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de présentation est puissant et flexible, il fournit la possibilité de disposer des éléments dans une application qui peuvent être ajustés pour répondre aux exigences des différentes langues. La liste suivante souligne quelques-uns des avantages de la disposition automatique.

- L’interface utilisateur s’affiche correctement dans n’importe quel langage.

- Réduit le besoin de réajuster la position et la taille des contrôles une fois le texte traduit.

- Réduit le besoin de réajuster la taille de la fenêtre.

- Disposition de l’interface utilisateur s’affiche correctement dans n’importe quel langage.

- La localisation peut se trouver réduite à sa plus simple expression, à savoir la traduction d’une chaîne.

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a>Disposition automatique et contrôles

La disposition automatique permet à une application d’ajuster automatiquement la taille d’un contrôle. Par exemple, un contrôle peut changer pour accommoder la longueur d’une chaîne. Cette fonctionnalité permet aux responsables de la localisation de traduire la chaîne sans devoir redimensionner le contrôle pour que le texte traduit s’ajuste. L’exemple suivant crée un bouton avec un contenu en anglais.

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

Dans l’exemple, il vous suffit de changer le texte pour que le bouton soit en espagnol. Par exemple :

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

Le graphique suivant illustre la sortie des exemples de code :

![Même bouton avec le texte dans différentes langues](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a>Disposition automatique et normes de codage

À l’aide de l’approche de la disposition automatique nécessite un ensemble de codage et de normes de conception et de règles pour créer une interface utilisateur entièrement localisable. Les indications suivantes vont simplifier le codage de votre disposition automatique.

**N’utilisez pas de positions absolues**

- N’utilisez pas <xref:System.Windows.Controls.Canvas> , car il positionne les éléments absolument.

- Utilisez <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, et <xref:System.Windows.Controls.Grid> pour positionner les contrôles.

Pour une discussion sur divers types de panneaux, consultez [vue d’ensemble de panneaux](../controls/panels-overview.md).

**Ne définissez pas une taille fixe pour une fenêtre**

- Utilisez <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>. Par exemple :

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**Ajouter un <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- Ajouter un <xref:System.Windows.FrameworkElement.FlowDirection%2A> à l’élément racine de votre application.

  WPF fournit un moyen pratique pour prendre en charge horizontales, bidirectionnelles et des dispositions verticales. Dans l’infrastructure de présentation, le <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété peut être utilisée pour définir la disposition. Les modèles de sens du déroulement sont les suivants :

  - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) : disposition horizontale pour le Latin, Asie de l’est et ainsi de suite.

  - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectionnelle pour l’arabe, hébreu et ainsi de suite.

**Utiliser des polices composites au lieu des polices physiques**

- Avec les polices composites, le <xref:System.Windows.Controls.Control.FontFamily%2A> propriété ne doit pas être localisé.

- Les développeurs peuvent utiliser l’une des polices suivantes ou créer la leur.

  - Interface utilisateur globale
  - Sans Serif global
  - Serif global

**Ajouter XML : lang**

- Ajouter le `xml:lang` attribut dans l’élément racine de votre interface utilisateur, tel que `xml:lang="en-US"` pour une application en anglais.

- Étant donné que les polices composites utilisent `xml:lang` pour déterminer la police à utiliser, définissez cette propriété pour prendre en charge les scénarios multilingues.

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a>Disposition automatique et grilles

Le <xref:System.Windows.Controls.Grid> élément, est utile pour la disposition automatique car il permet à un développeur positionner des éléments. Un <xref:System.Windows.Controls.Grid> contrôle est capable de répartir l’espace disponible entre ses éléments enfants, à l’aide d’une disposition de ligne et de colonne. Les éléments d’interface utilisateur peuvent s’étendre sur plusieurs cellules, et il est possible d’avoir des grilles imbriquées. Les grilles sont utiles, car ils vous permettent de créer et de positionner une interface utilisateur complexe. L’exemple suivant illustre l’utilisation d’une grille pour positionner des boutons et du texte. Notez que la hauteur et la largeur des cellules sont définies sur <xref:System.Windows.GridUnitType.Auto>; par conséquent, la cellule qui contient le bouton avec une image s’ajuste à l’image.

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

Le graphique suivant montre la grille produite par le code précédent.

![Exemple de grille](./media/glob-grid.png "glob_grid") grille

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Disposition automatique et grilles avec la propriété IsSharedSizeScope

Un <xref:System.Windows.Controls.Grid> élément est utile dans des applications localisables pour créer des contrôles qui s’ajustent en fonction du contenu. Cependant, il peut parfois être nécessaire que les contrôles conservent une taille particulière quel que soit le contenu. Par exemple, pour les boutons « OK », « Annuler » et « Parcourir », vous n’avez probablement pas besoin que les boutons s’adaptent à la taille du contenu. Dans ce cas le <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> propriété jointe est utile pour partager le même dimensionnement entre plusieurs éléments de grille. L’exemple suivant montre comment partager des données entre plusieurs de dimensionnement de ligne et de colonne <xref:System.Windows.Controls.Grid> éléments.

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> Pour l’exemple de code complet, consultez [partage de propriétés de dimensionnement entre grilles](../controls/how-to-share-sizing-properties-between-grids.md)

## <a name="see-also"></a>Voir aussi

- [Globalisation pour WPF](globalization-for-wpf.md)
- [Utiliser la disposition automatique pour créer un bouton](how-to-use-automatic-layout-to-create-a-button.md)
- [Utiliser une grille pour la disposition automatique](how-to-use-a-grid-for-automatic-layout.md)
