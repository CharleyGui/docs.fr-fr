---
title: "Comment : produire une valeur en fonction d'une liste d'éléments liés"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], MultiBinding
- Multibinding [WPF]
ms.assetid: b3d06378-b511-4181-95aa-316d60c9229b
ms.openlocfilehash: da183a34eb85de54b1e3f54f8d14c09e25640165
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459697"
---
# <a name="how-to-produce-a-value-based-on-a-list-of-bound-items"></a><span data-ttu-id="07336-102">Comment : produire une valeur en fonction d'une liste d'éléments liés</span><span class="sxs-lookup"><span data-stu-id="07336-102">How to: Produce a Value Based on a List of Bound Items</span></span>
<span data-ttu-id="07336-103"><xref:System.Windows.Data.MultiBinding> vous permet de lier une propriété de cible de liaison à une liste de propriétés sources, puis d’appliquer une logique pour produire une valeur avec les entrées données.</span><span class="sxs-lookup"><span data-stu-id="07336-103"><xref:System.Windows.Data.MultiBinding> allows you to bind a binding target property to a list of source properties and then apply logic to produce a value with the given inputs.</span></span> <span data-ttu-id="07336-104">Cet exemple montre comment utiliser <xref:System.Windows.Data.MultiBinding>.</span><span class="sxs-lookup"><span data-stu-id="07336-104">This example demonstrates how to use <xref:System.Windows.Data.MultiBinding>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07336-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="07336-105">Example</span></span>  
 <span data-ttu-id="07336-106">Dans l’exemple suivant, `NameListData` fait référence à une collection d’objets `PersonName`, qui sont des objets contenant deux propriétés, `firstName` et `lastName`.</span><span class="sxs-lookup"><span data-stu-id="07336-106">In the following example, `NameListData` refers to a collection of `PersonName` objects, which are objects that contain two properties, `firstName` and `lastName`.</span></span> <span data-ttu-id="07336-107">L’exemple suivant produit une <xref:System.Windows.Controls.TextBlock> qui affiche le prénom et le nom d’une personne avec le nom de famille en premier.</span><span class="sxs-lookup"><span data-stu-id="07336-107">The following example produces a <xref:System.Windows.Controls.TextBlock> that shows the first and last names of a person with the last name first.</span></span>  
  
 [!code-xaml[MultiBinding#Resources1](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources1)]  
[!code-xaml[MultiBinding#Resources2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
[!code-xaml[MultiBinding#MultiBindingTextBox2](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindingtextbox2)]  
[!code-xaml[MultiBinding#Window](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#window)]  
  
 <span data-ttu-id="07336-108">Pour comprendre comment est généré le format nom-prénom, jetons un œil à l’implémentation du `NameConverter` :</span><span class="sxs-lookup"><span data-stu-id="07336-108">To understand how the last-name-first format is produced, let's take a look at the implementation of the `NameConverter`:</span></span>  
  
 [!code-csharp[MultiBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/NameConverter.cs#3)]
 [!code-vb[MultiBinding#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameConverter.vb#3)]  
  
 <span data-ttu-id="07336-109">`NameConverter` implémente l'interface <xref:System.Windows.Data.IMultiValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="07336-109">`NameConverter` implements the <xref:System.Windows.Data.IMultiValueConverter> interface.</span></span> <span data-ttu-id="07336-110">`NameConverter` prend les valeurs des liaisons individuelles et les stocke dans le tableau d’objets de valeurs.</span><span class="sxs-lookup"><span data-stu-id="07336-110">`NameConverter` takes the values from the individual bindings and stores them in the values object array.</span></span> <span data-ttu-id="07336-111">L’ordre dans lequel les éléments de <xref:System.Windows.Data.Binding> apparaissent sous l’élément <xref:System.Windows.Data.MultiBinding> est l’ordre dans lequel ces valeurs sont stockées dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="07336-111">The order in which the <xref:System.Windows.Data.Binding> elements appear under the <xref:System.Windows.Data.MultiBinding> element is the order in which those values are stored in the array.</span></span> <span data-ttu-id="07336-112">La valeur de l’attribut <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> est référencée par l’argument de paramètre de la méthode <xref:System.Windows.Data.MultiBinding.Converter%2A>, qui exécute un commutateur sur le paramètre pour déterminer comment mettre en forme le nom.</span><span class="sxs-lookup"><span data-stu-id="07336-112">The value of the <xref:System.Windows.Data.MultiBinding.ConverterParameter%2A> attribute is referenced by the parameter argument of the <xref:System.Windows.Data.MultiBinding.Converter%2A> method, which performs a switch on the parameter to determine how to format the name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07336-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07336-113">See also</span></span>

- [<span data-ttu-id="07336-114">Convertir des données liées</span><span class="sxs-lookup"><span data-stu-id="07336-114">Convert Bound Data</span></span>](how-to-convert-bound-data.md)
- [<span data-ttu-id="07336-115">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="07336-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="07336-116">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="07336-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
