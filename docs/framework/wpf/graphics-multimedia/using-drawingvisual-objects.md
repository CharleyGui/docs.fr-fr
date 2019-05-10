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
ms.openlocfilehash: a0ce66e8956c8d7f1da1152f193f651ed1a54e3b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623569"
---
# <a name="using-drawingvisual-objects"></a>Utilisation d'objets DrawingVisual
Cette rubrique fournit une vue d’ensemble de l’utilisation de <xref:System.Windows.Media.DrawingVisual> des objets dans le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] couche visuelle.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>Objet DrawingVisual  
 Le <xref:System.Windows.Media.DrawingVisual> est une classe qui est utilisé pour restituer le texte, des images ou des formes de dessin légère. Cette classe est dite légère, car elle n’assure pas la gestion des dispositions ni des événements, ce qui améliore ses performances. C’est pourquoi, les dessins de ce type sont idéaux pour les arrière-plans et les images clipart.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>Conteneur hôte DrawingVisual  
 Pour pouvoir utiliser <xref:System.Windows.Media.DrawingVisual> objets, vous devez créer un conteneur hôte pour les objets. L’objet conteneur hôte doit dériver de la <xref:System.Windows.FrameworkElement> (classe), qui fournit la disposition et la gestion des événements qui le prennent en charge le <xref:System.Windows.Media.DrawingVisual> ne dispose pas de classe. L’objet de type conteneur hôte n’affiche pas de propriétés visibles, dans la mesure où son but principal est de contenir des objets enfants. Toutefois, le <xref:System.Windows.UIElement.Visibility%2A> propriété du conteneur hôte doit être définie sur <xref:System.Windows.Visibility.Visible>; sinon, aucun de ses éléments enfants seront visibles.  
  
 Lorsque vous créez un objet de conteneur hôte pour des objets visuels, vous devez stocker les références d’objet visuel dans un <xref:System.Windows.Media.VisualCollection>. Utilisez le <xref:System.Windows.Media.VisualCollection.Add%2A> méthode pour ajouter un objet visuel au conteneur hôte. Dans l’exemple suivant, un objet conteneur hôte est créé et trois objets visuels sont ajoutés à son <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  Pour consulter l’intégralité de l’exemple de code duquel l’exemple de code précédent a été extrait, référez-vous à la section [Hit Test Using DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994) (Test de positionnement à l’aide d’exemples de DrawingVisuals).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Création d'objets DrawingVisual  
 Lorsque vous créez un <xref:System.Windows.Media.DrawingVisual> de l’objet, il n’a aucun contenu de dessin. Vous pouvez ajouter du texte, des graphismes ou contenu de l’image en récupérant l’objet <xref:System.Windows.Media.DrawingContext> et de dessin dedans. Un <xref:System.Windows.Media.DrawingContext> est retourné en appelant le <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> méthode d’un <xref:System.Windows.Media.DrawingVisual> objet.  
  
 Pour dessiner un rectangle dans le <xref:System.Windows.Media.DrawingContext>, utilisez le <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> méthode de la <xref:System.Windows.Media.DrawingContext> objet. Il existe des méthodes similaires pour dessiner d’autres types de contenu. Quand vous avez terminé le contenu de dessin dans le <xref:System.Windows.Media.DrawingContext>, appelez le <xref:System.Windows.Media.DrawingContext.Close%2A> méthode pour fermer le <xref:System.Windows.Media.DrawingContext> et conserver le contenu.  
  
 Dans l’exemple suivant, un <xref:System.Windows.Media.DrawingVisual> objet est créé et un rectangle est dessiné dans son <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>Création de remplacements pour les membres FrameworkElement  
 L’objet de type conteneur hôte est chargé de gérer sa collection d’objets visuels. Cela nécessite que le conteneur hôte implémenter des substitutions de membres pour la dérivée <xref:System.Windows.FrameworkElement> classe.  
  
 La liste suivante décrit les deux membres que vous devez substituer :  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Retourne un enfant à l’index spécifié de la collection d’éléments enfants.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Obtient le nombre d’éléments enfants visuels dans cet élément.  
  
 Dans l’exemple suivant, des substitutions pour les deux <xref:System.Windows.FrameworkElement> membres sont implémentées.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>Prise en charge du test de positionnement  
 L’objet conteneur hôte peut fournir la gestion des événements même si elle n’affiche pas de propriétés visibles, toutefois, son <xref:System.Windows.UIElement.Visibility%2A> propriété doit être définie sur <xref:System.Windows.Visibility.Visible>. Cela vous permet de créer une routine de gestion des événements pour le conteneur hôte, capable de détecter les événements de la souris, tels que le relâchement du bouton gauche de la souris. Routine de gestion d’événements peuvent ensuite implémenter le test de positionnement en appelant le <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> (méthode). La méthode <xref:System.Windows.Media.HitTestResultCallback> paramètre fait référence à une procédure définie par l’utilisateur que vous pouvez utiliser pour déterminer l’action résultante d’un test de positionnement.  
  
 Dans l’exemple suivant, la prise en charge du test de positionnement est implémentée pour l’objet de type conteneur hôte et ses enfants.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [Vue d’ensemble du rendu graphique de WPF](wpf-graphics-rendering-overview.md)
- [Test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md)
