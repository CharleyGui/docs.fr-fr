---
title: 'Comment : utiliser SelectedValue, SelectedValuePath et SelectedItem'
description: Découvrez comment utiliser les propriétés SelectedValue et SelectedValuePath pour spécifier une valeur pour le SelectedItem d’un Windows Presentation Foundation TreeView.
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: ddac2455dee0bf69d25307340eddd5364e43e823
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166278"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a><span data-ttu-id="81306-103">Comment : utiliser SelectedValue, SelectedValuePath et SelectedItem</span><span class="sxs-lookup"><span data-stu-id="81306-103">How to: Use SelectedValue, SelectedValuePath, and SelectedItem</span></span>
<span data-ttu-id="81306-104">Cet exemple montre comment utiliser les <xref:System.Windows.Controls.TreeView.SelectedValue%2A> Propriétés et <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> pour spécifier une valeur pour le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> d’un <xref:System.Windows.Controls.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="81306-104">This example shows how to use the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> and <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> properties to specify a value for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> of a <xref:System.Windows.Controls.TreeView>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81306-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="81306-105">Example</span></span>  
 <span data-ttu-id="81306-106">La <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriété fournit un moyen de spécifier un <xref:System.Windows.Controls.TreeView.SelectedValue%2A> pour le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> dans un <xref:System.Windows.Controls.TreeView> .</span><span class="sxs-lookup"><span data-stu-id="81306-106">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property provides a way to specify a <xref:System.Windows.Controls.TreeView.SelectedValue%2A> for the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> in a <xref:System.Windows.Controls.TreeView>.</span></span> <span data-ttu-id="81306-107">Le <xref:System.Windows.Controls.TreeView.SelectedItem%2A> représente un objet dans la <xref:System.Windows.Controls.ItemsControl.Items%2A> collection et le <xref:System.Windows.Controls.TreeView> affiche la valeur d’une propriété unique de l’élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="81306-107">The <xref:System.Windows.Controls.TreeView.SelectedItem%2A> represents an object in the <xref:System.Windows.Controls.ItemsControl.Items%2A> collection and the <xref:System.Windows.Controls.TreeView> displays the value of a single property of the selected item.</span></span> <span data-ttu-id="81306-108">La <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> propriété spécifie le chemin d’accès à la propriété qui est utilisée pour déterminer la valeur de la <xref:System.Windows.Controls.TreeView.SelectedValue%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="81306-108">The <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> property specifies the path to the property that is used to determine the value of the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property.</span></span> <span data-ttu-id="81306-109">Les exemples de cette rubrique illustrent ce concept.</span><span class="sxs-lookup"><span data-stu-id="81306-109">The examples in this topic illustrate this concept.</span></span>  
  
 <span data-ttu-id="81306-110">L’exemple suivant montre un <xref:System.Windows.Data.XmlDataProvider> qui contient des informations sur les employés.</span><span class="sxs-lookup"><span data-stu-id="81306-110">The following example shows an <xref:System.Windows.Data.XmlDataProvider> that contains employee information.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 <span data-ttu-id="81306-111">L’exemple suivant définit un <xref:System.Windows.HierarchicalDataTemplate> qui affiche les `EmployeeName` et `EmployeeWorkDay` de `Employee` .</span><span class="sxs-lookup"><span data-stu-id="81306-111">The following example defines a <xref:System.Windows.HierarchicalDataTemplate> that displays the `EmployeeName` and `EmployeeWorkDay` of the `Employee`.</span></span> <span data-ttu-id="81306-112">Notez que le <xref:System.Windows.HierarchicalDataTemplate> ne spécifie pas le dans le cadre `EmployeeNumber` du modèle.</span><span class="sxs-lookup"><span data-stu-id="81306-112">Note that the <xref:System.Windows.HierarchicalDataTemplate> does not specify the `EmployeeNumber` as part of the template.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 <span data-ttu-id="81306-113">L’exemple suivant montre un <xref:System.Windows.Controls.TreeView> qui utilise le précédemment défini <xref:System.Windows.HierarchicalDataTemplate> et qui affecte <xref:System.Windows.Controls.TreeView.SelectedValue%2A> la valeur à la propriété `EmployeeNumber` .</span><span class="sxs-lookup"><span data-stu-id="81306-113">The following example shows a <xref:System.Windows.Controls.TreeView> that uses the previously defined <xref:System.Windows.HierarchicalDataTemplate> and that sets the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> property to the `EmployeeNumber`.</span></span> <span data-ttu-id="81306-114">Lorsque vous sélectionnez un `EmployeeName` dans le <xref:System.Windows.Controls.TreeView> , la <xref:System.Windows.Controls.TreeView.SelectedItem%2A> propriété retourne l' `EmployeeInfo` élément de données qui correspond au sélectionné `EmployeeName` .</span><span class="sxs-lookup"><span data-stu-id="81306-114">When you select an `EmployeeName` in the <xref:System.Windows.Controls.TreeView>, the <xref:System.Windows.Controls.TreeView.SelectedItem%2A> property returns the `EmployeeInfo` data item that corresponds to the selected `EmployeeName`.</span></span> <span data-ttu-id="81306-115">Toutefois, étant donné que a la <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> <xref:System.Windows.Controls.TreeView> valeur `EmployeeNumber` , le a la <xref:System.Windows.Controls.TreeView.SelectedValue%2A> valeur `EmployeeNumber` .</span><span class="sxs-lookup"><span data-stu-id="81306-115">However, because the <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> of this <xref:System.Windows.Controls.TreeView> is set to `EmployeeNumber`, the <xref:System.Windows.Controls.TreeView.SelectedValue%2A> is set to the `EmployeeNumber`.</span></span>  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a><span data-ttu-id="81306-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81306-116">See also</span></span>

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [<span data-ttu-id="81306-117">Vue d'ensemble de TreeView</span><span class="sxs-lookup"><span data-stu-id="81306-117">TreeView Overview</span></span>](treeview-overview.md)
- [<span data-ttu-id="81306-118">Rubriques Comment</span><span class="sxs-lookup"><span data-stu-id="81306-118">How-to Topics</span></span>](treeview-how-to-topics.md)
