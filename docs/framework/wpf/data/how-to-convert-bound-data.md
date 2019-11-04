---
title: 'Comment : convertir des données liées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- converting [WPF], bound data
- data binding [WPF], converting bound data
- binding data [WPF], converting bound data
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
ms.openlocfilehash: f9ad390626092d481bf47f017f643a29302c1b29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458859"
---
# <a name="how-to-convert-bound-data"></a><span data-ttu-id="4d029-102">Comment : convertir des données liées</span><span class="sxs-lookup"><span data-stu-id="4d029-102">How to: Convert Bound Data</span></span>
<span data-ttu-id="4d029-103">Cet exemple montre comment appliquer la conversion aux données utilisées dans les liaisons.</span><span class="sxs-lookup"><span data-stu-id="4d029-103">This example shows how to apply conversion to data that is used in bindings.</span></span>  
  
 <span data-ttu-id="4d029-104">Pour convertir des données pendant une liaison, vous devez créer une classe qui implémente l’interface <xref:System.Windows.Data.IValueConverter>, qui comprend les méthodes <xref:System.Windows.Data.IValueConverter.Convert%2A> et <xref:System.Windows.Data.IValueConverter.ConvertBack%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d029-104">To convert data during binding, you must create a class that implements the <xref:System.Windows.Data.IValueConverter> interface, which includes the <xref:System.Windows.Data.IValueConverter.Convert%2A> and <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d029-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d029-105">Example</span></span>  
 <span data-ttu-id="4d029-106">L’exemple suivant illustre l’implémentation d’un convertisseur de dates qui convertit la valeur de date passée afin qu’elle affiche uniquement l’année, le mois et le jour.</span><span class="sxs-lookup"><span data-stu-id="4d029-106">The following example shows the implementation of a date converter that converts the date value passed in so that it only shows the year, the month, and the day.</span></span> <span data-ttu-id="4d029-107">Lors de l’implémentation de l’interface <xref:System.Windows.Data.IValueConverter>, il est recommandé de décorer l’implémentation avec un attribut <xref:System.Windows.Data.ValueConversionAttribute> pour indiquer aux outils de développement les types de données impliqués dans la conversion, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4d029-107">When implementing the <xref:System.Windows.Data.IValueConverter> interface, it is a good practice to decorate the implementation with a <xref:System.Windows.Data.ValueConversionAttribute> attribute to indicate to development tools the data types involved in the conversion, as in the following example:</span></span>  
  
 [!code-csharp[DataBindingLab#18](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 <span data-ttu-id="4d029-108">Une fois que vous avez créé un convertisseur, vous pouvez l’ajouter en tant que ressource dans votre fichier [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4d029-108">Once you have created a converter, you can add it as a resource in your [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file.</span></span> <span data-ttu-id="4d029-109">Dans l’exemple suivant, *src* est mappé à l’espace de noms dans lequel *DateConverter* est défini.</span><span class="sxs-lookup"><span data-stu-id="4d029-109">In the following example, *src* maps to the namespace in which *DateConverter* is defined.</span></span>  
  
 [!code-xaml[DataBindingLab#15](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 <span data-ttu-id="4d029-110">Enfin, vous pouvez utiliser le convertisseur dans votre liaison à l’aide de la syntaxe suivante.</span><span class="sxs-lookup"><span data-stu-id="4d029-110">Finally, you can use the converter in your binding using the following syntax.</span></span> <span data-ttu-id="4d029-111">Dans l’exemple suivant, le contenu de texte de l' <xref:System.Windows.Controls.TextBlock> est lié à *StartDate*, qui est une propriété d’une source de données externe.</span><span class="sxs-lookup"><span data-stu-id="4d029-111">In the following example, the text content of the <xref:System.Windows.Controls.TextBlock> is bound to *StartDate*, which is a property of an external data source.</span></span>  
  
 [!code-xaml[DataBindingLab#17](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 <span data-ttu-id="4d029-112">Les ressources de style référencées dans l’exemple ci-dessus sont définies dans une section de ressource non présentée dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="4d029-112">The style resources referenced in the above example are defined in a resource section not shown in this topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d029-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d029-113">See also</span></span>

- [<span data-ttu-id="4d029-114">Implémenter la validation de la liaison</span><span class="sxs-lookup"><span data-stu-id="4d029-114">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="4d029-115">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="4d029-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="4d029-116">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="4d029-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
