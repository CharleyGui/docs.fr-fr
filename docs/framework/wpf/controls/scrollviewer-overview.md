---
title: Vue d'ensemble de ScrollViewer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 2ff0f134ea3174f7f034d47446aab782e2141916
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186983"
---
# <a name="scrollviewer-overview"></a>Vue d'ensemble de ScrollViewer
Le contenu d’une interface utilisateur occupe souvent un espace plus important que la zone d’affiche d’un écran d’ordinateur. Le <xref:System.Windows.Controls.ScrollViewer> contrôle fournit un moyen pratique d’activer le défilement du contenu dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] les applications. Ce sujet introduit <xref:System.Windows.Controls.ScrollViewer> l’élément et fournit plusieurs exemples d’utilisation.  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>Le contrôle ScrollViewer  
 Il existe deux éléments prédéfinis [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui <xref:System.Windows.Controls.Primitives.ScrollBar> permettent <xref:System.Windows.Controls.ScrollViewer>le défilement dans les applications: et . Le <xref:System.Windows.Controls.ScrollViewer> contrôle encapsule des <xref:System.Windows.Controls.Primitives.ScrollBar> éléments horizontaux et <xref:System.Windows.Controls.Panel> verticaux et un récipient de contenu (comme un élément) afin d’afficher d’autres éléments visibles dans une zone défilementable. Vous devez construire un objet personnalisé <xref:System.Windows.Controls.Primitives.ScrollBar> afin d’utiliser l’élément pour le défilement du contenu. Cependant, vous pouvez <xref:System.Windows.Controls.ScrollViewer> utiliser l’élément par lui-même parce <xref:System.Windows.Controls.Primitives.ScrollBar> qu’il s’agit d’un contrôle composite qui encapsule la fonctionnalité.  
  
 Le <xref:System.Windows.Controls.ScrollViewer> contrôle répond aux commandes de la souris et du clavier, et définit de nombreuses méthodes pour faire défiler le contenu par incréments prédéterminés. Vous pouvez <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> utiliser l’événement pour <xref:System.Windows.Controls.ScrollViewer> détecter un changement dans un état.  
  
 A <xref:System.Windows.Controls.ScrollViewer> ne peut avoir qu’un seul enfant, généralement un <xref:System.Windows.Controls.Panel> élément qui peut héberger une <xref:System.Windows.Controls.Panel.Children%2A> collection d’éléments. La <xref:System.Windows.Controls.ContentPresenter.Content%2A> propriété définit l’unique <xref:System.Windows.Controls.ScrollViewer>enfant de la .  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>Défilement physique vs logique  
 Le défilement physique est utilisé pour faire défiler le contenu selon un incrément physique prédéterminé, généralement une valeur déclarée en pixels. Le défilement logique est utilisé pour faire défiler l’écran jusqu’à l’élément suivant dans l’arborescence logique. Le défilement physique est <xref:System.Windows.Controls.Panel> le comportement par défaut de défilement pour la plupart des éléments. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge les deux types de défilement.  
  
#### <a name="the-iscrollinfo-interface"></a>L’interface IScrollInfo  
 L’interface <xref:System.Windows.Controls.Primitives.IScrollInfo> représente la principale <xref:System.Windows.Controls.ScrollViewer> région de défilement dans un contrôle ou dérivé. L’interface définit les propriétés et les <xref:System.Windows.Controls.Panel> méthodes de défilement qui peuvent être mises en œuvre par des éléments qui nécessitent un défilement par unité logique, plutôt que par une augmentation physique. Le fait <xref:System.Windows.Controls.Primitives.IScrollInfo> de jeter <xref:System.Windows.Controls.Panel> une instance à un dérivé, puis en utilisant ses méthodes de défilement fournit un moyen utile de faire défiler vers la prochaine unité logique dans une collection d’enfants, plutôt que par incrément de pixel. Par défaut, <xref:System.Windows.Controls.ScrollViewer> le contrôle prend en charge le défilement par unités physiques.  
  
 <xref:System.Windows.Controls.StackPanel>et <xref:System.Windows.Controls.VirtualizingStackPanel> à <xref:System.Windows.Controls.Primitives.IScrollInfo> la fois l’implémentation et le soutien natif défilement logique. Pour les contrôles de mise en page qui prennent en charge <xref:System.Windows.Controls.Panel> le défilement logique natif, vous pouvez toujours réaliser le défilement physique en enveloppant l’élément hôte dans un <xref:System.Windows.Controls.ScrollViewer> et en définissant la <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> propriété à `false`.  
  
 L’exemple de code suivant montre <xref:System.Windows.Controls.Primitives.IScrollInfo> comment <xref:System.Windows.Controls.StackPanel> lancer une instance de<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>et d’utiliser des méthodes de défilement de contenu ( et ) définis par l’interface.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>Définition et utilisation d’un élément ScrollViewer  
 L’exemple suivant <xref:System.Windows.Controls.ScrollViewer> crée un dans une fenêtre qui contient du texte et un rectangle. <xref:System.Windows.Controls.Primitives.ScrollBar>éléments n’apparaissent que lorsqu’ils sont nécessaires. Lorsque vous resize la <xref:System.Windows.Controls.Primitives.ScrollBar> fenêtre, les éléments apparaissent et <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> disparaissent, en raison des valeurs mises à jour de la et des propriétés.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>Application d’un style à un élément ScrollViewer  
 Comme tous les contrôles dans <xref:System.Windows.Controls.ScrollViewer> Windows Presentation Foundation, le peut être stylé afin de changer le comportement de rendu par défaut du contrôle. Pour plus d’informations sur l’application d’un style aux contrôles, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>Pagination de documents  
 Pour le contenu de document, il est possible de choisir un conteneur de documents qui prend en charge la pagination plutôt que d’utiliser le défilement. <xref:System.Windows.Documents.FlowDocument>est pour les documents qui sont conçus pour être <xref:System.Windows.Controls.FlowDocumentPageViewer>hébergés dans un contrôle de visualisation, tels que , qui prend en charge la pagination du contenu sur plusieurs pages, empêchant la nécessité de défilement. <xref:System.Windows.Controls.DocumentViewer>fournit une solution <xref:System.Windows.Documents.FixedDocument> pour l’affichage du contenu, qui utilise le défilement traditionnel pour afficher du contenu en dehors du domaine de la zone d’affichage.  
  
 Pour plus d’informations sur les formats et les options de présentation de documents, consultez [Documents dans WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Comment : Créer un visualiseur de défilement](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Documents dans WPF](../advanced/documents-in-wpf.md)
- [Styles et modèles ScrollBar](scrollbar-styles-and-templates.md)
- [Commandes](../advanced/optimizing-performance-controls.md)
