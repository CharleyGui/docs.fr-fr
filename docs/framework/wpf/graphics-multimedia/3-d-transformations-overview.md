---
title: Aperçu des transformations 3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D transformations
- transformations [WPF], 3D
ms.assetid: e45e555d-ac1e-4b36-aced-e433afe7f27f
ms.openlocfilehash: 0efd6d247f23760c878c82cc92e99f1b83c1b9d2
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112347"
---
# <a name="3d-transformations-overview"></a>Aperçu des transformations 3D
Ce sujet décrit comment appliquer les transformations aux [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] modèles 3D dans le système graphique. Les transformations permettent au développeur de repositionner, redimensionner et réorienter des modèles sans modifier les valeurs de base qui les définissent.  

## <a name="3d-coordinate-space"></a>Espace de coordonnées 3D  
 Le contenu graphique 3D est [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] encapsulé <xref:System.Windows.Controls.Viewport3D>dans un élément, qui peut participer à la structure d’élément bidimensionnel. Le système graphique traite Viewport3D comme un élément visuel à deux dimensions comme de nombreux autres éléments dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Viewport3D fonctionne comme une fenêtre, ou plus précisément une fenêtre d’affichage, dans une scène 3D. Plus précisément, il s’agit d’une surface sur laquelle une scène 3D est projetée.  Bien que vous puissiez utiliser Viewport3D avec d’autres objets de dessin 2D dans le même graphique de scène, vous ne pouvez pas interpénétrer les objets 2D et 3D dans un Viewport3D. Dans la discussion suivante, l’espace de coordonnées décrit est contenu par l’élément Viewport3D.  
  
 Le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] système de coordonnées des graphiques 2D localise l’origine en haut à gauche de la surface de rendu (généralement l’écran). Dans le système 2D, les valeurs positives à axe x procèdent aux valeurs de l’axe y droite et positives se poursuivent. Dans le système de coordonnées 3D, cependant, l’origine est située au centre de l’écran, avec des valeurs positives à axe x allant vers la droite mais des valeurs positives de l’axe Y allant vers le haut à la place, et des valeurs positives z-axe allant vers l’extérieur de l’origine, vers le spectateur.  
  
 ![Systèmes de coordonnées](./media/coordsystem-1.png "CoordSystem-1")  
Comparaison du système de coordonnées  
  
 L’espace défini par ces axes est le cadre de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]référence stationnaire pour les objets 3D dans . Lorsque vous générez des modèles dans cet espace et créez des lumières et des caméras pour les consulter, il est utile de distinguer ce frame stationnaire de référence, ou « espace universel » du frame local de référence que vous créez pour chaque modèle lorsque vous lui appliquez des transformations. N’oubliez également pas que les objets dans l’espace universel peuvent sembler entièrement différents, ou ne pas du tout être visibles, en fonction des paramètres de lumière et de caméra, mais que la position de la caméra ne modifie pas l’emplacement des objets dans l’espace universel.  
  
## <a name="transforming-models"></a>Transformation de modèles  
 Lorsque vous créez des modèles, ils ont un emplacement particulier dans la scène. Pour déplacer ces modèles dans la scène, pour les faire pivoter ou pour modifier leur taille, il n’est pas pratique de modifier les vertex qui définissent les modèles eux-mêmes. Au lieu de cela, tout comme en 2D, vous appliquez des transformations aux modèles.  
  
 Chaque objet modèle <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> a une propriété avec laquelle vous pouvez déplacer, réorienter ou redimensionner le modèle. Lorsque vous appliquez une transformation, vous décalez tous les points du modèle par le vecteur ou la valeur que la transformation spécifie. En d’autres termes, vous avez transformé l’espace de coordonnées dans lequel le modèle est défini (« espace de modèle »), mais vous n’avez pas modifié les valeurs qui composent la géométrie du modèle dans le système de coordonnées de la scène entière (« espace universel »).  
  
## <a name="translation-transformations"></a>Transformations de translation  
 Les transformations 3D héritent de la classe <xref:System.Windows.Media.Media3D.Transform3D>de base abstraite ; ceux-ci incluent les <xref:System.Windows.Media.Media3D.TranslateTransform3D>classes <xref:System.Windows.Media.Media3D.ScaleTransform3D>de <xref:System.Windows.Media.Media3D.RotateTransform3D>transformation d’affine, , , et . Le [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] système 3D <xref:System.Windows.Media.Media3D.MatrixTransform3D> fournit également une classe qui vous permet de spécifier les mêmes transformations dans des opérations de matrice plus concises.  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D>déplace tous les points dans le Model3D dans la <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A>direction <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetY%2A>du <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetZ%2A> vecteur de compensation que vous spécifiez avec le , , et les propriétés. Par exemple, en prenant un vertex d’un cube à (2,2,2), un vecteur de décalage de (0, 1,6, 1) déplacerait ce vertex de (2,2,2) à (2, 3,6, 3). Le vertex du cube est toujours (2,2,2) dans l’espace du modèle, mais désormais l’espace du modèle a modifié sa relation à l’espace universel afin que (2,2,2) dans l’espace du modèle soit (2, 3,6, 3) dans l’espace universel.  
  
 ![Figure de translation](./media/transforms-translate.png "Transforme-Traduire")  
Translation avec décalage  
  
 Les exemples de code suivants montrent comment appliquer une translation.  
  
 [!code-xaml[animation3dgallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="scale-transformations"></a>Transformations d’échelle  
 <xref:System.Windows.Media.Media3D.ScaleTransform3D>modifie l’échelle du modèle par un vecteur d’échelle spécifié en référence à un point central. Spécifiez une échelle uniforme, qui met à l’échelle du modèle par la même valeur dans les axes X, Y et Z, pour modifier la taille du modèle proportionnellement. Par exemple, définir le <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> <xref:System.Windows.Media.ScaleTransform.ScaleY%2A>transformateur, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> et les propriétés à 0,5 moitiés de la taille du modèle; réglage des mêmes propriétés à 2 double son échelle dans les trois axes.  
  
 ![Uniform ScaleTransform3D](./media/threecubes-uniformscale-1.png "threecubes_uniformscale_1")  
Exemple de ScaleVector  
  
 En spécifiant une transformation d’échelle non uniforme, une transformation d’échelle dont les valeurs X, Y et Z ne sont pas toutes les mêmes, vous pouvez provoquer l’étirement ou la contraction d’un modèle dans une ou deux dimensions sans affecter les autres. Par exemple, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> le réglage <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> à 1, à 2, et <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> à 1 ferait doubler le modèle transformé en hauteur, mais rester inchangé le long des axes X et Z.  
  
 Par défaut, ScaleTransform3D étire ou contracte les sommets par rapport à l’origine (0,0,0). Si le modèle que vous souhaitez transformer n’est pas dessiné depuis l’origine, cependant, la mise à l’échelle du modèle à partir de l’origine ne fait pas évoluer le modèle « sur place. » Au lieu de cela, lorsque les sommets du modèle sont multipliés par le vecteur d’échelle, l’opération de mise à l’échelle a pour effet de déplacer le modèle en plus de le mettre à l’échelle.  
  
 ![Trois cubes mis à l'échelle avec point central spécifié](./media/threecubes-scaledwithcenter-1.png "threecubes_scaledwithcenter_1")  
Exemple de centre de mise à l’échelle  
  
 Pour mettre à l’échelle un modèle « en place », spécifiez le centre du modèle en définissant les propriétés de <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>l’ScaleTransform3D et. <xref:System.Windows.Media.Media3D.ScaleTransform3D.CenterZ%2A> Cela garantit que le système graphique échelles de l’espace modèle, <xref:System.Windows.Media.Media3D.Point3D>puis le traduit au centre sur le spécifié . À l’inverse, si vous avez généré le modèle par rapport à l’origine et que vous spécifiez un autre point, attendez-vous à ce que le modèle transformé soit déplacé par rapport à l’origine.  
  
## <a name="rotation-transformations"></a>Transformations de rotation  
 Vous pouvez faire pivoter un modèle en 3D de plusieurs façons différentes. Une rotation classique spécifie un axe et un angle de rotation autour de cet axe. La <xref:System.Windows.Media.Media3D.RotateTransform3D> classe vous permet <xref:System.Windows.Media.Media3D.Rotation3D> de <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> définir un avec sa propriété. Vous spécifiez <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> ensuite et <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> les propriétés sur la Rotation3D, dans ce cas un <xref:System.Windows.Media.Media3D.AxisAngleRotation3D>, pour définir la transformation. Les exemples suivants font pivoter un modèle de 60 degrés autour de l’axe Y.  
  
 [!code-xaml[animation3dgallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
 Remarque[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] : la 3D est un système droitier, ce qui signifie qu’une valeur d’angle positive pour une rotation entraîne une rotation dans le sens inverse des aiguilles d’une montre sur l’axe.  
  
 Les rotations d’angle d’axe supposent la <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterX%2A>rotation <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterY%2A>au <xref:System.Windows.Media.Media3D.RotateTransform3D.CenterZ%2A> sujet de l’origine si une valeur n’est pas spécifiée pour le , , et les propriétés sur RotateTransform3D. Comme avec la mise à l’échelle, il est utile de garder l’esprit que la rotation transforme l’espace de coordonnées entier du modèle. Si le modèle n’a pas été créé par rapport à l’origine ou a été déplacé précédemment, la rotation peut « pivoter » autour de l’origine au lieu de tourner sur place.  
  
 ![Rotation avec nouveau point central](./media/threecubes-rotationwithcenter-1.png "threecubes_rotationwithcenter_1")  
Rotation avec nouveau centre spécifié  
  
 Pour faire pivoter le modèle « sur place », spécifiez le centre réel du modèle en tant que centre de la rotation. Étant donné que la géométrie est généralement modelée par rapport à l’origine, vous pouvez généralement obtenir le résultat attendu d’un ensemble de transformations en redimensionnant d’abord le modèle (par mise à l’échelle), puis en définissant son orientation (par rotation) et enfin en le déplaçant vers l’emplacement souhaité (par translation).  
  
 ![Rotation de 60 degrés dans les axes x&#45; et y&#45;](./media/twocubes-rotation2axes-1.png "twocubes_rotation2axes_1")  
Exemple de rotation  
  
 Les rotations axe/angle fonctionnent bien pour les transformations statiques et certaines animations. Toutefois, envisagez la rotation d’un modèle de cube à 60 degrés autour de l’axe X, puis de 45 degrés autour de l’axe Z. Vous pouvez décrire cette transformation sous forme de deux transformations affines discrètes ou de matrice. Toutefois, il peut être difficile d’animer une rotation définie de cette façon. Même si les positions de début et de fin du modèle calculées par les deux approches sont les mêmes, les positions intermédiaires prises par le modèle sont incertaines en matière de calcul. Les quaternions représentent une autre façon de calculer l’interpolation entre le début et la fin d’une rotation.  
  
 Une quaternion représente un axe dans l’espace 3D et une rotation autour de cet axe. Par exemple, un quaternion peut représenter un axe (1,1,2) et une rotation de 50 degrés. La capacité des quaternions à définir des rotations vient des opérations que vous pouvez effectuer dessus : composition et interpolation. La composition de deux quaternions appliqués à une géométrie signifie « faire pivoter la géométrie autour de l’axe2 par la rotation2, puis la faire pivoter autour de l’axe1 par la rotation1 ». En utilisant la composition, vous pouvez combiner les deux rotations sur la géométrie pour obtenir un seul quaternion qui représente le résultat. Étant donné que l’interpolation de quaternion peut calculer un chemin fluide et raisonnable d’un axe et d’une orientation à l’autre, vous pouvez interpoler de du quaternion d’origine vers le quaternion composé pour effectuer une transition en douceur d’un autre à l’autre, ce qui vous permet d’animer la transformation. Pour les modèles que vous souhaitez animer, <xref:System.Windows.Media.Media3D.Quaternion> vous pouvez spécifier une destination pour la rotation en utilisant un <xref:System.Windows.Media.Media3D.QuaternionRotation3D> pour la <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> propriété.  
  
## <a name="using-transformation-collections"></a>Utilisation des collections de transformations  
 Lorsque vous générez une scène, il est courant d’appliquer plusieurs transformations à un modèle. Ajouter des transformations à la <xref:System.Windows.Media.Media3D.Transform3DGroup.Children%2A> collection de la <xref:System.Windows.Media.Media3D.Transform3DGroup> classe pour regrouper les transformations commodément pour s’appliquer à différents modèles de la scène. Il est souvent utile de réutiliser une transformation dans plusieurs groupes, de la même façon que vous pouvez réutiliser un modèle en appliquant un ensemble de transformations différent à chaque instance. Notez que l’ordre dans lequel les transformations sont ajoutées à la collection est important : les transformations de la collection sont appliquées de la première à la dernière.  
  
## <a name="animating-transformations"></a>Animation de transformations  
 La [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] mise en œuvre 3D participe au même système de synchronisation et d’animation que les graphismes 2D. En d’autres termes, pour animer une scène 3D, animer les propriétés de ses modèles. Il est possible d’animer directement des propriétés de primitives, mais il est généralement plus facile d’animer des transformations qui modifient la position ou l’apparence de modèles. Parce que les transformations peuvent être appliquées aux <xref:System.Windows.Media.Media3D.Model3DGroup> objets ainsi qu’aux modèles individuels, il est possible d’appliquer un ensemble d’animations aux enfants d’un Model3Dgroup et un autre ensemble d’animations à un groupe d’objets.  Pour plus d’informations sur le minutage [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et le système d’animation, consultez [Vue d'ensemble de l'animation](animation-overview.md) et [Vue d'ensemble des storyboards](storyboards-overview.md).  
  
 Pour animer un objet dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], créez une chronologie, définissez une animation (qui est en fait une modification de valeur de propriété dans le temps) et spécifiez la propriété à laquelle appliquer l’animation. Cette propriété doit être une propriété d’un FrameworkElement. Parce que tous les objets d’une scène 3D sont des enfants de Viewport3D, les propriétés ciblées par toute animation que vous souhaitez appliquer à la scène sont des propriétés de Viewport3D. Il est important de déterminer le chemin d’accès de la propriété vers l’animation avec précaution, car la syntaxe peut être complexe.  
  
 Supposons que vous souhaitez faire pivoter un objet sur place, mais aussi appliquer un mouvement oscillant pour exposer une plus grande partie de l’objet à afficher. Vous pouvez choisir d’appliquer une RotateTransform3D.RotateTransform3D au modèle et animer son axe de rotation d’un vecteur à un autre. L’exemple de code <xref:System.Windows.Media.Animation.Vector3DAnimation> suivant montre l’application d’une propriété à l’Axe de la rotation3D de la transformation, <xref:System.Windows.Media.TransformGroup>en supposant que le RotateTransform3D soit l’une des nombreuses transformations appliquées au modèle avec un .  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 Utilisez une syntaxe similaire pour cibler d’autres propriétés de transformation pour déplacer ou redimensionner l’objet.  Par exemple, vous <xref:System.Windows.Media.Animation.Point3DAnimation> pouvez appliquer un à la propriété ScaleCenter sur une transformation échelle pour provoquer un modèle de déformer en douceur sa forme.  
  
 Bien que les exemples <xref:System.Windows.Media.Media3D.GeometryModel3D>précédents transforment les propriétés de , il est également possible de transformer les propriétés d’autres modèles dans la scène.  En animant des translations appliquées aux objets Light, par exemple, vous pouvez créer des effets de lumière et d’ombre qui peuvent modifier considérablement l’apparence de vos modèles.  
  
 Étant donné que les caméras sont également des modèles, il est aussi possible de transformer les propriétés de la caméra.  Même si vous pouvez tout à fait modifier l’apparence de la scène en transformant les distances sur le plan de la position de la caméra (en transformant ainsi la projection de scène entière), notez que beaucoup d’effets que vous obtenez de cette façon peuvent ne pas paraître aussi « visuellement cohérents » que les transformations appliquées à l’emplacement ou la position des modèles dans la scène.  
  
## <a name="see-also"></a>Voir aussi

- [Aperçu graphique 3D](3-d-graphics-overview.md)
- [Vue d'ensemble des transformations](transforms-overview.md)
- [2D transforme l’échantillon](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
