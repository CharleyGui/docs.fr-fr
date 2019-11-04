---
title: "Comment : trier et grouper des données à l'aide d'une vue en XAML"
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: 9e42dd330535f71438ab7af3dca9d078e9dfd8d3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460128"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a><span data-ttu-id="0da7a-102">Comment : trier et grouper des données à l'aide d'une vue en XAML</span><span class="sxs-lookup"><span data-stu-id="0da7a-102">How to: Sort and Group Data Using a View in XAML</span></span>
<span data-ttu-id="0da7a-103">Cet exemple montre comment créer une vue d’une collection de données dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0da7a-103">This example shows how to create a view of a data collection in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="0da7a-104">Les vues permettent les fonctionnalités de regroupement, de tri, de filtrage et la notion d’un élément actuel.</span><span class="sxs-lookup"><span data-stu-id="0da7a-104">Views allow for the functionalities of grouping, sorting, filtering, and the notion of a current item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0da7a-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="0da7a-105">Example</span></span>  
 <span data-ttu-id="0da7a-106">Dans l’exemple suivant, la ressource statique nommée *places* est définie comme une collection d’objets *place* , dans laquelle chaque objet *place* est constitué d’un nom de ville et de l’État.</span><span class="sxs-lookup"><span data-stu-id="0da7a-106">In the following example, the static resource named *places* is defined as a collection of *Place* objects, in which each *Place* object is consisted of a city name and the state.</span></span> <span data-ttu-id="0da7a-107">Le préfixe *src* est mappé à l’espace de noms dans lequel *la source de* données est définie.</span><span class="sxs-lookup"><span data-stu-id="0da7a-107">The prefix *src* is mapped to the namespace where the data source *Places* is defined.</span></span> <span data-ttu-id="0da7a-108">Le préfixe *SCM* est mappé à `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` et les *fichiers DAT* sont mappés à `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span><span class="sxs-lookup"><span data-stu-id="0da7a-108">The prefix *scm* maps to `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` and *dat* maps to `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.</span></span>  
  
 <span data-ttu-id="0da7a-109">L’exemple suivant crée une vue de la collection de données qui est triée par nom de ville et regroupée par État.</span><span class="sxs-lookup"><span data-stu-id="0da7a-109">The following example creates a view of the data collection that is sorted by the city name and grouped by the state.</span></span>  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 <span data-ttu-id="0da7a-110">La vue peut ensuite être une source de liaison, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="0da7a-110">The view can then be a binding source, as in the following example:</span></span>  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 <span data-ttu-id="0da7a-111">Pour les liaisons aux données XML définies dans une ressource <xref:System.Windows.Data.XmlDataProvider>, faites précéder le nom XML d’un symbole @.</span><span class="sxs-lookup"><span data-stu-id="0da7a-111">For bindings to XML data defined in an <xref:System.Windows.Data.XmlDataProvider> resource, precede the XML name with an @ symbol.</span></span>  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a><span data-ttu-id="0da7a-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0da7a-112">See also</span></span>

- <xref:System.Windows.Data.CollectionViewSource>
- [<span data-ttu-id="0da7a-113">Obtenir la vue par défaut d'une collection de données</span><span class="sxs-lookup"><span data-stu-id="0da7a-113">Get the Default View of a Data Collection</span></span>](how-to-get-the-default-view-of-a-data-collection.md)
- [<span data-ttu-id="0da7a-114">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="0da7a-114">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="0da7a-115">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="0da7a-115">How-to Topics</span></span>](data-binding-how-to-topics.md)
