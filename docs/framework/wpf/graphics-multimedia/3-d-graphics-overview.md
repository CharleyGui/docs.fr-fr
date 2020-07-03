---
title: Vue d’ensemble des graphiques 3D
description: Familiarisez-vous avec les graphiques 3D dans Windows Presentation Foundation (WPF) pour dessiner, transformer et animer des graphiques 3D dans le balisage et le code procédural.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: 51da6a1ed6d5e98b99c64ee23be52f7b2385897f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853873"
---
# <a name="3d-graphics-overview"></a>Vue d’ensemble des graphiques 3D
<a name="introduction"></a>La fonctionnalité 3D dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permet aux développeurs de dessiner, transformer et animer des graphiques 3D dans le balisage et le code procédural. Les développeurs peuvent combiner des graphiques 2D et 3D pour créer des contrôles enrichis, fournir des illustrations complexes de données ou améliorer l’expérience utilisateur de l’interface d’une application. la prise en charge 3D dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n’est pas conçue pour fournir une plateforme de développement de jeux complète. Cette rubrique fournit une vue d’ensemble de la fonctionnalité 3D dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système graphique.  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>3D dans un conteneur 2D  
 le contenu graphique 3D dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est encapsulé dans un élément, <xref:System.Windows.Controls.Viewport3D> , qui peut participer à la structure d’élément à deux dimensions. Le système graphique traite <xref:System.Windows.Controls.Viewport3D> comme un élément visuel à deux dimensions comme de nombreux autres dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . <xref:System.Windows.Controls.Viewport3D>fonctionne comme une fenêtre, une fenêtre d’affichage, dans une scène en trois dimensions. Plus précisément, c’est une surface sur laquelle une scène 3D est projetée.  
  
 Dans une application 2D conventionnelle, utilisez <xref:System.Windows.Controls.Viewport3D> comme vous le feriez pour un autre élément de conteneur comme Grid ou Canvas.  Bien que vous puissiez utiliser <xref:System.Windows.Controls.Viewport3D> avec d’autres objets de dessin 2D dans le même graphique de scène, vous ne pouvez pas interpénétrer les objets 2D et 3D dans un <xref:System.Windows.Controls.Viewport3D> .  Cette rubrique se concentrera sur la façon de dessiner des graphiques 3D dans le <xref:System.Windows.Controls.Viewport3D> .  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>Espace de coordonnées 3D  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de coordonnées pour les graphiques 2D localise l’origine dans le coin supérieur gauche de la zone de rendu (en général l’écran). Dans le système 2D, les valeurs positives de l’axe des x continuent à droite et les valeurs positives de l’axe des y s’effectuent vers le bas.  Dans le système de coordonnées 3D, toutefois, l’origine se trouve au centre de la zone de rendu, avec les valeurs positives de l’axe des abscisses qui se poursuivent à droite mais les valeurs de l’axe des y positives continuent vers le haut, et les valeurs positives de l’axe z qui continuent vers l’extérieur de l’origine, vers la visionneuse.  
  
 ![Systèmes de coordonnées](./media/coordsystem-1.png "CoordSystem-1")  
Représentations conventionnelles des systèmes de coordonnées 2D et 3D  
  
 L’espace défini par ces axes est le cadre stationnaire de référence pour les objets 3D dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Lorsque vous générez des modèles dans cet espace et créez des lumières et des caméras pour les consulter, il est utile de distinguer ce frame stationnaire de référence, ou « espace universel » du frame local de référence que vous créez pour chaque modèle lorsque vous lui appliquez des transformations. N’oubliez également pas que les objets dans l’espace universel peuvent sembler entièrement différents, ou ne pas du tout être visibles, en fonction des paramètres de lumière et de caméra, mais que la position de la caméra ne modifie pas l’emplacement des objets dans l’espace universel.  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>Caméras et projections  
 Les développeurs qui travaillent en 2D sont habitués à positionner des primitives de dessin sur un écran à deux dimensions. Lorsque vous créez une scène 3D, il est important de se souvenir que vous créez véritablement une représentation 2D d’objets 3D. Comme une scène 3D présente un aspect différent selon le point de vue du spectateur, vous devez spécifier ce point de vue. La <xref:System.Windows.Media.Media3D.Camera> classe vous permet de spécifier ce point de vue pour une scène 3D.  
  
 Pour comprendre comment une scène 3D est représentée sur une surface 2D, vous pouvez également décrire la scène comme une projection sur la surface d’affichage. <xref:System.Windows.Media.Media3D.ProjectionCamera>Vous permet de spécifier différentes projections et leurs propriétés pour modifier la façon dont le spectateur voit les modèles 3D. Un <xref:System.Windows.Media.Media3D.PerspectiveCamera> spécifie une projection qui foreshortens la scène.  En d’autres termes, le <xref:System.Windows.Media.Media3D.PerspectiveCamera> fournit une perspective de point de fuite.  Vous pouvez spécifier la position de la caméra dans l’espace de coordonnées de la scène, la direction et le champ de vue pour la caméra, et un vecteur qui définit le sens de « haut » dans la scène. Le diagramme suivant illustre la <xref:System.Windows.Media.Media3D.PerspectiveCamera> projection de.  
  
 Les <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> Propriétés et de <xref:System.Windows.Media.Media3D.ProjectionCamera> limitent la plage de la projection de la caméra. Étant donné que les caméras peuvent se trouver n’importe où dans la scène, il est possible de placer la caméra à l’intérieur d’un modèle ou très près d’un modèle, ce qui fait qu’il est difficile de bien distinguer les objets.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>vous permet de spécifier une distance minimale de l’appareil photo au-delà de laquelle les objets ne seront pas dessinés.  À l’inverse, <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> vous permet de spécifier une distance à partir de la caméra au-delà de laquelle les objets ne seront pas dessinés, ce qui garantit que les objets trop éloignés pour être reconnaissables ne seront pas inclus dans la scène.  
  
 ![Installation de l'appareil photo](./media/coordsystem-6.png "CoordSystem-6")  
Position d'une caméra  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>spécifie une projection orthogonale d’un modèle 3D sur une surface visuelle 2D. Comme les autres caméras, elle spécifie une position, la direction d’affichage et la direction « vers le haut ». Toutefois, contrairement <xref:System.Windows.Media.Media3D.PerspectiveCamera> <xref:System.Windows.Media.Media3D.OrthographicCamera> à, décrit une projection qui n’inclut pas la réduction de perspective. En d’autres termes, <xref:System.Windows.Media.Media3D.OrthographicCamera> décrit une zone d’affichage dont les côtés sont parallèles, au lieu d’une zone dont les côtés se remplissent à un point de l’appareil photo. L’illustration suivante montre le même modèle que celui affiché à l’aide <xref:System.Windows.Media.Media3D.PerspectiveCamera> de et <xref:System.Windows.Media.Media3D.OrthographicCamera> .  
  
 ![Projection orthographique et en perspective](./media/camera-projections4.png "Camera_projections4")  
Projections en perspective et orthographiques  
  
 Le code suivant montre des paramètres de caméra typiques.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>Modèle et primitives de maillage  
  
 <xref:System.Windows.Media.Media3D.Model3D>est la classe de base abstraite qui représente un objet 3D générique. Pour générer une scène 3D, vous avez besoin de certains objets à afficher, et les objets qui composent le graphique de scène dérivent de <xref:System.Windows.Media.Media3D.Model3D> . Actuellement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge les géométries de modélisation avec <xref:System.Windows.Media.Media3D.GeometryModel3D> . La <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> propriété de ce modèle prend une primitive de maillage.  
  
 Pour générer un modèle, commencez par créer une primitive, ou maillage. Une primitive 3D est une collection de vertex qui forment une seule entité 3D. La plupart des systèmes 3D fournissent des primitives modélisées sur la figure fermée la plus simple : un triangle défini par trois vertex.  Les trois points d’un triangle étant coplanaires, vous pouvez continuer à ajouter des triangles pour modeler des formes complexes, appelées mailles.  
  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système 3D fournit actuellement la <xref:System.Windows.Media.Media3D.MeshGeometry3D> classe, qui vous permet de spécifier une géométrie. elle ne prend pas actuellement en charge les primitives 3D prédéfinies comme les formes sphère et cubique. Commencez à créer un <xref:System.Windows.Media.Media3D.MeshGeometry3D> en spécifiant une liste de sommets triangulaires comme <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> propriété. Chaque vertex est spécifié en tant que <xref:System.Windows.Media.Media3D.Point3D> .  (Dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , spécifiez cette propriété comme une liste de nombres regroupés en trois qui représentent les coordonnées de chaque vertex.) En fonction de sa géométrie, votre maille peut être composée de plusieurs triangles, certains d’entre eux partageant les mêmes angles (sommets). Pour dessiner le maillage correctement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a besoin d’informations sur les sommets qui sont partagés par les triangles respectifs. Vous fournissez ces informations en spécifiant une liste d’indices de triangle avec la <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> propriété. Cette liste spécifie l’ordre dans lequel les points spécifiés dans la <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste déterminent un triangle.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 Dans l’exemple précédent, la <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste spécifie huit sommets pour définir un maillage en forme de cube. La <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> propriété spécifie une liste de douze groupes de trois index.  Chaque nombre de la liste fait référence à un décalage dans la <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste.  Par exemple, les trois premiers sommets spécifiés par la <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste sont (1, 1, 0), (0, 1, 0) et (0, 0, 0). Les trois premiers index spécifiés par la <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> liste sont 0, 2 et 1, ce qui correspond aux premier, troisième et deuxième points de la <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste. Par conséquent, le premier triangle qui compose le modèle de cube sera composé de (1,1,0) à (0,1,0) à (0,0,0), et les onze triangles restants seront déterminés de la même façon.  
  
 Vous pouvez continuer à définir le modèle en spécifiant des valeurs pour les <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> Propriétés et.  Pour restituer la surface du modèle, le système graphique a besoin d’informations sur la direction à laquelle la surface fait face sur tout triangle donné. Il utilise ces informations pour effectuer des calculs d’éclairage pour le modèle : les surfaces qui font face directement à une source de lumière apparaissent plus claires que celles inclinées par rapport à la lumière. Même si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut déterminer les vecteurs normaux par défaut en utilisant les coordonnées de position, vous pouvez également spécifier différents vecteurs normaux pour reproduire approximativement l’apparence des surfaces courbes.  
  
 La <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> propriété spécifie une collection de <xref:System.Windows.Point> s qui indiquent au système graphique comment mapper les coordonnées qui déterminent la façon dont une texture est dessinée sur les vertex de la maille. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>sont spécifiés sous la forme d’une valeur comprise entre 0 et 1 inclus.  Comme avec la <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> propriété, le système graphique peut calculer des coordonnées de texture par défaut, mais vous pouvez choisir de définir des coordonnées de texture différentes pour contrôler le mappage d’une texture qui comprend une partie d’un modèle répétitif, par exemple. Vous trouverez plus d’informations sur les coordonnées de texture dans les rubriques suivantes, ou dans le kit de développement managé Direct3D.  
  
 L’exemple suivant montre comment créer une face du modèle de cube en code procédural. Vous pouvez dessiner le cube entier comme un GeometryModel3D unique ; Cet exemple dessine le visage du cube en tant que modèle distinct afin d’appliquer des textures distinctes à chaque visage ultérieurement.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>Application de matériaux au modèle  
  
 Pour qu’une maille ressemble à un objet en trois dimensions, elle doit avoir une texture appliquée pour couvrir la surface définie par ses sommets et triangles afin de pouvoir être éclairée et projetée par la caméra. En 2D, vous utilisez la <xref:System.Windows.Media.Brush> classe pour appliquer des couleurs, des modèles, des dégradés ou d’autres contenus visuels à des zones de l’écran.  Toutefois, l’apparence des objets 3D est une fonction du modèle d’éclairage, pas seulement de la couleur ou du motif qui leur est appliqué. Les objets réels reflètent différemment la lumière selon la qualité de leurs surfaces : les surfaces brillantes ne semblent pas si rugueuses que les surfaces mates, et certains objets semblent absorber la lumière alors que d’autres brillent. Vous pouvez appliquer les mêmes pinceaux aux objets 3D que vous pouvez appliquer aux objets 2D, mais vous ne pouvez pas les appliquer directement.  
  
 Pour définir les caractéristiques de la surface d’un modèle, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise la <xref:System.Windows.Media.Media3D.Material> classe abstraite. Les sous-classes concrètes de Material déterminent certaines des caractéristiques d’apparence de la surface du modèle, et chacune fournit également une propriété Brush à laquelle vous pouvez passer un SolidColorBrush, TileBrush ou VisualBrush.  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>Spécifie que le pinceau sera appliqué au modèle comme s’il s’agissait d’un modèle éclairé de manière diffuse. L’utilisation de DiffuseMaterial s’apparente le plus à l’utilisation de pinceaux directement sur les modèles 2D ; les surfaces de modèle ne reflètent pas la lumière comme si elle était brillante.  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>Spécifie que le pinceau sera appliqué au modèle comme si la surface du modèle était dure ou brillante, capable de refléter les surbrillances. Vous pouvez définir le degré auquel la texture suggèrera cette qualité réfléchissante, ou « brillant », en spécifiant une valeur pour la <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> propriété.  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>vous permet de spécifier que la texture sera appliquée comme si le modèle produisait une lumière égale à la couleur du pinceau. Cela ne fait pas du modèle un éclairage. Toutefois, il participera différemment à l’ombrage que s’il était texturé avec DiffuseMaterial ou SpecularMaterial.  
  
 Pour de meilleures performances, les faces <xref:System.Windows.Media.Media3D.GeometryModel3D> arrières d’un (les faces qui sont hors de la vue, car elles sont sur le côté opposé du modèle de l’appareil photo) sont éliminées de la scène.  Pour spécifier un <xref:System.Windows.Media.Media3D.Material> à appliquer à la face arrière d’un modèle comme un plan, définissez la propriété du modèle <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> .  
  
 Pour obtenir certaines qualités de surface, comme les effets lumineux ou de miroir, vous souhaiterez appliquer plusieurs pinceaux différents à un modèle à la suite. Vous pouvez appliquer et réutiliser plusieurs documents à l’aide de la <xref:System.Windows.Media.Media3D.MaterialGroup> classe. Les enfants du MaterialGroup sont appliqués du premier au dernier en plusieurs passes de rendu.  
  
 Les exemples de code suivants montrent comment appliquer une couleur unie et un dessin en tant que pinceaux à des modèles 3D.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>Éclairage de la scène  
 Les lumières dans les graphiques 3D font les lumières dans le monde réel : elles rendent les surfaces visibles. Plus précisément, les lumières déterminent la partie d’une scène qui figurera dans la projection. Les objets de lumière dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] créent divers effets de lumière et d’ombre et sont modelés d’après le comportement de diverses lumières réelles. Incluez au moins une lumière dans votre scène, ou aucun modèle ne sera visible.  
  
 Les lumières suivantes dérivent de la classe de base <xref:System.Windows.Media.Media3D.Light> :  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: Fournit un éclairage ambiant qui éclaire tous les objets uniformément, quel que soit leur emplacement ou leur orientation.  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: Éclaire comme une source de lumière distante.  Les lumières directionnelles ont un <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> spécifié en tant qu’Vector3D, mais aucun emplacement spécifié.  
  
- <xref:System.Windows.Media.Media3D.PointLight>: Éclaire comme une source de lumière proche. Les PointLights ont une position et convertissent la lumière à partir de cette position. Les objets dans la scène sont éclairés en fonction de leur position et de la distance par rapport à la lumière. <xref:System.Windows.Media.Media3D.PointLightBase>expose une <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> propriété, qui détermine une distance au-delà de laquelle les modèles ne seront pas éclairés par la lumière. PointLight expose également des propriétés d’atténuation, qui déterminent la façon dont l’intensité de la lumière diminue sur la distance. Vous pouvez spécifier des interpolations constantes, linéaires ou quadratiques pour l’atténuation de la lumière.  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: Hérite de <xref:System.Windows.Media.Media3D.PointLight> . Les Spotlights éclairent comme PointLight et ont une position et une direction. Ils projetent la lumière dans une zone conique définie par <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> les <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> Propriétés et, spécifiées en degrés.  
  
 Les lumières étant des <xref:System.Windows.Media.Media3D.Model3D> objets, vous pouvez transformer et animer des propriétés de lumière, notamment la position, la couleur, la direction et la plage.  
  
 [!code-xaml[hittest3d#HitTest3D3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml#hittest3d3dn6)]  
  
 [!code-csharp[basic3d#Basic3D3DN11](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn11)]
 [!code-vb[basic3d#Basic3D3DN11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn11)]  
  
 [!code-csharp[basic3d#Basic3D3DN12](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn12)]
 [!code-vb[basic3d#Basic3D3DN12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn12)]  
  
 [!code-csharp[basic3d#Basic3D3DN13](~/samples/snippets/csharp/VS_Snippets_Wpf/Basic3D/CSharp/Window1.xaml.cs#basic3d3dn13)]
 [!code-vb[basic3d#Basic3D3DN13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Basic3D/visualbasic/window1.xaml.vb#basic3d3dn13)]  
  
<a name="transforms"></a>
## <a name="transforming-models"></a>Transformation de modèles  
 Lorsque vous créez des modèles, ils ont un emplacement particulier dans la scène. Pour déplacer ces modèles dans la scène, pour les faire pivoter ou pour modifier leur taille, il n’est pas pratique de modifier les vertex qui définissent les modèles eux-mêmes.  Au lieu de cela, tout comme en 2D, vous appliquez des transformations aux modèles.  
  
 Chaque objet de modèle a une <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> propriété qui vous permet de déplacer, de réorienter ou de redimensionner le modèle.  Lorsque vous appliquez une transformation, vous décalez tous les points du modèle par le vecteur ou la valeur que la transformation spécifie. En d’autres termes, vous avez transformé l’espace de coordonnées dans lequel le modèle est défini (« espace de modèle »), mais vous n’avez pas modifié les valeurs qui composent la géométrie du modèle dans le système de coordonnées de la scène entière (« espace universel »).  
  
 Pour plus d’informations sur la transformation des modèles, consultez [vue d’ensemble des transformations 3D](3-d-transformations-overview.md).  
  
<a name="animations"></a>
## <a name="animating-models"></a>Animation de modèles  
 L' [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implémentation 3D participe au même système de minutage et d’animation que les graphiques 2D. En d’autres termes, pour animer une scène 3D, animez les propriétés de ses modèles. Il est possible d’animer directement des propriétés de primitives, mais il est généralement plus facile d’animer des transformations qui modifient la position ou l’apparence de modèles. Étant donné que les transformations peuvent être appliquées aux <xref:System.Windows.Media.Media3D.Model3DGroup> objets, ainsi qu’à des modèles individuels, il est possible d’appliquer un ensemble d’animations à un enfant d’un Model3DGroup et un autre ensemble d’animations à un groupe d’objets enfants. Vous pouvez également obtenir divers effets visuels en animant les propriétés d’éclairage de votre scène. Enfin, vous pouvez choisir d’animer la projection elle-même en animant la position d’une caméra ou un champ de vue. Pour plus d’informations sur le minutage [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et le système d’animation, consultez les rubriques [Vue d'ensemble de l'animation](animation-overview.md), [Vue d'ensemble des storyboards](storyboards-overview.md) et [Vue d'ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
 Pour animer un objet dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous créez une chronologie, définissez une animation (qui est en fait une modification de valeur de propriété dans le temps) et spécifiez la propriété à laquelle appliquer l’animation. Étant donné que tous les objets d’une scène 3D sont des enfants de <xref:System.Windows.Controls.Viewport3D> , les propriétés ciblées par une animation que vous souhaitez appliquer à la scène sont des propriétés de Viewport3D.  
  
 Supposons que vous souhaitez faire osciller un modèle. Vous pouvez choisir d’appliquer un <xref:System.Windows.Media.Media3D.RotateTransform3D> au modèle et d’animer l’axe de sa rotation d’un vecteur à un autre. L’exemple de code suivant montre comment appliquer une Vector3DAnimation à la propriété Axis de la Rotation3D de la transformation, en supposant que RotateTransform3D est une des multiples transformations appliquées au modèle avec un TransformGroup.  
  
 [!code-csharp[3doverview#3DOverview3DN1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn1)]
 [!code-vb[3doverview#3DOverview3DN1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn1)]  
  
 [!code-csharp[3doverview#3DOverview3DN3](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn3)]
 [!code-vb[3doverview#3DOverview3DN3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn3)]  
  
 [!code-csharp[3doverview#3DOverview3DN4](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn4)]
 [!code-vb[3doverview#3DOverview3DN4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn4)]  
  
 [!code-csharp[3doverview#3DOverview3DN5](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn5)]
 [!code-vb[3doverview#3DOverview3DN5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn5)]  
  
<a name="animations1"></a>
## <a name="add-3d-content-to-the-window"></a>Ajouter du contenu 3D à la fenêtre  
 Pour afficher la scène, ajoutez des modèles et des lumières à un <xref:System.Windows.Media.Media3D.Model3DGroup> , puis définissez <xref:System.Windows.Media.Media3D.Model3DGroup> en tant que <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> de <xref:System.Windows.Media.Media3D.ModelVisual3D> . Ajoutez le <xref:System.Windows.Media.Media3D.ModelVisual3D> à la <xref:System.Windows.Controls.Viewport3D.Children%2A> collection de <xref:System.Windows.Controls.Viewport3D> . Ajoutez des caméras au <xref:System.Windows.Controls.Viewport3D> en définissant sa <xref:System.Windows.Controls.Viewport3D.Camera%2A> propriété.  
  
 Enfin, ajoutez le <xref:System.Windows.Controls.Viewport3D> à la fenêtre. Lorsque le <xref:System.Windows.Controls.Viewport3D> est inclus en tant que contenu d’un élément de disposition comme Canvas, spécifiez la taille du Viewport3D en définissant ses <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> Propriétés et (héritée de <xref:System.Windows.FrameworkElement> ).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [Vue d’ensemble des transformations 3D](3-d-transformations-overview.md)
- [Optimiser les performances 3D de WPF](maximize-wpf-3d-performance.md)
- [Rubriques de procédures](3-d-graphics-how-to-topics.md)
- [Vue d'ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Peinture avec des objets d'image, de dessin et visuels](painting-with-images-drawings-and-visuals.md)
