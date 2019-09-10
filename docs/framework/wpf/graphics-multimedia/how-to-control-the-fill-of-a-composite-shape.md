---
title: 'Procédure : Contrôler le remplissage d’une forme composite'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], composite [WPF], controlling fill
- composite shapes [WPF], controlling fill
- graphics [WPF], composite shapes
- fill [WPF], controlling
ms.assetid: c1c94575-9eca-48a5-a49a-2ec65259f229
ms.openlocfilehash: 89f69d392e8838af99538c759a2f06453e1bcd60
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855900"
---
# <a name="how-to-control-the-fill-of-a-composite-shape"></a>Procédure : Contrôler le remplissage d’une forme composite

La <xref:System.Windows.Media.GeometryGroup.FillRule%2A> propriété d’un <xref:System.Windows.Media.GeometryGroup> ou <xref:System.Windows.Media.PathGeometry>d’un, spécifie une « règle » que la forme composite utilise pour déterminer si un point donné fait partie de la géométrie. Il existe deux valeurs possibles pour <xref:System.Windows.Media.FillRule>: <xref:System.Windows.Media.FillRule.EvenOdd> et <xref:System.Windows.Media.FillRule.Nonzero>. Les sections suivantes décrivent comment utiliser ces deux règles.

**EvenOdd** Cette règle détermine si un point se trouve dans la région de remplissage en dessinant un rayon à partir de ce point vers l’infini dans n’importe quelle direction et en comptant le nombre de segments de chemin d’accès dans la forme donnée que le rayon traverse. Si ce nombre est impair, le point est à l’intérieur ; s’il est pair, le point est à l’extérieur.

Par exemple, le code XAML ci-dessous crée une forme composite composée d’une série d’anneaux concentriques ( <xref:System.Windows.Media.GeometryGroup.FillRule%2A> cible) <xref:System.Windows.Media.FillRule.EvenOdd>avec un défini sur.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleEvenOddValue](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillruleevenoddvalue)]

L’illustration suivante montre la forme créée dans l’exemple précédent.

![Cercle composé d’une série de sonneries concentriques avec des couleurs alternées.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-property.png)

Dans l’illustration précédente, Notez que le centre et le troisième anneau ne sont pas remplis. En effet, un rayon dessiné à partir de n’importe quel point dans un de ces deux anneaux traverse un nombre pair de segments. Consultez l’illustration suivante :

![Diagramme montrant les rayons EvenOdd dessinés dans le cercle.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-evenodd-rays.png)

**Différente** Cette règle détermine si un point se trouve dans la région de remplissage du tracé en dessinant un rayon à partir de ce point vers l’infini dans n’importe quelle direction, puis en examinant les emplacements où un segment de la forme coupe le rayon. En commençant à zéro, comptez un point chaque fois qu’un segment coupe le rayon de gauche à droite, et soustrayez un point chaque fois qu’un segment de tracé traverse le rayon de droite à gauche. Comptez ensuite le nombre d’intersections : si le résultat est égal à zéro, le point est à l’extérieur du tracé. Sinon, il est à l’intérieur.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValueEllipseGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovalueellipsegeometry)]

À l’aide de l’exemple précédent, <xref:System.Windows.Media.FillRule.Nonzero> la <xref:System.Windows.Media.GeometryGroup.FillRule%2A> valeur pour donne l’illustration suivante :

![Un cercle composé d’une série d’anneaux concentriques remplis avec la même couleur.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-nonzero.png)

Comme vous pouvez le voir, tous les anneaux sont remplis. En effet, tous les segments s’étendent dans la même direction, ce qui signifie qu’un rayon dessiné à partir de n’importe quel point traversera un ou plusieurs segments et que la somme des intersections ne sera pas égale à zéro. Par exemple, dans l’illustration suivante, les flèches rouges représentent la direction dans laquelle les segments sont dessinés et la flèche blanche représente un rayon arbitraire exécuté à partir d’un point dans l’anneau le plus profond. En commençant par une valeur égale à zéro, pour chaque segment que le rayon traverse, une valeur de un est ajoutée car le segment traverse le rayon de gauche à droite.

![Diagramme montrant la valeur de la propriété FillRule égale à différente de zéro.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-value-equal-nonzero.png)

Pour mieux illustrer le comportement <xref:System.Windows.Media.FillRule.Nonzero> de la règle, une forme plus complexe avec des segments exécutés dans des directions différentes est requise. Le code XAML ci-dessous crée une forme similaire à celle de l’exemple précédent, sauf qu' <xref:System.Windows.Media.PathGeometry> il est créé <xref:System.Windows.Media.EllipseGeometry> avec un plutôt qu’un qui crée quatre arcs concentriques, et non des cercles concentriques entièrement fermés.

[!code-xaml[GeometriesMiscSnippets_snip#FillRuleNonZeroValuePathGeometry](~/samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/FillRuleExample.xaml#fillrulenonzerovaluepathgeometry)]

L’illustration suivante montre la forme créée dans l’exemple précédent.

![Cercle composé d’une série de sonneries concentriques avec des couleurs alternées avec le troisième arc non rempli.](./media/how-to-control-the-fill-of-a-composite-shape/pathgeometry-concentric-arcs.png)

Notez que le troisième arc partant du centre n’est pas rempli. L’illustration suivante montre pourquoi il s’agit de. Dans l’illustration, les flèches rouges représentent la direction dans laquelle les segments sont dessinés. Les deux flèches blanches représentent deux rayons arbitraires qui partent d’un point dans la région « non remplie ». Comme le montre l’illustration, la somme des valeurs d’un rayon donné qui traverse les segments dans son tracé est égale à zéro. Comme indiqué ci-dessus, une somme égale à zéro signifie que le point ne fait pas partie de la géométrie (il ne fait pas partie du remplissage) tandis qu’une somme qui n’est *pas* égale à zéro, y compris une valeur négative, fait partie de la géométrie.

![Diagramme montrant des radiations arbitraires traversant des segments.](./media/how-to-control-the-fill-of-a-composite-shape/arbitrary-ray-cross-segment.png)

> [!NOTE]
> Dans le cadre de <xref:System.Windows.Media.FillRule>, toutes les formes sont considérées comme fermées. S’il y a un écart dans un segment, dessinez une ligne imaginaire pour le fermer. Dans l’exemple ci-dessus, on observe existe de petits écarts au niveau des anneaux. On peut donc s’attendre à ce qu’un rayon qui traverse cet écart produise un résultat différent de celui d’un rayon qui s’étend dans une autre direction. Vous trouverez ci-dessous une illustration agrandie de l’un de ces écarts et du « segment imaginaire » (segment qui est dessiné <xref:System.Windows.Media.FillRule>à des fins d’application du) qui le ferme.

![Diagramme montrant les segments FillRule qui sont toujours fermés.](./media/how-to-control-the-fill-of-a-composite-shape/fillrule-closed-segments.png)

## <a name="example"></a>Exemple

## <a name="see-also"></a>Voir aussi

- [Créer une forme composite](how-to-create-a-composite-shape.md)
- [Vue d’ensemble de Geometry](geometry-overview.md)
