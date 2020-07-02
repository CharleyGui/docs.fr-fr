---
title: 'Comment : effectuer une liaison à une collection et afficher des informations basées sur la sélection'
description: Suivez cet exemple pour savoir comment effectuer une liaison à une collection et afficher des informations basées sur la sélection dans le Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619609"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a><span data-ttu-id="6c08d-103">Comment : effectuer une liaison à une collection et afficher des informations basées sur la sélection</span><span class="sxs-lookup"><span data-stu-id="6c08d-103">How to: Bind to a Collection and Display Information Based on Selection</span></span>
<span data-ttu-id="6c08d-104">Dans un scénario maître-détail simple, vous avez une liaison de données <xref:System.Windows.Controls.ItemsControl> telle que <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="6c08d-104">In a simple master-detail scenario, you have a data-bound <xref:System.Windows.Controls.ItemsControl> such as a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="6c08d-105">En fonction de la sélection de l’utilisateur, vous pouvez afficher plus d’informations sur l’élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="6c08d-105">Based on user selection, you display more information about the selected item.</span></span> <span data-ttu-id="6c08d-106">Cet exemple montre comment implémenter ce scénario.</span><span class="sxs-lookup"><span data-stu-id="6c08d-106">This example shows how to implement this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c08d-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="6c08d-107">Example</span></span>  
 <span data-ttu-id="6c08d-108">Dans cet exemple, `People` est un <xref:System.Collections.ObjectModel.ObservableCollection%601> de `Person` classes.</span><span class="sxs-lookup"><span data-stu-id="6c08d-108">In this example, `People` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `Person` classes.</span></span> <span data-ttu-id="6c08d-109">Cette `Person` classe contient trois propriétés : `FirstName` , `LastName` et `HomeTown` , tout type `string` .</span><span class="sxs-lookup"><span data-stu-id="6c08d-109">This `Person` class contains three properties: `FirstName`, `LastName`, and `HomeTown`, all of type `string`.</span></span>  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <span data-ttu-id="6c08d-110">Le <xref:System.Windows.Controls.ContentControl> utilise les éléments suivants <xref:System.Windows.DataTemplate> qui définissent le mode de présentation des informations d’un `Person` :</span><span class="sxs-lookup"><span data-stu-id="6c08d-110">The <xref:System.Windows.Controls.ContentControl> uses the following <xref:System.Windows.DataTemplate> that defines how the information of a `Person` is presented:</span></span>  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 <span data-ttu-id="6c08d-111">La capture d’écran suivante illustre ce que produit l’exemple.</span><span class="sxs-lookup"><span data-stu-id="6c08d-111">The following is a screenshot of what the example produces.</span></span> <span data-ttu-id="6c08d-112">La <xref:System.Windows.Controls.ContentControl> affiche les autres propriétés de la personne sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="6c08d-112">The <xref:System.Windows.Controls.ContentControl> shows the other properties of the person selected.</span></span>  
  
 <span data-ttu-id="6c08d-113">![Liaison à une collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span><span class="sxs-lookup"><span data-stu-id="6c08d-113">![Binding to a collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")</span></span>  
  
 <span data-ttu-id="6c08d-114">Les deux points à noter dans cet exemple sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="6c08d-114">The two things to notice in this example are:</span></span>  
  
1. <span data-ttu-id="6c08d-115"><xref:System.Windows.Controls.ListBox>Et la <xref:System.Windows.Controls.ContentControl> liaison à la même source.</span><span class="sxs-lookup"><span data-stu-id="6c08d-115">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.ContentControl> bind to the same source.</span></span> <span data-ttu-id="6c08d-116">Les <xref:System.Windows.Data.Binding.Path%2A> Propriétés des deux liaisons ne sont pas spécifiées, car les deux contrôles sont en liaison avec l’objet de collection entier.</span><span class="sxs-lookup"><span data-stu-id="6c08d-116">The <xref:System.Windows.Data.Binding.Path%2A> properties of both bindings are not specified because both controls are binding to the entire collection object.</span></span>  
  
2. <span data-ttu-id="6c08d-117">Vous devez affecter la valeur à la propriété pour que <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> `true` cela fonctionne.</span><span class="sxs-lookup"><span data-stu-id="6c08d-117">You must set the <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> property to `true` for this to work.</span></span> <span data-ttu-id="6c08d-118">La définition de cette propriété permet de s’assurer que l’élément sélectionné est toujours défini en tant que <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> .</span><span class="sxs-lookup"><span data-stu-id="6c08d-118">Setting this property ensures that the selected item is always set as the <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>.</span></span> <span data-ttu-id="6c08d-119">Sinon, si le <xref:System.Windows.Controls.ListBox> récupère les données à partir d’un <xref:System.Windows.Data.CollectionViewSource> , il synchronise automatiquement la sélection et la devise.</span><span class="sxs-lookup"><span data-stu-id="6c08d-119">Alternatively, if the <xref:System.Windows.Controls.ListBox> gets it data from a <xref:System.Windows.Data.CollectionViewSource>, it synchronizes selection and currency automatically.</span></span>  
  
 <span data-ttu-id="6c08d-120">Notez que la `Person` classe substitue la `ToString` méthode de la façon suivante.</span><span class="sxs-lookup"><span data-stu-id="6c08d-120">Note that the `Person` class overrides the `ToString` method the following way.</span></span> <span data-ttu-id="6c08d-121">Par défaut, le <xref:System.Windows.Controls.ListBox> appelle `ToString` et affiche une représentation sous forme de chaîne de chaque objet de la collection liée.</span><span class="sxs-lookup"><span data-stu-id="6c08d-121">By default, the <xref:System.Windows.Controls.ListBox> calls `ToString` and displays a string representation of each object in the bound collection.</span></span> <span data-ttu-id="6c08d-122">C’est pourquoi chaque `Person` apparaît comme un prénom dans le <xref:System.Windows.Controls.ListBox> .</span><span class="sxs-lookup"><span data-stu-id="6c08d-122">That is why each `Person` appears as a first name in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a><span data-ttu-id="6c08d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c08d-123">See also</span></span>

- [<span data-ttu-id="6c08d-124">Utiliser le modèle maître/détail avec des données hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="6c08d-124">Use the Master-Detail Pattern with Hierarchical Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [<span data-ttu-id="6c08d-125">Utiliser le modèle maître/détail avec des données XML hiérarchiques</span><span class="sxs-lookup"><span data-stu-id="6c08d-125">Use the Master-Detail Pattern with Hierarchical XML Data</span></span>](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [<span data-ttu-id="6c08d-126">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="6c08d-126">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="6c08d-127">Vue d'ensemble des modèles de données</span><span class="sxs-lookup"><span data-stu-id="6c08d-127">Data Templating Overview</span></span>](data-templating-overview.md)
- [<span data-ttu-id="6c08d-128">Rubriques de procédures</span><span class="sxs-lookup"><span data-stu-id="6c08d-128">How-to Topics</span></span>](data-binding-how-to-topics.md)
