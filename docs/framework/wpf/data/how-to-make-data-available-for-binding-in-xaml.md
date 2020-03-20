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
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174184"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="4db75-102">Comment : rendre des données disponibles pour la liaison en XAML</span><span class="sxs-lookup"><span data-stu-id="4db75-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="4db75-103">Ce sujet traite de différentes façons dont [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]vous pouvez rendre les données disponibles pour la liaison, en fonction des besoins de votre application.</span><span class="sxs-lookup"><span data-stu-id="4db75-103">This topic discusses various ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4db75-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="4db75-104">Example</span></span>  
 <span data-ttu-id="4db75-105">Si vous avez un terme de langage commun (CLR) [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]objet que vous souhaitez lier à partir de , une `x:Key`façon que vous pouvez rendre l’objet disponible pour la liaison est de le définir comme une ressource et lui donner un .</span><span class="sxs-lookup"><span data-stu-id="4db75-105">If you have a common language runtime (CLR) object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="4db75-106">Dans l’exemple suivant, `Person` vous avez un `PersonName`objet avec une propriété à cordes nommée .</span><span class="sxs-lookup"><span data-stu-id="4db75-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="4db75-107">L’objet `Person` (dans la ligne `<src>` indiquée sur laquelle contient `SDKSample`l’élément) est défini dans l’espace nom appelé .</span><span class="sxs-lookup"><span data-stu-id="4db75-107">The `Person` object (in the line shown highlighted that contains the `<src>` element) is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <span data-ttu-id="4db75-108">Vous pouvez ensuite <xref:System.Windows.Controls.TextBlock> lier le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]contrôle à l’objet `<TextBlock>` en , comme le montre la ligne surlignée qui contient l’élément.</span><span class="sxs-lookup"><span data-stu-id="4db75-108">You can then bind the <xref:System.Windows.Controls.TextBlock> control to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as the highlighted line that contains the `<TextBlock>` element shows.</span></span>
  
 <span data-ttu-id="4db75-109">Alternativement, vous pouvez <xref:System.Windows.Data.ObjectDataProvider> utiliser la classe, comme dans l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="4db75-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example:</span></span>  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 <span data-ttu-id="4db75-110">Vous définissez la liaison de la même `<TextBlock>` manière, comme le montre la ligne surlignée qui contient l’élément.</span><span class="sxs-lookup"><span data-stu-id="4db75-110">You define the binding the same way, as the highlighted line that contains the `<TextBlock>` element shows.</span></span>  
  
 <span data-ttu-id="4db75-111">Dans cet exemple particulier, le résultat est <xref:System.Windows.Controls.TextBlock> le même `Joe`: vous avez un contenu texte avec.</span><span class="sxs-lookup"><span data-stu-id="4db75-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="4db75-112">Cependant, <xref:System.Windows.Data.ObjectDataProvider> la classe fournit des fonctionnalités telles que la capacité de se lier au résultat d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="4db75-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="4db75-113">Vous pouvez choisir <xref:System.Windows.Data.ObjectDataProvider> d’utiliser la classe si vous avez besoin de la fonctionnalité qu’il fournit.</span><span class="sxs-lookup"><span data-stu-id="4db75-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="4db75-114">Toutefois, si vous êtes contraignant à un objet qui a `DataContext` déjà été créé, vous devez définir le code, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4db75-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="4db75-115">Pour accéder aux données XML pour la liaison à l’aide de la <xref:System.Windows.Data.XmlDataProvider> classe, voir Bind to [XML Data Using an XMLDataProvider et XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="4db75-115">To access XML data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="4db75-116">Pour accéder aux données XML pour la liaison à l’aide de la <xref:System.Windows.Data.ObjectDataProvider> classe, voir Bind to [XDocument, XElement ou LINQ pour les résultats de requête XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="4db75-116">To access XML data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="4db75-117">Pour plus d’informations sur de nombreuses façons dont vous pouvez spécifier les données que vous êtes contraignant, voir [Spécifier la source contraignante](how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="4db75-117">For information about many ways you can specify the data you are binding to, see [Specify the Binding Source](how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="4db75-118">Pour plus d’informations sur les types de données que vous pouvez lier à ou comment mettre en œuvre vos propres objets de temps d’exécution de langue commune (CLR) pour la liaison, voir [Binding Sources Overview](binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4db75-118">For information about what types of data you can bind to or how to implement your own common language runtime (CLR) objects for binding, see [Binding Sources Overview](binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db75-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4db75-119">See also</span></span>

- [<span data-ttu-id="4db75-120">Aperçu de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="4db75-120">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="4db75-121">Sujets comment se passer</span><span class="sxs-lookup"><span data-stu-id="4db75-121">How-to Topics</span></span>](data-binding-how-to-topics.md)
