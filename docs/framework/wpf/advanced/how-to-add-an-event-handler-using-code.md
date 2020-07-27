---
title: "Comment : ajouter un gestionnaire d'événements à l'aide de code"
description: Utilisez cet exemple pour apprendre à ajouter un gestionnaire d’événements à un élément dans Windows Presentation Foundation à l’aide de code, au lieu de le déclarer à l’aide de XAML.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: b36969f7a65ccbf6c9d03b22767d9eacdc177ad1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166366"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="1d7e9-103">Comment : ajouter un gestionnaire d'événements à l'aide de code</span><span class="sxs-lookup"><span data-stu-id="1d7e9-103">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="1d7e9-104">Cet exemple montre comment ajouter un gestionnaire d’événements à un élément à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="1d7e9-104">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="1d7e9-105">Si vous souhaitez ajouter un gestionnaire d’événements à un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] élément et que la page de balisage qui contient l’élément a déjà été chargée, vous devez ajouter le gestionnaire à l’aide du code.</span><span class="sxs-lookup"><span data-stu-id="1d7e9-105">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="1d7e9-106">Si vous développez l’arborescence d’éléments pour une application entièrement à l’aide de code sans déclarer d’éléments à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , vous pouvez également appeler des méthodes spécifiques pour ajouter des gestionnaires d’événements à l’arborescence d’éléments construite.</span><span class="sxs-lookup"><span data-stu-id="1d7e9-106">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d7e9-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="1d7e9-107">Example</span></span>  
 <span data-ttu-id="1d7e9-108">L’exemple suivant ajoute un nouveau <xref:System.Windows.Controls.Button> à une page existante définie initialement dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1d7e9-108">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="1d7e9-109">Un fichier code-behind implémente une méthode de gestionnaire d’événements, puis ajoute cette méthode en tant que nouveau gestionnaire d’événements sur <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="1d7e9-109">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="1d7e9-110">L’exemple C# utilise l' `+=` opérateur pour assigner un gestionnaire à un événement.</span><span class="sxs-lookup"><span data-stu-id="1d7e9-110">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="1d7e9-111">Il s’agit du même opérateur que celui utilisé pour assigner un gestionnaire dans le modèle de gestion des événements common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1d7e9-111">This is the same operator that is used to assign a handler in the common language runtime (CLR) event handling model.</span></span> <span data-ttu-id="1d7e9-112">Microsoft Visual Basic ne prend pas en charge cet opérateur comme un moyen d’ajouter des gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="1d7e9-112">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="1d7e9-113">Au lieu de cela, elle nécessite l’une des deux techniques suivantes :</span><span class="sxs-lookup"><span data-stu-id="1d7e9-113">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="1d7e9-114">Utilisez la <xref:System.Windows.UIElement.AddHandler%2A> méthode avec un `AddressOf` opérateur pour référencer l’implémentation du gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="1d7e9-114">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="1d7e9-115">Utilisez le `Handles` mot clé dans le cadre de la définition du gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="1d7e9-115">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="1d7e9-116">Cette technique n’est pas illustrée ici ; consultez [Visual Basic et gestion des événements WPF](visual-basic-and-wpf-event-handling.md).</span><span class="sxs-lookup"><span data-stu-id="1d7e9-116">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> <span data-ttu-id="1d7e9-117">L’ajout d’un gestionnaire d’événements dans la page initialement analysée [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] est bien plus simple.</span><span class="sxs-lookup"><span data-stu-id="1d7e9-117">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="1d7e9-118">Dans l’élément objet où vous souhaitez ajouter le gestionnaire d’événements, ajoutez un attribut qui correspond au nom de l’événement que vous souhaitez gérer.</span><span class="sxs-lookup"><span data-stu-id="1d7e9-118">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="1d7e9-119">Spécifiez ensuite la valeur de cet attribut comme nom de la méthode de gestionnaire d’événements que vous avez définie dans le fichier code-behind de la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span><span class="sxs-lookup"><span data-stu-id="1d7e9-119">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="1d7e9-120">Pour plus d’informations, consultez vue d’ensemble [du langage XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md) ou [vue d’ensemble des événements routés](routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1d7e9-120">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d7e9-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1d7e9-121">See also</span></span>

- [<span data-ttu-id="1d7e9-122">Vue d'ensemble des événements routés</span><span class="sxs-lookup"><span data-stu-id="1d7e9-122">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="1d7e9-123">Rubriques Comment</span><span class="sxs-lookup"><span data-stu-id="1d7e9-123">How-to Topics</span></span>](events-how-to-topics.md)
