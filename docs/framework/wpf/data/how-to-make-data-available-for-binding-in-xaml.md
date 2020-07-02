---
title: 'Comment : rendre des données disponibles pour la liaison en XAML'
description: Découvrez les différentes façons dont vous pouvez rendre les données disponibles en fonction des besoins de votre application dans Windows Presentation Foundation (WPF).
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 16618ce8b19f5dd5854c4d126e7fc455f0428a28
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620792"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="14280-103">Comment : rendre des données disponibles pour la liaison en XAML</span><span class="sxs-lookup"><span data-stu-id="14280-103">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="14280-104">Cette rubrique décrit les différentes façons dont vous pouvez rendre les données disponibles pour [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] la liaison dans, en fonction des besoins de votre application.</span><span class="sxs-lookup"><span data-stu-id="14280-104">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14280-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="14280-105">Example</span></span>  
 <span data-ttu-id="14280-106">Si vous avez un objet common language runtime (CLR) à partir duquel vous souhaitez établir une liaison [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , vous pouvez rendre l’objet disponible pour la liaison pour le définir en tant que ressource et lui donner un `x:Key` .</span><span class="sxs-lookup"><span data-stu-id="14280-106">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="14280-107">Dans l’exemple suivant, vous avez un `Person` objet avec une propriété de chaîne nommée `PersonName` .</span><span class="sxs-lookup"><span data-stu-id="14280-107">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="14280-108">L' `Person` objet (dans la ligne affichée en surbrillance qui contient l' `<src>` élément) est défini dans l’espace de noms appelé `SDKSample` .</span><span class="sxs-lookup"><span data-stu-id="14280-108">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="14280-109">Vous pouvez ensuite lier le <xref:System.Windows.Controls.TextBlock> contrôle à l’objet dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , comme le montre la ligne en surbrillance qui contient l' `<TextBlock>` élément.</span><span class="sxs-lookup"><span data-stu-id="14280-109">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span>
  
 <span data-ttu-id="14280-110">Vous pouvez également utiliser la <xref:System.Windows.Data.ObjectDataProvider> classe, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="14280-110">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="14280-111">Vous définissez la liaison de la même façon, car la ligne mise en surbrillance qui contient l' `<TextBlock>` élément s’affiche.</span><span class="sxs-lookup"><span data-stu-id="14280-111">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="14280-112">Dans cet exemple, le résultat est le même : vous avez un <xref:System.Windows.Controls.TextBlock> avec le contenu de texte `Joe` .</span><span class="sxs-lookup"><span data-stu-id="14280-112">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="14280-113">Toutefois, la <xref:System.Windows.Data.ObjectDataProvider> classe fournit des fonctionnalités telles que la possibilité de créer une liaison avec le résultat d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="14280-113">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="14280-114">Vous pouvez choisir d’utiliser la <xref:System.Windows.Data.ObjectDataProvider> classe si vous avez besoin des fonctionnalités qu’elle fournit.</span><span class="sxs-lookup"><span data-stu-id="14280-114">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="14280-115">Toutefois, si vous effectuez une liaison à un objet qui a déjà été créé, vous devez définir `DataContext` dans le code, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="14280-115">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="14280-116">Pour accéder aux données XML pour la liaison à l’aide de la <xref:System.Windows.Data.XmlDataProvider> classe, consultez [lier aux données XML à l’aide d’un XMLDataProvider et de requêtes XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="14280-116">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="14280-117">Pour accéder aux données XML pour la liaison à l’aide de la <xref:System.Windows.Data.ObjectDataProvider> classe, consultez les résultats de la [requête bind to XDocument, XELEMENT ou LINQ for XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="14280-117">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="14280-118">Pour plus d’informations sur les différentes façons de spécifier les données que vous liez, consultez [spécifier la source de liaison](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="14280-118">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="14280-119">Pour plus d’informations sur les types de données que vous pouvez lier ou sur la façon d’implémenter vos propres objets common language runtime (CLR) pour la liaison, consultez [vue d’ensemble des sources de liaison](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="14280-119">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14280-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14280-120">See also</span></span>

- [<span data-ttu-id="14280-121">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="14280-121">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="14280-122">Rubriques de procédures</span><span class="sxs-lookup"><span data-stu-id="14280-122">How-to Topics</span></span>](data-binding-how-to-topics.md)
