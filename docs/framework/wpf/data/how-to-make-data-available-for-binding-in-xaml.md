---
title: 'Procédure : Rendre des données disponibles pour la liaison en XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 3487a160cc49ab6b779a20157668915c2da33900
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401496"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="97917-102">Procédure : Rendre des données disponibles pour la liaison en XAML</span><span class="sxs-lookup"><span data-stu-id="97917-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="97917-103">Cette rubrique décrit les différentes façons dont vous pouvez rendre les données disponibles pour [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]la liaison dans, en fonction des besoins de votre application.</span><span class="sxs-lookup"><span data-stu-id="97917-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97917-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="97917-104">Example</span></span>  
 <span data-ttu-id="97917-105">Si vous avez un objet Common Language Runtime (CLR) à partir duquel [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]vous souhaitez établir une liaison, vous pouvez rendre l’objet disponible pour la liaison pour le définir en tant que ressource et lui donner un. `x:Key`</span><span class="sxs-lookup"><span data-stu-id="97917-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="97917-106">Dans l’exemple suivant, vous avez un `Person` objet avec une propriété de chaîne `PersonName`nommée.</span><span class="sxs-lookup"><span data-stu-id="97917-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="97917-107">L' `Person` objet (dans la ligne affichée en surbrillance `<src>` qui contient l’élément) est défini dans `SDKSample`l’espace de noms appelé.</span><span class="sxs-lookup"><span data-stu-id="97917-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="97917-108">Vous pouvez ensuite lier le <xref:System.Windows.Controls.TextBlock> contrôle à l’objet dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], comme le montre la ligne en surbrillance qui contient l' `<TextBlock>` élément.</span><span class="sxs-lookup"><span data-stu-id="97917-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span> 
  
 <span data-ttu-id="97917-109">Vous pouvez également utiliser la <xref:System.Windows.Data.ObjectDataProvider> classe, comme dans l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="97917-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="97917-110">Vous définissez la liaison de la même façon, car la ligne mise en surbrillance qui contient l' `<TextBlock>` élément s’affiche.</span><span class="sxs-lookup"><span data-stu-id="97917-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="97917-111">Dans cet exemple, le résultat est le même: vous avez un <xref:System.Windows.Controls.TextBlock> avec le contenu `Joe`de texte.</span><span class="sxs-lookup"><span data-stu-id="97917-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="97917-112">Toutefois, la <xref:System.Windows.Data.ObjectDataProvider> classe fournit des fonctionnalités telles que la possibilité de créer une liaison avec le résultat d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="97917-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="97917-113">Vous pouvez choisir d’utiliser la <xref:System.Windows.Data.ObjectDataProvider> classe si vous avez besoin des fonctionnalités qu’elle fournit.</span><span class="sxs-lookup"><span data-stu-id="97917-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="97917-114">Toutefois, si vous effectuez une liaison à un objet qui a déjà été créé, vous devez définir dans `DataContext` le code, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="97917-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="97917-115">Pour accéder [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] aux données pour la liaison <xref:System.Windows.Data.XmlDataProvider> à l’aide de la classe, consultez [lier aux données XML à l’aide d’un XMLDataProvider et de requêtes XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="97917-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="97917-116">Pour accéder [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] aux données pour la liaison <xref:System.Windows.Data.ObjectDataProvider> à l’aide de la classe, consultez les résultats de la [requête bind to XDocument, XElement ou LINQ for XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="97917-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="97917-117">Pour plus d’informations sur les différentes façons de spécifier les données que vous liez, consultez [spécifier la source de liaison](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="97917-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="97917-118">Pour plus d’informations sur les types de données que vous pouvez lier ou sur la façon d’implémenter vos propres objets common language runtime (CLR) pour la liaison, consultez [vue d’ensemble des sources de liaison](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="97917-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97917-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97917-119">See also</span></span>

- [<span data-ttu-id="97917-120">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="97917-120">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="97917-121">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="97917-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
