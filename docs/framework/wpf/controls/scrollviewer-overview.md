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
ms.openlocfilehash: 993f3c861cbead88df3503eb01f18e5d1f69e2d8
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458436"
---
# <a name="scrollviewer-overview"></a>Vue d'ensemble de ScrollViewer
Le contenu d’une interface utilisateur occupe souvent un espace plus important que la zone d’affiche d’un écran d’ordinateur. Le contrôle <xref:System.Windows.Controls.ScrollViewer> offre un moyen pratique d’activer le défilement du contenu dans les applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Cette rubrique présente l’élément <xref:System.Windows.Controls.ScrollViewer> et fournit plusieurs exemples d’utilisation.  
  
<a name="what_is_a_scrollviewer_element"></a>   
## <a name="the-scrollviewer-control"></a>Le contrôle ScrollViewer  
 Il existe deux éléments prédéfinis qui permettent le défilement dans des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] : <xref:System.Windows.Controls.Primitives.ScrollBar> et <xref:System.Windows.Controls.ScrollViewer>. Le contrôle <xref:System.Windows.Controls.ScrollViewer> encapsule les éléments <xref:System.Windows.Controls.Primitives.ScrollBar> horizontaux et verticaux et un conteneur de contenu (par exemple, un élément <xref:System.Windows.Controls.Panel>) afin d’afficher d’autres éléments visibles dans une zone à défilement. Vous devez générer un objet personnalisé afin d’utiliser l’élément <xref:System.Windows.Controls.Primitives.ScrollBar> pour le défilement du contenu. Toutefois, vous pouvez utiliser l’élément <xref:System.Windows.Controls.ScrollViewer> seul, car il s’agit d’un contrôle composite qui encapsule des fonctionnalités <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
 Le contrôle <xref:System.Windows.Controls.ScrollViewer> répond aux commandes de souris et de clavier, et définit de nombreuses méthodes permettant de faire défiler le contenu par incréments prédéterminés. Vous pouvez utiliser l’événement <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> pour détecter une modification dans un État <xref:System.Windows.Controls.ScrollViewer>.  
  
 Un <xref:System.Windows.Controls.ScrollViewer> ne peut avoir qu’un seul enfant, généralement un élément <xref:System.Windows.Controls.Panel> qui peut héberger une collection d’éléments <xref:System.Windows.Controls.Panel.Children%2A>. La propriété <xref:System.Windows.Controls.ContentPresenter.Content%2A> définit le seul enfant du <xref:System.Windows.Controls.ScrollViewer>.  
  
<a name="scrollviewer_physical_vs_logical"></a>   
## <a name="physical-vs-logical-scrolling"></a>Défilement physique et logique  
 Le défilement physique est utilisé pour faire défiler le contenu selon un incrément physique prédéterminé, généralement une valeur déclarée en pixels. Le défilement logique est utilisé pour faire défiler l’écran jusqu’à l’élément suivant dans l’arborescence logique. Le défilement physique est le comportement de défilement par défaut pour la plupart des éléments <xref:System.Windows.Controls.Panel>. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge les deux types de défilement.  
  
#### <a name="the-iscrollinfo-interface"></a>L’interface IScrollInfo  
 L’interface <xref:System.Windows.Controls.Primitives.IScrollInfo> représente la zone de défilement principale au sein d’un <xref:System.Windows.Controls.ScrollViewer> ou d’un contrôle dérivé. L’interface définit des propriétés et des méthodes de défilement qui peuvent être implémentées par <xref:System.Windows.Controls.Panel> éléments qui nécessitent un défilement par unité logique, plutôt que par incrément physique. Le cast d’une instance de <xref:System.Windows.Controls.Primitives.IScrollInfo> en une <xref:System.Windows.Controls.Panel> dérivée, puis l’utilisation de ses méthodes de défilement offre un moyen pratique de faire défiler vers l’unité logique suivante dans une collection enfant, plutôt que par incrément de pixel. Par défaut, le contrôle <xref:System.Windows.Controls.ScrollViewer> prend en charge le défilement par unités physiques.  
  
 <xref:System.Windows.Controls.StackPanel> et <xref:System.Windows.Controls.VirtualizingStackPanel> implémentent <xref:System.Windows.Controls.Primitives.IScrollInfo> et prennent en charge le défilement logique en mode natif. Pour les contrôles de disposition qui prennent en charge le défilement logique en mode natif, vous pouvez toujours effectuer un défilement physique en encapsulant l’élément hôte <xref:System.Windows.Controls.Panel> dans un <xref:System.Windows.Controls.ScrollViewer> et en affectant à la propriété <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> la valeur `false`.  
  
 L’exemple de code suivant montre comment effectuer un cast d’une instance de <xref:System.Windows.Controls.Primitives.IScrollInfo> en <xref:System.Windows.Controls.StackPanel> et utiliser les méthodes de défilement du contenu (<xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> et <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A>) définies par l’interface.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>   
## <a name="defining-and-using-a-scrollviewer-element"></a>Définition et utilisation d’un élément ScrollViewer  
 L’exemple suivant crée un <xref:System.Windows.Controls.ScrollViewer> dans une fenêtre qui contient du texte et un rectangle. les éléments de <xref:System.Windows.Controls.Primitives.ScrollBar> s’affichent uniquement lorsqu’ils sont nécessaires. Lorsque vous redimensionnez la fenêtre, les éléments <xref:System.Windows.Controls.Primitives.ScrollBar> apparaissent et disparaissent, en raison des valeurs mises à jour des propriétés <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> et <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A>.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>   
## <a name="styling-a-scrollviewer"></a>Application d’un style à un élément ScrollViewer  
 Comme tous les contrôles de Windows Presentation Foundation, le style du <xref:System.Windows.Controls.ScrollViewer> peut être appliqué pour modifier le comportement de rendu par défaut du contrôle. Pour plus d’informations sur l’application d’un style aux contrôles, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>   
## <a name="paginating-documents"></a>Pagination de documents  
 Pour le contenu de document, il est possible de choisir un conteneur de documents qui prend en charge la pagination plutôt que d’utiliser le défilement. <xref:System.Windows.Documents.FlowDocument> concerne les documents qui sont conçus pour être hébergés dans un contrôle d’affichage, tel que <xref:System.Windows.Controls.FlowDocumentPageViewer>, qui prend en charge la pagination du contenu sur plusieurs pages, ce qui évite d’avoir à faire défiler le contenu. <xref:System.Windows.Controls.DocumentViewer> fournit une solution pour afficher du contenu <xref:System.Windows.Documents.FixedDocument>, qui utilise le défilement traditionnel pour afficher le contenu en dehors du domaine de la zone d’affichage.  
  
 Pour plus d’informations sur les formats et les options de présentation de documents, consultez [Documents dans WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Comment : créer une visionneuse de défilement](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Documents dans WPF](../advanced/documents-in-wpf.md)
- [Styles et modèles ScrollBar](scrollbar-styles-and-templates.md)
- [Contrôles](../advanced/optimizing-performance-controls.md)
