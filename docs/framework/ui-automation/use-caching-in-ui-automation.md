---
title: Utiliser la mise en cache dans UI Automation
description: Découvrez comment utiliser la mise en cache dans UI Automation. Passez en revue les étapes permettant d’activer une requête de cache, de mettre en cache des propriétés AutomationElement et d’obtenir des modèles mis en cache.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: f99fb724130c359a77c72db66dd9f837ef1a2219
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258606"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="2ff20-104">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="2ff20-104">Use Caching in UI Automation</span></span>

> [!NOTE]
> <span data-ttu-id="2ff20-105">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="2ff20-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="2ff20-106">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="2ff20-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="2ff20-107">Cette section montre comment implémenter la mise en cache des propriétés <xref:System.Windows.Automation.AutomationElement> et des modèles de contrôle.</span><span class="sxs-lookup"><span data-stu-id="2ff20-107">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="2ff20-108">Activer une requête de Cache</span><span class="sxs-lookup"><span data-stu-id="2ff20-108">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="2ff20-109">Créez un <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="2ff20-109">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="2ff20-110">Spécifiez les propriétés et les modèles à mettre en cache à l’aide de la méthode <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="2ff20-110">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="2ff20-111">Spécifiez la portée de la mise en cache en définissant la propriété <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> .</span><span class="sxs-lookup"><span data-stu-id="2ff20-111">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="2ff20-112">Spécifiez l’affichage de la sous-arborescence en définissant la propriété <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> .</span><span class="sxs-lookup"><span data-stu-id="2ff20-112">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="2ff20-113">Affectez à la propriété <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> la valeur <xref:System.Windows.Automation.AutomationElementMode.None> si vous souhaitez augmenter l’efficacité en ne récupérant pas de référence complète aux objets.</span><span class="sxs-lookup"><span data-stu-id="2ff20-113">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="2ff20-114">(Cela rend impossible la récupération des valeurs actuelles de ces objets.)</span><span class="sxs-lookup"><span data-stu-id="2ff20-114">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="2ff20-115">Activez la requête à l’aide <xref:System.Windows.Automation.CacheRequest.Activate%2A> d’un `using` bloc ( `Using` dans Microsoft Visual Basic .net).</span><span class="sxs-lookup"><span data-stu-id="2ff20-115">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="2ff20-116">Après avoir obtenu des objets <xref:System.Windows.Automation.AutomationElement> ou vous être inscrit à des événements, désactivez la requête en utilisant <xref:System.Windows.Automation.CacheRequest.Pop%2A> (si <xref:System.Windows.Automation.CacheRequest.Push%2A> a été utilisé) ou en supprimant l’objet créé par <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="2ff20-116">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="2ff20-117">(Utilisez <xref:System.Windows.Automation.CacheRequest.Activate%2A> dans un `using` bloc ( `Using` dans Microsoft Visual Basic .net).</span><span class="sxs-lookup"><span data-stu-id="2ff20-117">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="2ff20-118">Mettre en cache des propriétés AutomationElement</span><span class="sxs-lookup"><span data-stu-id="2ff20-118">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="2ff20-119">Lorsqu’un <xref:System.Windows.Automation.CacheRequest> est actif, obtenez des objets <xref:System.Windows.Automation.AutomationElement> en utilisant <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, ou obtenez un <xref:System.Windows.Automation.AutomationElement> comme source d’un événement pour lequel vous vous êtes inscrit lorsque le <xref:System.Windows.Automation.CacheRequest> était actif.</span><span class="sxs-lookup"><span data-stu-id="2ff20-119">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="2ff20-120">(Vous pouvez également créer un cache en passant un <xref:System.Windows.Automation.CacheRequest> à GetUpdatedCache ou l’une des méthodes <xref:System.Windows.Automation.TreeWalker> .)</span><span class="sxs-lookup"><span data-stu-id="2ff20-120">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="2ff20-121">Utilisez <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> ou récupérez une propriété de la propriété <xref:System.Windows.Automation.AutomationElement.Cached%2A> de l’ <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="2ff20-121">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="2ff20-122">Obtenir des modèles mis en cache et leurs propriétés</span><span class="sxs-lookup"><span data-stu-id="2ff20-122">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="2ff20-123">Lorsqu’un <xref:System.Windows.Automation.CacheRequest> est actif, obtenez des objets <xref:System.Windows.Automation.AutomationElement> en utilisant <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> ou <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, ou obtenez un <xref:System.Windows.Automation.AutomationElement> comme source d’un événement pour lequel vous vous êtes inscrit lorsque le <xref:System.Windows.Automation.CacheRequest> était actif.</span><span class="sxs-lookup"><span data-stu-id="2ff20-123">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="2ff20-124">(Vous pouvez également créer un cache en passant un <xref:System.Windows.Automation.CacheRequest> à GetUpdatedCache ou l’une des méthodes <xref:System.Windows.Automation.TreeWalker> .)</span><span class="sxs-lookup"><span data-stu-id="2ff20-124">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="2ff20-125">Utilisez <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> pour récupérer un modèle mis en cache.</span><span class="sxs-lookup"><span data-stu-id="2ff20-125">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="2ff20-126">Récupérez les valeurs de propriété de la propriété `Cached` du modèle de contrôle.</span><span class="sxs-lookup"><span data-stu-id="2ff20-126">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ff20-127"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2ff20-127">Example</span></span>  

 <span data-ttu-id="2ff20-128">L’exemple de code suivant présente différents aspects de la mise en cache, en utilisant <xref:System.Windows.Automation.CacheRequest.Activate%2A> pour activer le <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="2ff20-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="2ff20-129"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2ff20-129">Example</span></span>  

 <span data-ttu-id="2ff20-130">L’exemple de code suivant présente différents aspects de la mise en cache, en utilisant <xref:System.Windows.Automation.CacheRequest.Push%2A> pour activer le <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="2ff20-130">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="2ff20-131">Excepté lorsque vous souhaitez imbriquer des requêtes de cache, il est préférable d’utiliser <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="2ff20-131">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="2ff20-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ff20-132">See also</span></span>

- [<span data-ttu-id="2ff20-133">Mise en cache dans les clients UI Automation</span><span class="sxs-lookup"><span data-stu-id="2ff20-133">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
