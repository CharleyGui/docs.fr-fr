---
title: 'Comment : rendre des données disponibles pour la liaison en XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 97e878e4932ca9122bf27f76c32d1a56e69f253a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740609"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="03119-102">Comment : rendre des données disponibles pour la liaison en XAML</span><span class="sxs-lookup"><span data-stu-id="03119-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="03119-103">Cette rubrique décrit les différentes façons dont vous pouvez rendre les données disponibles pour la liaison dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], selon les besoins de votre application.</span><span class="sxs-lookup"><span data-stu-id="03119-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03119-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="03119-104">Example</span></span>  
 <span data-ttu-id="03119-105">Si vous souhaitez lier un objet common language runtime (CLR) à partir de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez rendre l’objet disponible pour la liaison pour le définir en tant que ressource et lui donner un `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="03119-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="03119-106">Dans l’exemple suivant, vous avez un objet `Person` avec une propriété de chaîne nommée `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="03119-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="03119-107">L’objet `Person` (dans la ligne affichée en surbrillance qui contient l’élément `<src>`) est défini dans l’espace de noms appelé `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="03119-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="03119-108">Vous pouvez ensuite lier le contrôle <xref:System.Windows.Controls.TextBlock> à l’objet dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], comme le montre la ligne mise en surbrillance qui contient l’élément `<TextBlock>`.</span><span class="sxs-lookup"><span data-stu-id="03119-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="03119-109">Vous pouvez également utiliser la classe <xref:System.Windows.Data.ObjectDataProvider>, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="03119-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="03119-110">Vous définissez la liaison de la même façon, car la ligne mise en surbrillance qui contient l’élément `<TextBlock>` s’affiche.</span><span class="sxs-lookup"><span data-stu-id="03119-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="03119-111">Dans cet exemple, le résultat est le même : vous avez un <xref:System.Windows.Controls.TextBlock> avec le contenu de texte `Joe`.</span><span class="sxs-lookup"><span data-stu-id="03119-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="03119-112">Toutefois, la classe <xref:System.Windows.Data.ObjectDataProvider> fournit des fonctionnalités telles que la possibilité d’effectuer une liaison au résultat d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="03119-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="03119-113">Vous pouvez choisir d’utiliser la classe <xref:System.Windows.Data.ObjectDataProvider> si vous avez besoin des fonctionnalités qu’elle fournit.</span><span class="sxs-lookup"><span data-stu-id="03119-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="03119-114">Toutefois, si vous effectuez une liaison à un objet qui a déjà été créé, vous devez définir la `DataContext` dans le code, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="03119-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="03119-115">Pour accéder aux données XML à des fins de liaison à l’aide de la classe <xref:System.Windows.Data.XmlDataProvider>, consultez [lier à des données XML à l’aide d’un XMLDataProvider et de requêtes XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="03119-115">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="03119-116">Pour accéder aux données XML pour la liaison à l’aide de la classe <xref:System.Windows.Data.ObjectDataProvider>, consultez [lier aux résultats de requête de type XDocument, XElement ou LINQ for XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="03119-116">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="03119-117">Pour plus d’informations sur les différentes façons de spécifier les données que vous liez, consultez [spécifier la source de liaison](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="03119-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="03119-118">Pour plus d’informations sur les types de données que vous pouvez lier ou sur la façon d’implémenter vos propres objets common language runtime (CLR) pour la liaison, consultez [vue d’ensemble des sources de liaison](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="03119-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03119-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03119-119">See also</span></span>

- [<span data-ttu-id="03119-120">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="03119-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="03119-121">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="03119-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
