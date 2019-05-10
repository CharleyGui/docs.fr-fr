---
title: 'Optimisation des performances : Disposition et conception'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: a18cc364d625cc98f77e63b0f361980ef574e8a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611907"
---
# <a name="optimizing-performance-layout-and-design"></a>Optimisation des performances : Disposition et conception
La conception de votre [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application peut influer sur ses performances en créant des charges mémoire inutiles pour calculer la disposition et valider les références d’objet. La construction d’objets, en particulier au moment de l’exécution, peut affecter les caractéristiques de performances de votre application.  
  
 Cette rubrique fournit des recommandations sur ces aspects des performances.  
  
## <a name="layout"></a>Mise en page  
 Le terme « passe de disposition » décrit le processus de mesure et réorganisation des membres d’un <xref:System.Windows.Controls.Panel>-dérivée de collection d’objets des enfants et ensuite les dessiner à l’écran. La passe de disposition est un processus mathématique intensif (le nombre de calculs nécessaires est proportionnel au nombre d’enfants présents dans la collection). Par exemple, chaque fois qu’un enfant <xref:System.Windows.UIElement> objet dans la collection change de position, il a la possibilité de déclencher une nouvelle passe par le système de disposition. Compte tenu de la relation étroite entre les caractéristiques d’objet et le comportement de disposition, il est important de comprendre le type des événements qui peuvent appeler le système de disposition. Votre application sera d’autant plus performante que vous réduirez autant que possible les appels inutiles de la passe de disposition.  
  
 Le système de disposition effectue deux passes pour chaque membre enfant d’une collection : une passe de mesure et une passe de réorganisation. Chaque objet enfant propose sa propre implémentation substituée de le <xref:System.Windows.UIElement.Measure%2A> et <xref:System.Windows.UIElement.Arrange%2A> méthodes afin de fournir son propre comportement de disposition spécifique. Pour schématiser, une disposition est un système récursif qui entraîne le dimensionnement, le positionnement et le tracé d’un élément à l’écran.  
  
- Un enfant <xref:System.Windows.UIElement> objet commence le processus de disposition en faisant d’abord ses propriétés principales mesurées.  
  
- L’objet <xref:System.Windows.FrameworkElement> propriétés liées à la taille, telles que <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, et <xref:System.Windows.FrameworkElement.Margin%2A>, sont évaluées.  
  
- <xref:System.Windows.Controls.Panel>-logique spécifique est appliquée, telles que la <xref:System.Windows.Controls.DockPanel.Dock%2A> propriété de la <xref:System.Windows.Controls.DockPanel>, ou le <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriété de la <xref:System.Windows.Controls.StackPanel>.  
  
- Le contenu est réorganisé, ou positionné, après que tous les objets enfants ont été mesurés.  
  
- La collection d’objets enfants est dessinée à l’écran.  
  
 Le processus de passe de disposition est encore appelé si l’une des actions suivantes se produit :  
  
- Un objet enfant est ajouté à la collection.  
  
- Un <xref:System.Windows.FrameworkElement.LayoutTransform%2A> est appliqué à l’objet enfant.  
  
- Le <xref:System.Windows.UIElement.UpdateLayout%2A> méthode est appelée pour l’objet enfant.  
  
- Quand une modification est apportée à la valeur d’une propriété de dépendance marquée avec des métadonnées qui affectent les passes de mesure ou de réorganisation.  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>Utiliser le panneau le plus efficace si possible  
 La complexité du processus de disposition est directement basée sur le comportement de disposition de la <xref:System.Windows.Controls.Panel>-éléments dérivés que vous utilisez. Par exemple, un <xref:System.Windows.Controls.Grid> ou <xref:System.Windows.Controls.StackPanel> contrôle fournit beaucoup plus de fonctionnalités qu’un <xref:System.Windows.Controls.Canvas> contrôle. Ce choix accru de fonctionnalités se traduit par une augmentation du coût des performances. Toutefois, si vous n’avez pas besoin de la fonctionnalité qui un <xref:System.Windows.Controls.Grid> fournit de contrôle, vous devez utiliser les alternatives moins coûteuses, comme un <xref:System.Windows.Controls.Canvas> ou un panneau personnalisé.  
  
 Pour plus d’informations, consultez la page [Vue d’ensemble de Panel](../controls/panels-overview.md).  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>Mettre à jour RenderTransform au lieu de le remplacer  
 Vous pourrez peut-être mettre à jour un <xref:System.Windows.Media.Transform> au lieu d’en remplaçant la valeur d’un <xref:System.Windows.UIElement.RenderTransform%2A> propriété. C’est notamment le cas dans les scénarios qui comportent une animation. En mettant à jour une existante <xref:System.Windows.Media.Transform>, vous évitez d’initier un calcul de disposition inutile.  
  
### <a name="build-your-tree-top-down"></a>Générer votre arborescence de haut en bas  
 Quand un nœud est ajouté ou supprimé de l’arborescence logique, des invalidations de propriété sont déclenchées sur le parent du nœud et tous ses enfants. De ce fait, il convient de toujours suivre un modèle de construction de haut en bas pour éviter le coût d’invalidations inutiles sur des nœuds qui ont déjà été validés. Le tableau suivant montre la différence de vitesse d’exécution entre la génération d’une arborescence de haut en bas et bas en haut, où l’arborescence comprend 150 niveaux avec une seule <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Controls.DockPanel> à chaque niveau.  
  
|**Action**|**Construction d’arborescence (en ms)**|**Rendu — construction d’arborescence incluse (en ms)**|  
|----------------|---------------------------------|-------------------------------------------------|  
|De bas en haut|366|454|  
|De haut en bas|11|96|  
  
 L’exemple de code suivant montre comment créer une arborescence de haut en bas.  
  
 [!code-csharp[Performance#PerformanceSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 Pour plus d’informations sur l’arborescence logique, consultez [Arborescences dans WPF](trees-in-wpf.md).  
  
## <a name="see-also"></a>Voir aussi

- [Optimisation des performances des applications WPF](optimizing-wpf-application-performance.md)
- [Planification des performances des applications](planning-for-application-performance.md)
- [Tirer parti du matériel](optimizing-performance-taking-advantage-of-hardware.md)
- [Graphiques 2D et acquisition d'images](optimizing-performance-2d-graphics-and-imaging.md)
- [Comportement de l’objet](optimizing-performance-object-behavior.md)
- [Ressources d'application](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Liaison de données](optimizing-performance-data-binding.md)
- [Autres recommandations relatives aux performances](optimizing-performance-other-recommendations.md)
- [Disposition](layout.md)
