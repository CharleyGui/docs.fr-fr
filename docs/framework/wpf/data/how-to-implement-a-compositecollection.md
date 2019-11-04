---
title: 'Comment : implémenter une classe CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: b3450cdc476b7090251a06b5b2b2718d29e18209
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454029"
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="3b8d0-102">Comment : implémenter une classe CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="3b8d0-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="3b8d0-103">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b8d0-103">Example</span></span>  
 <span data-ttu-id="3b8d0-104">L’exemple suivant montre comment afficher plusieurs collections et éléments sous la forme d’une liste à l’aide de la classe <xref:System.Windows.Data.CompositeCollection>.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="3b8d0-105">Dans cet exemple, `GreekGods` est une <xref:System.Collections.ObjectModel.ObservableCollection%601> d' `GreekGod` objets personnalisés.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="3b8d0-106">Les modèles de données sont définis de façon à ce que `GreekGod` objets et les objets de `GreekHero` apparaissent respectivement avec une couleur d’arrière-plan jaune et cyan.</span><span class="sxs-lookup"><span data-stu-id="3b8d0-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3b8d0-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b8d0-107">See also</span></span>

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [<span data-ttu-id="3b8d0-108">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="3b8d0-108">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="3b8d0-109">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="3b8d0-109">How-to Topics</span></span>](data-binding-how-to-topics.md)
