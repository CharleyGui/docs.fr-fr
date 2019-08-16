---
title: Implémentation du modèle de contrôle MultipleView d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 26e8ae7d0c560d8539b17e29d47545894cb4bb0f
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545197"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="b3e8e-102">Implémentation du modèle de contrôle MultipleView d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="b3e8e-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="b3e8e-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b3e8e-104">Pour obtenir les informations les [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]plus récentes [sur, consultez API Windows Automation: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="b3e8e-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b3e8e-105">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, notamment des informations sur les événements et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="b3e8e-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="b3e8e-107">Le modèle de contrôle <xref:System.Windows.Automation.MultipleViewPattern> permet de prendre en charge des contrôles qui fournissent plusieurs représentations du même ensemble d’informations ou de contrôles enfants, et permettent de basculer entre elles.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="b3e8e-108">Les exemples de contrôles qui peuvent présenter plusieurs affichages incluent le mode liste (qui peut afficher son contenu sous forme de miniatures, de vignettes, [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] d’icônes ou de détails), des graphiques (secteurs, courbes, barres [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] , valeurs de cellule avec une formule), des documents (normal, disposition Web, mise en page, lecture, disposition, plan), calendrier Microsoft Outlook (année, mois, semaine, jour) [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] et habillages.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] charts (pie, line, bar, cell value with a formula), [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skins.</span></span> <span data-ttu-id="b3e8e-109">Les vues prises en charge sont déterminées par le développeur de contrôle et sont spécifiques à chaque contrôle.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="b3e8e-110">Conventions et recommandations en matière d'implémentation</span><span class="sxs-lookup"><span data-stu-id="b3e8e-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="b3e8e-111">Quand vous implémentez le modèle de contrôle Multiple View, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b3e8e-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="b3e8e-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> doit également être implémenté sur un conteneur qui gère la vue actuelle s’il est différent d’un contrôle qui fournit la vue actuelle.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="b3e8e-113">Par exemple, l’Explorateur Windows contient un contrôle List pour le contenu du dossier actuel, tandis que la vue du contrôle est gérée à partir de l’application de l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="b3e8e-114">Un contrôle qui est en mesure de trier son contenu n’est pas censé prendre en charge plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="b3e8e-115">La collection de vues doit être identique sur l’ensemble des instances.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="b3e8e-116">Les noms des vues doivent pouvoir être utilisés dans le cadre de la synthèse vocale, de l’écriture en Braille et dans d’autres applications lisibles par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="b3e8e-117">Membres requis pour IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="b3e8e-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="b3e8e-118">Les propriétés et méthodes suivantes sont requises pour implémenter IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="b3e8e-119">Membres nécessaires</span><span class="sxs-lookup"><span data-stu-id="b3e8e-119">Required members</span></span>|<span data-ttu-id="b3e8e-120">Type de membre</span><span class="sxs-lookup"><span data-stu-id="b3e8e-120">Member type</span></span>|<span data-ttu-id="b3e8e-121">Notes</span><span class="sxs-lookup"><span data-stu-id="b3e8e-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="b3e8e-122">Propriété</span><span class="sxs-lookup"><span data-stu-id="b3e8e-122">Property</span></span>|<span data-ttu-id="b3e8e-123">Aucun</span><span class="sxs-lookup"><span data-stu-id="b3e8e-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="b3e8e-124">Méthode</span><span class="sxs-lookup"><span data-stu-id="b3e8e-124">Method</span></span>|<span data-ttu-id="b3e8e-125">Aucun</span><span class="sxs-lookup"><span data-stu-id="b3e8e-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="b3e8e-126">Méthode</span><span class="sxs-lookup"><span data-stu-id="b3e8e-126">Method</span></span>|<span data-ttu-id="b3e8e-127">Aucun</span><span class="sxs-lookup"><span data-stu-id="b3e8e-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="b3e8e-128">Méthode</span><span class="sxs-lookup"><span data-stu-id="b3e8e-128">Method</span></span>|<span data-ttu-id="b3e8e-129">Aucun</span><span class="sxs-lookup"><span data-stu-id="b3e8e-129">None</span></span>|  
  
 <span data-ttu-id="b3e8e-130">Aucun événement n’est associé à ce modèle de contrôle.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="b3e8e-131">Exceptions</span><span class="sxs-lookup"><span data-stu-id="b3e8e-131">Exceptions</span></span>  
 <span data-ttu-id="b3e8e-132">Le fournisseur doit lever les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="b3e8e-133">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="b3e8e-133">Exception type</span></span>|<span data-ttu-id="b3e8e-134">Condition</span><span class="sxs-lookup"><span data-stu-id="b3e8e-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="b3e8e-135">Quand la méthode <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> est appelée avec un paramètre qui n’est pas membre de la collection de vues prises en charge.</span><span class="sxs-lookup"><span data-stu-id="b3e8e-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3e8e-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3e8e-136">See also</span></span>

- [<span data-ttu-id="b3e8e-137">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="b3e8e-137">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="b3e8e-138">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="b3e8e-138">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="b3e8e-139">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="b3e8e-139">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="b3e8e-140">Présentation de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="b3e8e-140">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [<span data-ttu-id="b3e8e-141">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="b3e8e-141">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
