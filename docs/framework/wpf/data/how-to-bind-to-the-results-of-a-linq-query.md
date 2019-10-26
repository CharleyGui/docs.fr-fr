---
title: "Comment : effectuer une liaison avec les résultats d'une requête LINQ"
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 70f4b439d231d69e5671216bc4e62d0789ce66c7
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920136"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a><span data-ttu-id="c606e-102">Comment : effectuer une liaison avec les résultats d'une requête LINQ</span><span class="sxs-lookup"><span data-stu-id="c606e-102">How to: Bind to the Results of a LINQ Query</span></span>

<span data-ttu-id="c606e-103">Cet exemple montre comment exécuter une requête LINQ, puis établir une liaison avec les résultats.</span><span class="sxs-lookup"><span data-stu-id="c606e-103">This example demonstrates how to run a LINQ query and then bind to the results.</span></span>

## <a name="example"></a><span data-ttu-id="c606e-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="c606e-104">Example</span></span>

<span data-ttu-id="c606e-105">L’exemple suivant crée deux zones de liste.</span><span class="sxs-lookup"><span data-stu-id="c606e-105">The following example creates two list boxes.</span></span> <span data-ttu-id="c606e-106">La première zone de liste contient trois éléments de liste.</span><span class="sxs-lookup"><span data-stu-id="c606e-106">The first list box contains three list items.</span></span>

[!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]

<span data-ttu-id="c606e-107">La sélection d’un élément de la première zone de liste appelle le gestionnaire d’événements suivant.</span><span class="sxs-lookup"><span data-stu-id="c606e-107">Selecting an item from the first list box invokes the following event handler.</span></span> <span data-ttu-id="c606e-108">Dans cet exemple, `Tasks` est une collection d’objets `Task`.</span><span class="sxs-lookup"><span data-stu-id="c606e-108">In this example, `Tasks` is a collection of `Task` objects.</span></span> <span data-ttu-id="c606e-109">La classe `Task` a une propriété nommée `Priority`.</span><span class="sxs-lookup"><span data-stu-id="c606e-109">The `Task` class has a property named `Priority`.</span></span> <span data-ttu-id="c606e-110">Ce gestionnaire d’événements exécute une requête LINQ qui retourne la collection d’objets `Task` ayant la valeur de priorité sélectionnée, puis le définit comme <xref:System.Windows.FrameworkElement.DataContext%2A>:</span><span class="sxs-lookup"><span data-stu-id="c606e-110">This event handler runs a LINQ query that returns the collection of `Task` objects that have the selected priority value, and then sets that as the <xref:System.Windows.FrameworkElement.DataContext%2A>:</span></span>

[!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]

<span data-ttu-id="c606e-111">La deuxième zone de liste est liée à cette collection, car sa valeur <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> est définie sur `{Binding}`.</span><span class="sxs-lookup"><span data-stu-id="c606e-111">The second list box binds to that collection because its <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> value is set to `{Binding}`.</span></span> <span data-ttu-id="c606e-112">En conséquence, il affiche la collection retournée (selon le `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span><span class="sxs-lookup"><span data-stu-id="c606e-112">As a result, it displays the returned collection (based on the `myTaskTemplate` <xref:System.Windows.DataTemplate>).</span></span>

## <a name="see-also"></a><span data-ttu-id="c606e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c606e-113">See also</span></span>

- [<span data-ttu-id="c606e-114">Rendre des données disponibles pour la liaison en XAML</span><span class="sxs-lookup"><span data-stu-id="c606e-114">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
- [<span data-ttu-id="c606e-115">Effectuer une liaison à une collection et afficher des informations basées sur la sélection</span><span class="sxs-lookup"><span data-stu-id="c606e-115">Bind to a Collection and Display Information Based on Selection</span></span>](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [<span data-ttu-id="c606e-116">Nouveautés de WPF version 4.5</span><span class="sxs-lookup"><span data-stu-id="c606e-116">What's New in WPF Version 4.5</span></span>](../getting-started/whats-new.md)
- [<span data-ttu-id="c606e-117">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="c606e-117">Data Binding Overview</span></span>](data-binding-overview.md)
