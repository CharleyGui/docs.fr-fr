---
title: Vue d'ensemble de ScrollViewer
description: En savoir plus sur le contrôle ScrollViewer, qui permet de faire défiler le contenu des applications Windows Presentation Foundation. Consultez Exemples d’utilisation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 1ef680bb004315a2b523814714d5533535d044e5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164635"
---
# <a name="scrollviewer-overview"></a>Vue d'ensemble de ScrollViewer
Le contenu d’une interface utilisateur occupe souvent un espace plus important que la zone d’affiche d’un écran d’ordinateur. Le <xref:System.Windows.Controls.ScrollViewer> contrôle offre un moyen pratique d’activer le défilement du contenu dans les [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications. Cette rubrique présente l' <xref:System.Windows.Controls.ScrollViewer> élément et fournit plusieurs exemples d’utilisation.  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>Le contrôle ScrollViewer  
 Il existe deux éléments prédéfinis qui permettent de faire défiler [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] les applications : <xref:System.Windows.Controls.Primitives.ScrollBar> et <xref:System.Windows.Controls.ScrollViewer> . Le <xref:System.Windows.Controls.ScrollViewer> contrôle encapsule des éléments horizontaux et verticaux <xref:System.Windows.Controls.Primitives.ScrollBar> et un conteneur de contenu (par exemple, un <xref:System.Windows.Controls.Panel> élément) afin d’afficher d’autres éléments visibles dans une zone à défilement. Vous devez générer un objet personnalisé afin d’utiliser l' <xref:System.Windows.Controls.Primitives.ScrollBar> élément pour le défilement du contenu. Toutefois, vous pouvez utiliser l' <xref:System.Windows.Controls.ScrollViewer> élément seul, car il s’agit d’un contrôle composite qui encapsule des <xref:System.Windows.Controls.Primitives.ScrollBar> fonctionnalités.  
  
 Le <xref:System.Windows.Controls.ScrollViewer> contrôle répond aux commandes de souris et de clavier, et définit de nombreuses méthodes permettant de faire défiler le contenu par incréments prédéterminés. Vous pouvez utiliser l' <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> événement pour détecter une modification dans un <xref:System.Windows.Controls.ScrollViewer> État.  
  
 Un <xref:System.Windows.Controls.ScrollViewer> ne peut avoir qu’un seul enfant, généralement un <xref:System.Windows.Controls.Panel> élément qui peut héberger une <xref:System.Windows.Controls.Panel.Children%2A> collection d’éléments. La <xref:System.Windows.Controls.ContentPresenter.Content%2A> propriété définit le seul enfant de <xref:System.Windows.Controls.ScrollViewer> .  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>Défilement physique et logique  
 Le défilement physique est utilisé pour faire défiler le contenu selon un incrément physique prédéterminé, généralement une valeur déclarée en pixels. Le défilement logique est utilisé pour faire défiler l’écran jusqu’à l’élément suivant dans l’arborescence logique. Le défilement physique est le comportement de défilement par défaut pour la plupart des <xref:System.Windows.Controls.Panel> éléments. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge les deux types de défilement.  
  
#### <a name="the-iscrollinfo-interface"></a>L’interface IScrollInfo  
 L' <xref:System.Windows.Controls.Primitives.IScrollInfo> interface représente la zone de défilement principale dans un <xref:System.Windows.Controls.ScrollViewer> contrôle dérivé de ou. L’interface définit des propriétés et des méthodes de défilement qui peuvent être implémentées par des <xref:System.Windows.Controls.Panel> éléments qui requièrent le défilement par unité logique, plutôt que par incrément physique. Le cast d’une instance de <xref:System.Windows.Controls.Primitives.IScrollInfo> vers un dérivé <xref:System.Windows.Controls.Panel> et l’utilisation de ses méthodes de défilement offrent un moyen pratique de faire défiler jusqu’à l’unité logique suivante dans une collection enfant, plutôt que par incrément de pixel. Par défaut, le <xref:System.Windows.Controls.ScrollViewer> contrôle prend en charge le défilement par unités physiques.  
  
 <xref:System.Windows.Controls.StackPanel>et <xref:System.Windows.Controls.VirtualizingStackPanel> implémentent <xref:System.Windows.Controls.Primitives.IScrollInfo> et prennent en charge le défilement logique en mode natif. Pour les contrôles de disposition qui prennent en charge le défilement logique en mode natif, vous pouvez toujours atteindre le défilement physique en encapsulant l' <xref:System.Windows.Controls.Panel> élément hôte dans un <xref:System.Windows.Controls.ScrollViewer> et en affectant à la propriété la valeur <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> `false` .  
  
 L’exemple de code suivant montre comment effectuer un cast d’une instance de <xref:System.Windows.Controls.Primitives.IScrollInfo> en <xref:System.Windows.Controls.StackPanel> et utiliser les méthodes de défilement du contenu ( <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> et <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> ) définies par l’interface.  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>Définition et utilisation d’un élément ScrollViewer  
 L’exemple suivant crée un <xref:System.Windows.Controls.ScrollViewer> dans une fenêtre qui contient du texte et un rectangle. <xref:System.Windows.Controls.Primitives.ScrollBar>les éléments s’affichent uniquement lorsqu’ils sont nécessaires. Lorsque vous redimensionnez la fenêtre, les <xref:System.Windows.Controls.Primitives.ScrollBar> éléments apparaissent et disparaissent, en raison des valeurs mises à jour des <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> Propriétés et.  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>Application d’un style à un élément ScrollViewer  
 Comme tous les contrôles de Windows Presentation Foundation, le <xref:System.Windows.Controls.ScrollViewer> style peut être appliqué afin de modifier le comportement de rendu par défaut du contrôle. Pour plus d’informations sur l’application d’un style aux contrôles, consultez [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>Pagination de documents  
 Pour le contenu de document, il est possible de choisir un conteneur de documents qui prend en charge la pagination plutôt que d’utiliser le défilement. <xref:System.Windows.Documents.FlowDocument>concerne les documents qui sont conçus pour être hébergés dans un contrôle d’affichage, tel que <xref:System.Windows.Controls.FlowDocumentPageViewer> , qui prend en charge la pagination du contenu sur plusieurs pages, ce qui évite d’avoir à faire défiler le contenu. <xref:System.Windows.Controls.DocumentViewer>fournit une solution pour afficher <xref:System.Windows.Documents.FixedDocument> du contenu, qui utilise le défilement traditionnel pour afficher le contenu en dehors du domaine de la zone d’affichage.  
  
 Pour plus d’informations sur les formats et les options de présentation de documents, consultez [Documents dans WPF](../advanced/documents-in-wpf.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [Comment : créer une visionneuse de défilement](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [Documents dans WPF](../advanced/documents-in-wpf.md)
- [Styles et modèles ScrollBar](scrollbar-styles-and-templates.md)
- [Contrôles](../advanced/optimizing-performance-controls.md)
