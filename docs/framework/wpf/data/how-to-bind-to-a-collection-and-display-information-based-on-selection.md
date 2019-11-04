---
title: 'Comment : effectuer une liaison à une collection et afficher des informations basées sur la sélection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459146"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="041fe-102">Comment : effectuer une liaison à une collection et afficher des informations basées sur la sélection</span><span class="sxs-lookup"><span data-stu-id="041fe-102">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="041fe-103">Dans un scénario maître-détail simple, vous avez un <xref:System.Windows.Controls.ItemsControl> lié aux données, tel qu’une <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="041fe-103">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="041fe-104">En fonction de la sélection de l’utilisateur, vous pouvez afficher plus d’informations sur l’élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="041fe-104">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="041fe-105">Cet exemple montre comment implémenter ce scénario.</span><span class="sxs-lookup"><span data-stu-id="041fe-105">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="041fe-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="041fe-106">Example</span></span>  
 <span data-ttu-id="041fe-107">Dans cet exemple, `People` est une <xref:System.Collections.ObjectModel.ObservableCollection%601> de `Person` classes.</span><span class="sxs-lookup"><span data-stu-id="041fe-107">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="041fe-108">Cette classe `Person` contient trois propriétés : `FirstName`, `LastName`et `HomeTown`, tout type `string`.</span><span class="sxs-lookup"><span data-stu-id="041fe-108">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="041fe-109">L' <xref:System.Windows.Controls.ContentControl> utilise les <xref:System.Windows.DataTemplate> suivantes qui définissent le mode de présentation des informations d’un `Person` :</span><span class="sxs-lookup"><span data-stu-id="041fe-109">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="041fe-110">La capture d’écran suivante illustre ce que produit l’exemple.</span><span class="sxs-lookup"><span data-stu-id="041fe-110">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="041fe-111">Le <xref:System.Windows.Controls.ContentControl> affiche les autres propriétés de la personne sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="041fe-111">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="041fe-112">![Liaison à une collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="041fe-112">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="041fe-113">Les deux points à noter dans cet exemple sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="041fe-113">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="041fe-114">Le <xref:System.Windows.Controls.ListBox> et le <xref:System.Windows.Controls.ContentControl> être liés à la même source.</span><span class="sxs-lookup"><span data-stu-id="041fe-114">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="041fe-115">Les propriétés <xref:System.Windows.Data.Binding.Path%2A> des deux liaisons ne sont pas spécifiées, car les deux contrôles sont en liaison avec l’objet de collection entier.</span><span class="sxs-lookup"><span data-stu-id="041fe-115">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="041fe-116">Vous devez définir la propriété <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> sur `true` pour que cela fonctionne.</span><span class="sxs-lookup"><span data-stu-id="041fe-116">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="041fe-117">La définition de cette propriété permet de s’assurer que l’élément sélectionné est toujours défini en tant que <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="041fe-117">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="041fe-118">Sinon, si le <xref:System.Windows.Controls.ListBox> obtient des données à partir d’un <xref:System.Windows.Data.CollectionViewSource>, il synchronise automatiquement la sélection et la devise.</span><span class="sxs-lookup"><span data-stu-id="041fe-118">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="041fe-119">Notez que la classe `Person` remplace la méthode `ToString` de la façon suivante.</span><span class="sxs-lookup"><span data-stu-id="041fe-119">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="041fe-120">Par défaut, le <xref:System.Windows.Controls.ListBox> appelle `ToString` et affiche une représentation sous forme de chaîne de chaque objet de la collection liée.</span><span class="sxs-lookup"><span data-stu-id="041fe-120">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="041fe-121">C’est pourquoi chaque `Person` apparaît en tant que prénom dans le <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="041fe-121">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="041fe-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="041fe-122">See also</span></span>

- [<span data-ttu-id="041fe-123">Utiliser le modèle maître/détail avec des données hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="041fe-123">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="041fe-124">Utiliser le modèle maître/détail avec des données XML hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="041fe-124">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="041fe-125">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="041fe-125">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="041fe-126">Vue d’ensemble des modèles de données</span><span class="sxs-lookup"><span data-stu-id="041fe-126">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="041fe-127">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="041fe-127">How-to Topics</span></span>](data-binding-how-to-topics.md)
