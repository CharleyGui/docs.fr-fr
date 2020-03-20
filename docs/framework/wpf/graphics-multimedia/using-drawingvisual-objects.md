---
title: Utilisation d'objets DrawingVisual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
ms.openlocfilehash: 9d67fbc0d9716c9df3935232c6c7e579b50d55bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148320"
---
# <a name="using-drawingvisual-objects"></a>Utilisation d'objets DrawingVisual
Ce sujet donne un aperçu <xref:System.Windows.Media.DrawingVisual> de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] la façon d’utiliser des objets dans la couche visuelle.  
  
<a name="drawingvisual_object"></a>
## <a name="drawingvisual-object"></a>Objet DrawingVisual  
 Il <xref:System.Windows.Media.DrawingVisual> s’agit d’une classe de dessin léger qui est utilisée pour rendre des formes, des images ou du texte. Cette classe est dite légère, car elle n’assure pas la gestion des dispositions ni des événements, ce qui améliore ses performances. C’est pourquoi, les dessins de ce type sont idéaux pour les arrière-plans et les images clipart.  
  
<a name="drawingvisual_host_container"></a>
## <a name="drawingvisual-host-container"></a>Conteneur hôte DrawingVisual  
 Afin d’utiliser des <xref:System.Windows.Media.DrawingVisual> objets, vous devez créer un conteneur d’hôte pour les objets. L’objet de conteneur <xref:System.Windows.FrameworkElement> hôte doit dériver de la classe, qui fournit le support de mise en page et de gestion d’événements qui manque à la <xref:System.Windows.Media.DrawingVisual> classe. L’objet de type conteneur hôte n’affiche pas de propriétés visibles, dans la mesure où son but principal est de contenir des objets enfants. Toutefois, <xref:System.Windows.UIElement.Visibility%2A> la propriété du conteneur hôte <xref:System.Windows.Visibility.Visible>doit être réglée à ; autrement, aucun de ses éléments enfant ne sera visible.  
  
 Lorsque vous créez un objet de conteneur d’hôte pour les <xref:System.Windows.Media.VisualCollection>objets visuels, vous devez stocker les références d’objets visuels dans un . Utilisez <xref:System.Windows.Media.VisualCollection.Add%2A> la méthode pour ajouter un objet visuel au conteneur hôte. Dans l’exemple suivant, un objet de conteneur d’hôte <xref:System.Windows.Media.VisualCollection>est créé, et trois objets visuels sont ajoutés à son .  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> Pour consulter l’intégralité de l’exemple de code duquel l’exemple de code précédent a été extrait, référez-vous à la section [Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual) (Test de positionnement à l’aide d’exemples de DrawingVisuals).  
  
<a name="creating_drawingvisual_objects"></a>
## <a name="creating-drawingvisual-objects"></a>Création d'objets DrawingVisual  
 Lorsque vous <xref:System.Windows.Media.DrawingVisual> créez un objet, il n’a pas de contenu de dessin. Vous pouvez ajouter du texte, des graphiques ou du <xref:System.Windows.Media.DrawingContext> contenu d’image en récupérant l’objet et en y attirant. A <xref:System.Windows.Media.DrawingContext> est retourné <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> en appelant <xref:System.Windows.Media.DrawingVisual> la méthode d’un objet.  
  
 Pour dessiner un <xref:System.Windows.Media.DrawingContext>rectangle dans <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> le <xref:System.Windows.Media.DrawingContext> , utilisez la méthode de l’objet. Il existe des méthodes similaires pour dessiner d’autres types de contenu. Lorsque vous avez fini <xref:System.Windows.Media.DrawingContext>de dessiner <xref:System.Windows.Media.DrawingContext.Close%2A> du contenu <xref:System.Windows.Media.DrawingContext> dans le , appelez la méthode pour fermer le et de persister le contenu.  
  
 Dans l’exemple <xref:System.Windows.Media.DrawingVisual> suivant, un objet est créé, <xref:System.Windows.Media.DrawingContext>et un rectangle est entraîné dans son .  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>
## <a name="creating-overrides-for-frameworkelement-members"></a>Création de remplacements pour les membres FrameworkElement  
 L’objet de type conteneur hôte est chargé de gérer sa collection d’objets visuels. Cela exige que le membre de mise <xref:System.Windows.FrameworkElement> en œuvre du conteneur hôte remplace la classe dérivée.  
  
 La liste suivante décrit les deux membres que vous devez substituer :  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Renvoie un enfant à l’index spécifié de la collection d’éléments pour enfants.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Obtient le nombre d’éléments visuels de l’enfant dans cet élément.  
  
 Dans l’exemple suivant, des <xref:System.Windows.FrameworkElement> dérogations pour les deux membres sont mises en œuvre.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>
## <a name="providing-hit-testing-support"></a>Prise en charge du test de positionnement  
 L’objet de conteneur hôte peut fournir la manipulation d’événement <xref:System.Windows.UIElement.Visibility%2A> même s’il n’affiche aucune propriété visible, cependant, sa propriété doit être réglée à <xref:System.Windows.Visibility.Visible>. Cela vous permet de créer une routine de gestion des événements pour le conteneur hôte, capable de détecter les événements de la souris, tels que le relâchement du bouton gauche de la souris. La routine de gestion de l’événement <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> peut ensuite mettre en œuvre des tests de frappe en invoquant la méthode. Le paramètre <xref:System.Windows.Media.HitTestResultCallback> de la méthode fait référence à une procédure définie par l’utilisateur que vous pouvez utiliser pour déterminer l’action résultante d’un test à succès.  
  
 Dans l’exemple suivant, la prise en charge du test de positionnement est implémentée pour l’objet de type conteneur hôte et ses enfants.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
- [Test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md)
