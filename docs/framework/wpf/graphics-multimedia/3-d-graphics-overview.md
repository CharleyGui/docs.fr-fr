---
title: Aperçu graphique 3D
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 3D graphics [WPF]
- graphics [WPF], 3D
ms.assetid: 67f31ed4-e36b-4b02-9889-dcce245d7afc
ms.openlocfilehash: e4918f7737bbe57a4f29c6c5cff1099f4f21674b
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291819"
---
# <a name="3d-graphics-overview"></a>Aperçu graphique 3D
<a name="introduction"></a>La fonctionnalité 3D [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] permet aux développeurs de dessiner, transformer et animer les graphiques 3D dans le code de balisage et de procédure. Les développeurs peuvent combiner des graphiques 2D et 3D pour créer des contrôles riches, fournir des illustrations complexes de données ou améliorer l’expérience utilisateur de l’interface d’une application. Le support 3D n’est [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pas conçu pour fournir une plate-forme de développement de jeu en vedette. Ce sujet fournit un aperçu de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fonctionnalité 3D dans le système graphique.  

<a name="threed_in_2d"></a>
## <a name="3d-in-a-2d-container"></a>3D dans un conteneur 2D  
 Le contenu graphique 3D est [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] encapsulé <xref:System.Windows.Controls.Viewport3D>dans un élément, qui peut participer à la structure d’élément bidimensionnel. Le système graphique <xref:System.Windows.Controls.Viewport3D> traite comme un élément visuel bidimensionnel comme beaucoup d’autres dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Viewport3D>fonctionne comme une fenêtre, un point de vue, dans une scène tridimensionnelle. Plus précisément, il s’agit d’une surface sur laquelle une scène 3D est projetée.  
  
 Dans une application 2D <xref:System.Windows.Controls.Viewport3D> conventionnelle, utilisez comme vous le feriez un autre élément de conteneur comme Grid ou Canvas.  Bien que <xref:System.Windows.Controls.Viewport3D> vous puissiez utiliser avec d’autres objets de dessin 2D dans le même graphique <xref:System.Windows.Controls.Viewport3D>de scène, vous ne pouvez pas interpénétrer les objets 2D et 3D dans un .  Ce sujet se concentrera sur la façon <xref:System.Windows.Controls.Viewport3D>de dessiner des graphiques 3D à l’intérieur de la .  
  
<a name="coord_space"></a>
## <a name="3d-coordinate-space"></a>Espace de coordonnées 3D  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de coordonnées des graphiques 2D localise l’origine en haut à gauche de la zone de rendu (généralement l’écran). Dans le système 2D, les valeurs positives à axe x procèdent aux valeurs de l’axe y droite et positives se poursuivent.  Dans le système de coordonnées 3D, cependant, l’origine est située au centre de la zone de rendu, avec des valeurs positives à axe x allant vers la droite mais des valeurs positives de l’axe Y allant vers le haut à la place, et des valeurs positives z-axe allant vers l’extérieur de l’origine, vers le spectateur.  
  
 ![Systèmes de coordonnées](./media/coordsystem-1.png "CoordSystem-1")  
Représentations conventionnelles des systèmes de coordonnées 2D et 3D  
  
 L’espace défini par ces axes est le cadre de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]référence stationnaire pour les objets 3D dans . Lorsque vous générez des modèles dans cet espace et créez des lumières et des caméras pour les consulter, il est utile de distinguer ce frame stationnaire de référence, ou « espace universel » du frame local de référence que vous créez pour chaque modèle lorsque vous lui appliquez des transformations. N’oubliez également pas que les objets dans l’espace universel peuvent sembler entièrement différents, ou ne pas du tout être visibles, en fonction des paramètres de lumière et de caméra, mais que la position de la caméra ne modifie pas l’emplacement des objets dans l’espace universel.  
  
<a name="cameras"></a>
## <a name="cameras-and-projections"></a>Caméras et projections  
 Les développeurs qui travaillent en 2D sont habitués à positionner le dessin des primitifs sur un écran bidimensionnel. Lorsque vous créez une scène 3D, il est important de se rappeler que vous créez vraiment une représentation 2D d’objets 3D. Parce qu’une scène 3D semble différente selon le point de vue du spectateur, vous devez spécifier ce point de vue. La <xref:System.Windows.Media.Media3D.Camera> classe vous permet de spécifier ce point de vue pour une scène 3D.  
  
 Une autre façon de comprendre comment une scène 3D est représentée sur une surface 2D est de décrire la scène comme une projection sur la surface d’observation. Le <xref:System.Windows.Media.Media3D.ProjectionCamera> vous permet de spécifier différentes projections et leurs propriétés pour changer la façon dont le spectateur voit les modèles 3D. A <xref:System.Windows.Media.Media3D.PerspectiveCamera> spécifie une projection qui prévient la scène.  En d’autres <xref:System.Windows.Media.Media3D.PerspectiveCamera> termes, la perspective fournit des points de disparition.  Vous pouvez spécifier la position de la caméra dans l’espace de coordonnées de la scène, la direction et le champ de vue pour la caméra, et un vecteur qui définit le sens de « haut » dans la scène. Le diagramme suivant <xref:System.Windows.Media.Media3D.PerspectiveCamera>illustre la projection de '.  
  
 Les <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A> <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> propriétés <xref:System.Windows.Media.Media3D.ProjectionCamera> et les propriétés de limiter la portée de la projection de la caméra. Étant donné que les caméras peuvent se trouver n’importe où dans la scène, il est possible de placer la caméra à l’intérieur d’un modèle ou très près d’un modèle, ce qui fait qu’il est difficile de bien distinguer les objets.  <xref:System.Windows.Media.Media3D.ProjectionCamera.NearPlaneDistance%2A>vous permet de spécifier une distance minimale de la caméra au-delà de laquelle les objets ne seront pas dessinés.  Inversement, <xref:System.Windows.Media.Media3D.ProjectionCamera.FarPlaneDistance%2A> vous permet de spécifier une distance de la caméra au-delà de laquelle les objets ne seront pas tirés, ce qui garantit que les objets trop éloignés pour être reconnaissables ne seront pas inclus dans la scène.  
  
 ![Installation de l'appareil photo](./media/coordsystem-6.png "CoordSystem-6")  
Position d'une caméra  
  
 <xref:System.Windows.Media.Media3D.OrthographicCamera>spécifie une projection orthogonale d’un modèle 3D à une surface visuelle 2D. Comme les autres caméras, elle spécifie une position, la direction d’affichage et la direction « vers le haut ». Contrairement <xref:System.Windows.Media.Media3D.PerspectiveCamera>à <xref:System.Windows.Media.Media3D.OrthographicCamera> , cependant, décrit une projection qui n’inclut pas la perspective de raccourcir. En d’autres termes, <xref:System.Windows.Media.Media3D.OrthographicCamera> décrit une boîte de visualisation dont les côtés sont parallèles, au lieu d’un dont les côtés se rencontrent dans un point à la caméra. L’image suivante montre le <xref:System.Windows.Media.Media3D.PerspectiveCamera> même <xref:System.Windows.Media.Media3D.OrthographicCamera>modèle que vu à l’aide et .  
  
 ![Projection orthographique et en perspective](./media/camera-projections4.png "Camera_projections4")  
Projections en perspective et orthographiques  
  
 Le code suivant montre des paramètres de caméra typiques.  
  
 [!code-csharp[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexampleinline1)]
 [!code-vb[3dgallery_procedural_snip#Basic3DShapeCodeExampleInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexampleinline1)]  
  
<a name="models_meshes"></a>
## <a name="model-and-mesh-primitives"></a>Modèle et primitives de maillage  
  
 <xref:System.Windows.Media.Media3D.Model3D>est la classe de base abstraite qui représente un objet 3D générique. Pour construire une scène 3D, vous avez besoin de quelques objets à <xref:System.Windows.Media.Media3D.Model3D>voir, et les objets qui composent le graphique de scène dérivent de . Actuellement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les supports de modélisation <xref:System.Windows.Media.Media3D.GeometryModel3D>géométries avec . La <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> propriété de ce modèle prend un maillage primitif.  
  
 Pour générer un modèle, commencez par créer une primitive, ou maillage. Un primitif 3D est une collection de vertices qui forment une seule entité 3D. La plupart des systèmes 3D fournissent des primitifs calqués sur la figure fermée la plus simple : un triangle défini par trois vertices.  Les trois points d’un triangle étant coplanaires, vous pouvez continuer à ajouter des triangles pour modeler des formes complexes, appelées mailles.  
  
 Le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système 3D <xref:System.Windows.Media.Media3D.MeshGeometry3D> fournit actuellement la classe, ce qui vous permet de spécifier n’importe quelle géométrie; il ne prend actuellement pas en charge les primitifs 3D prédéfinis comme les sphères et les formes cubiques. Commencez à <xref:System.Windows.Media.Media3D.MeshGeometry3D> créer un en spécifiant <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> une liste de vertices triangle comme sa propriété. Chaque vertex est <xref:System.Windows.Media.Media3D.Point3D>spécifié comme un .  (En [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], spécifiez cette propriété comme une liste de nombres regroupés en trois qui représentent les coordonnées de chaque vertex.) Selon sa géométrie, votre maillage peut être composé de nombreux triangles, dont certains partagent les mêmes coins (vertices). Pour dessiner le maillage correctement, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a besoin d’informations sur les sommets qui sont partagés par les triangles respectifs. Vous fournissez ces informations en spécifiant une liste d’indices triangles avec la <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> propriété. Cette liste précise l’ordre dans lequel <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> les points spécifiés dans la liste détermineront un triangle.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN3](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn3)]  
  
 Dans l’exemple <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> précédent, la liste spécifie huit vertices pour définir un maillage en forme de cube. La <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> propriété spécifie une liste de douze groupes de trois indices.  Chaque numéro de la liste fait <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> référence à une compensation dans la liste.  Par exemple, les trois premiers vertices spécifiés par la <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> liste sont (1,1,0), (0,1,0) et (0,0,0). Les trois premiers indices <xref:System.Windows.Media.Media3D.MeshGeometry3D.TriangleIndices%2A> spécifiés par la liste sont 0, 2 et 1, <xref:System.Windows.Media.Media3D.MeshGeometry3D.Positions%2A> qui correspondent aux premier, troisième et deuxième points de la liste. Par conséquent, le premier triangle qui compose le modèle de cube sera composé de (1,1,0) à (0,1,0) à (0,0,0), et les onze triangles restants seront déterminés de la même façon.  
  
 Vous pouvez continuer à définir le <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> modèle <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> en spécifiant les valeurs et les propriétés.  Pour restituer la surface du modèle, le système graphique a besoin d’informations sur la direction à laquelle la surface fait face sur tout triangle donné. Il utilise ces informations pour effectuer des calculs d’éclairage pour le modèle : les surfaces qui font face directement à une source de lumière apparaissent plus claires que celles inclinées par rapport à la lumière. Même si [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut déterminer les vecteurs normaux par défaut en utilisant les coordonnées de position, vous pouvez également spécifier différents vecteurs normaux pour reproduire approximativement l’apparence des surfaces courbes.  
  
 La <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A> propriété spécifie une collection de <xref:System.Windows.Point>s qui indiquent au système graphique comment cartographier les coordonnées qui déterminent comment une texture est attirée par les vertices du maillage. <xref:System.Windows.Media.Media3D.MeshGeometry3D.TextureCoordinates%2A>sont spécifiés comme une valeur comprise entre zéro et 1, inclusivement.  Comme avec <xref:System.Windows.Media.Media3D.MeshGeometry3D.Normals%2A> la propriété, le système graphique peut calculer les coordonnées de texture par défaut, mais vous pouvez choisir de définir différentes coordonnées de texture pour contrôler la cartographie d’une texture qui comprend une partie d’un modèle répétitif, par exemple. Vous trouverez plus d’informations sur les coordonnées de texture dans les rubriques suivantes, ou dans le kit de développement managé Direct3D.  
  
 L’exemple suivant montre comment créer une face du modèle de cube en code procédural. Vous pouvez dessiner le cube entier comme un seul GeometryModel3D; cet exemple attire le visage du cube comme un modèle distinct afin d’appliquer des textures séparées à chaque visage plus tard.  
  
 [!code-csharp[3doverview#3DOverview3DN6](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn6)]
 [!code-vb[3doverview#3DOverview3DN6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn6)]  
  
 [!code-csharp[3doverview#3DOverview3DN7](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn7)]
 [!code-vb[3doverview#3DOverview3DN7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn7)]  
  
<a name="materials"></a>'
## <a name="applying-materials-to-the-model"></a>Application de matériaux au modèle  
  
 Pour qu’une maille ressemble à un objet en trois dimensions, elle doit avoir une texture appliquée pour couvrir la surface définie par ses sommets et triangles afin de pouvoir être éclairée et projetée par la caméra. En 2D, vous <xref:System.Windows.Media.Brush> utilisez la classe pour appliquer des couleurs, des motifs, des gradients ou d’autres contenus visuels sur les zones de l’écran.  L’apparition d’objets 3D, cependant, est une fonction du modèle d’éclairage, pas seulement de la couleur ou du motif appliqué à eux. Les objets réels reflètent différemment la lumière selon la qualité de leurs surfaces : les surfaces brillantes ne semblent pas si rugueuses que les surfaces mates, et certains objets semblent absorber la lumière alors que d’autres brillent. Vous pouvez appliquer tous les mêmes pinceaux sur les objets 3D que vous pouvez appliquer sur des objets 2D, mais vous ne pouvez pas les appliquer directement.  
  
 Pour définir les caractéristiques de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la <xref:System.Windows.Media.Media3D.Material> surface d’un modèle, utilise la classe abstraite. Les sous-classes concrètes de Material déterminent certaines des caractéristiques d’apparence de la surface du modèle, et chacune fournit également une propriété Brush à laquelle vous pouvez passer un SolidColorBrush, TileBrush ou VisualBrush.  
  
- <xref:System.Windows.Media.Media3D.DiffuseMaterial>précise que le pinceau sera appliqué au modèle comme si ce modèle avait été allumé de façon diffuse. L’utilisation de DiffuseMaterial ressemble le plus à l’utilisation de brosses directement sur des modèles 2D; les surfaces du modèle ne reflètent pas la lumière comme si elle était brillante.  
  
- <xref:System.Windows.Media.Media3D.SpecularMaterial>précise que le pinceau sera appliqué sur le modèle comme si la surface du modèle était dure ou brillante, capable de refléter les reflets. Vous pouvez définir la mesure dans laquelle la texture suggérera cette qualité réfléchissante, ou «brillance», en spécifiant une valeur pour la <xref:System.Windows.Media.Media3D.SpecularMaterial.SpecularPower%2A> propriété.  
  
- <xref:System.Windows.Media.Media3D.EmissiveMaterial>vous permet de spécifier que la texture sera appliquée comme si le modèle émettait de la lumière égale à la couleur de la brosse. Cela ne fait pas du modèle un éclairage. Toutefois, il participera différemment à l’ombrage que s’il était texturé avec DiffuseMaterial ou SpecularMaterial.  
  
 Pour de meilleures performances, les <xref:System.Windows.Media.Media3D.GeometryModel3D> backfaces d’un (ces visages qui sont hors de vue parce qu’ils sont de l’autre côté du modèle de la caméra) sont extraits de la scène.  Pour spécifier un <xref:System.Windows.Media.Media3D.Material> à appliquer à la face arrière <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> d’un modèle comme un plan, définissez la propriété du modèle.  
  
 Pour obtenir certaines qualités de surface, comme les effets lumineux ou de miroir, vous souhaiterez appliquer plusieurs pinceaux différents à un modèle à la suite. Vous pouvez appliquer et réutiliser plusieurs matériaux en utilisant la <xref:System.Windows.Media.Media3D.MaterialGroup> classe. Les enfants du MaterialGroup sont appliqués du premier au dernier en plusieurs passes de rendu.  
  
 Les exemples de code suivants montrent comment appliquer une couleur solide et un dessin comme brosses sur des modèles 3D.  
  
 [!code-xaml[basic3d#Basic3DXAML3DN5](~/samples/snippets/xaml/VS_Snippets_Wpf/Basic3D/XAML/Window1.xaml#basic3dxaml3dn5)]  
  ' [!code-xaml[3doverview#3DOverview3DN9](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/app.xaml#3doverview3dn9)]  
 ' [!code-csharp[3doverview#3DOverview3DN8](~/samples/snippets/csharp/VS_Snippets_Wpf/3DOverview/CSharp/Window1.xaml.cs#3doverview3dn8)]
  [!code-vb[3doverview#3DOverview3DN8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DOverview/visualbasic/window1.xaml.vb#3doverview3dn8)]  
  
<a name="lights"></a>
## <a name="illuminating-the-scene"></a>Éclairage de la scène  
 Les lumières dans les graphiques 3D font ce que les lumières font dans le monde réel : elles rendent les surfaces visibles. Plus précisément, les lumières déterminent la partie d’une scène qui figurera dans la projection. Les objets de lumière dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] créent divers effets de lumière et d’ombre et sont modelés d’après le comportement de diverses lumières réelles. Inclure au moins une lumière dans votre scène, ou aucun modèle ne sera visible.  
  
 Les lumières suivantes dérivent <xref:System.Windows.Media.Media3D.Light>de la classe de base :  
  
- <xref:System.Windows.Media.Media3D.AmbientLight>: Fournit un éclairage ambiant qui illumine tous les objets uniformément, quel que soit leur emplacement ou leur orientation.  
  
- <xref:System.Windows.Media.Media3D.DirectionalLight>: S’illumine comme une source de lumière lointaine.  Les lumières directionnelles ont un <xref:System.Windows.Media.Media3D.DirectionalLight.Direction%2A> spécifié comme un Vector3D, mais aucun emplacement spécifié.  
  
- <xref:System.Windows.Media.Media3D.PointLight>: S’illumine comme une source lumineuse à proximité. Les PointLights ont une position et convertissent la lumière à partir de cette position. Les objets dans la scène sont éclairés en fonction de leur position et de la distance par rapport à la lumière. <xref:System.Windows.Media.Media3D.PointLightBase>expose une <xref:System.Windows.Media.Media3D.PointLightBase.Range%2A> propriété, qui détermine une distance au-delà de laquelle les modèles ne seront pas éclairés par la lumière. PointLight expose également les propriétés d’atténuation, qui déterminent comment l’intensité de la lumière diminue sur la distance. Vous pouvez spécifier des interpolations constantes, linéaires ou quadratiques pour l’atténuation de la lumière.  
  
- <xref:System.Windows.Media.Media3D.SpotLight>: Hérite <xref:System.Windows.Media.Media3D.PointLight>de . Les Spotlights éclairent comme PointLight et ont une position et une direction. Ils projettent la lumière dans une <xref:System.Windows.Media.Media3D.SpotLight.InnerConeAngle%2A> zone <xref:System.Windows.Media.Media3D.SpotLight.OuterConeAngle%2A> en forme de cône définie par et des propriétés, spécifiées en degrés.  
  
 Les <xref:System.Windows.Media.Media3D.Model3D> lumières sont des objets, de sorte que vous pouvez transformer et animer les propriétés lumineuses, y compris la position, la couleur, la direction et la portée.  
  
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
  
 Chaque objet modèle <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> a une propriété avec laquelle vous pouvez déplacer, réorienter ou resize le modèle.  Lorsque vous appliquez une transformation, vous décalez tous les points du modèle par le vecteur ou la valeur que la transformation spécifie. En d’autres termes, vous avez transformé l’espace de coordonnées dans lequel le modèle est défini (« espace de modèle »), mais vous n’avez pas modifié les valeurs qui composent la géométrie du modèle dans le système de coordonnées de la scène entière (« espace universel »).  
  
 Pour plus d’informations sur la transformation des modèles, voir [3D Transformations Aperçu](3-d-transformations-overview.md).  
  
<a name="animations"></a>
## <a name="animating-models"></a>Animation de modèles  
 La [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mise en œuvre 3D participe au même système de synchronisation et d’animation que les graphismes 2D. En d’autres termes, pour animer une scène 3D, animer les propriétés de ses modèles. Il est possible d’animer directement des propriétés de primitives, mais il est généralement plus facile d’animer des transformations qui modifient la position ou l’apparence de modèles. Parce que les transformations peuvent être appliquées aux <xref:System.Windows.Media.Media3D.Model3DGroup> objets ainsi qu’à des modèles individuels, il est possible d’appliquer un ensemble d’animations à un enfant d’un Model3DGroup et un autre ensemble d’animations à un groupe d’objets pour enfants. Vous pouvez également obtenir divers effets visuels en animant les propriétés d’éclairage de votre scène. Enfin, vous pouvez choisir d’animer la projection elle-même en animant la position d’une caméra ou un champ de vue. Pour plus d’informations sur le minutage [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et le système d’animation, consultez les rubriques [Vue d'ensemble de l'animation](animation-overview.md), [Vue d'ensemble des storyboards](storyboards-overview.md) et [Vue d'ensemble des objets Freezable](../advanced/freezable-objects-overview.md).  
  
 Pour animer un objet dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous créez une chronologie, définissez une animation (qui est en fait une modification de valeur de propriété dans le temps) et spécifiez la propriété à laquelle appliquer l’animation. Parce que tous les objets d’une <xref:System.Windows.Controls.Viewport3D>scène 3D sont des enfants de , les propriétés ciblées par toute animation que vous souhaitez appliquer à la scène sont des propriétés de Viewport3D.  
  
 Supposons que vous souhaitez faire osciller un modèle. Vous pouvez choisir <xref:System.Windows.Media.Media3D.RotateTransform3D> d’appliquer un sur le modèle, et d’animer l’axe de sa rotation d’un vecteur à l’autre. L’exemple de code suivant montre comment appliquer une Vector3DAnimation à la propriété Axis de la Rotation3D de la transformation, en supposant que RotateTransform3D est une des multiples transformations appliquées au modèle avec un TransformGroup.  
  
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
 Pour rendre la scène, ajouter <xref:System.Windows.Media.Media3D.Model3DGroup>des modèles <xref:System.Windows.Media.Media3D.Model3DGroup> et <xref:System.Windows.Media.Media3D.ModelVisual3D.Content%2A> des <xref:System.Windows.Media.Media3D.ModelVisual3D>lumières à un , puis définir le comme le d’un . Ajouter <xref:System.Windows.Media.Media3D.ModelVisual3D> la <xref:System.Windows.Controls.Viewport3D.Children%2A> collection de <xref:System.Windows.Controls.Viewport3D>la . Ajoutez des <xref:System.Windows.Controls.Viewport3D> caméras au <xref:System.Windows.Controls.Viewport3D.Camera%2A> réglage de sa propriété.  
  
 Enfin, ajoutez <xref:System.Windows.Controls.Viewport3D> la fenêtre. Lorsque <xref:System.Windows.Controls.Viewport3D> le contenu d’un élément de mise en page comme Canvas est <xref:System.Windows.FrameworkElement.Height%2A> inclus, spécifiez la taille du Viewport3D en définissant son et <xref:System.Windows.FrameworkElement.Width%2A> ses propriétés (héritées de <xref:System.Windows.FrameworkElement>).  
  
 [!code-xaml[hostingwpfusercontrolinwf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWpfUserControlInWf/CSharp/HostingWpfUserControlInWf/ConeControl.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Viewport3D>
- <xref:System.Windows.Media.Media3D.PerspectiveCamera>
- <xref:System.Windows.Media.Media3D.DirectionalLight>
- <xref:System.Windows.Media.Media3D.Material>
- [Aperçu des transformations 3D](3-d-transformations-overview.md)
- [Optimiser les performances 3D de WPF](maximize-wpf-3d-performance.md)
- [Sujets comment se passer](3-d-graphics-how-to-topics.md)
- [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
