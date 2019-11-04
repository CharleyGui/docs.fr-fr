---
title: Implémentation du modèle de contrôle MultipleView d’UI Automation
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 62f0ba1dc8b7836a3b4699699b91b567eb8051f3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458181"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a><span data-ttu-id="da021-102">Implémentation du modèle de contrôle MultipleView d’UI Automation</span><span class="sxs-lookup"><span data-stu-id="da021-102">Implementing the UI Automation MultipleView Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="da021-103">Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="da021-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="da021-104">Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="da021-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="da021-105">Cette rubrique présente les conventions et recommandations à respecter pour implémenter <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, notamment des informations sur les événements et les propriétés.</span><span class="sxs-lookup"><span data-stu-id="da021-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, including information about events and properties.</span></span> <span data-ttu-id="da021-106">Des liens vers des références supplémentaires sont répertoriés à la fin de la rubrique.</span><span class="sxs-lookup"><span data-stu-id="da021-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="da021-107">Le modèle de contrôle <xref:System.Windows.Automation.MultipleViewPattern> permet de prendre en charge des contrôles qui fournissent plusieurs représentations du même ensemble d’informations ou de contrôles enfants, et permettent de basculer entre elles.</span><span class="sxs-lookup"><span data-stu-id="da021-107">The <xref:System.Windows.Automation.MultipleViewPattern> control pattern is used to support controls that provide, and are able to switch between, multiple representations of the same set of information or child controls.</span></span>  
  
 <span data-ttu-id="da021-108">Les exemples de contrôles qui peuvent présenter plusieurs affichages sont le mode liste (qui peut afficher son contenu sous forme de miniatures, de vignettes, d’icônes ou de détails), les graphiques Microsoft Excel (secteurs, courbes, barres, valeurs de cellule avec une formule), les documents Microsoft Word (normal, page Web, imprimer). disposition, lecture, disposition, plan), calendrier Microsoft Outlook (année, mois, semaine, jour) et habillages du lecteur Microsoft Windows Media.</span><span class="sxs-lookup"><span data-stu-id="da021-108">Examples of controls that can present multiple views include the list view (which can show its contents as thumbnails, tiles, icons, or details), Microsoft Excel charts (pie, line, bar, cell value with a formula), Microsoft Word documents (normal, Web layout, print layout, reading layout, outline), Microsoft Outlook calendar (year, month, week, day), and Microsoft Windows Media Player skins.</span></span> <span data-ttu-id="da021-109">Les vues prises en charge sont déterminées par le développeur de contrôle et sont spécifiques à chaque contrôle.</span><span class="sxs-lookup"><span data-stu-id="da021-109">The supported views are determined by the control developer and are specific to each control.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="da021-110">Conventions et directives d'implémentation</span><span class="sxs-lookup"><span data-stu-id="da021-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="da021-111">Quand vous implémentez le modèle de contrôle Multiple View, notez les conventions et recommandations suivantes :</span><span class="sxs-lookup"><span data-stu-id="da021-111">When implementing the Multiple View control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="da021-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> doit également être implémenté sur un conteneur qui gère la vue actuelle s’il est différent d’un contrôle qui fournit la vue actuelle.</span><span class="sxs-lookup"><span data-stu-id="da021-112"><xref:System.Windows.Automation.Provider.IMultipleViewProvider> should also be implemented on a container that manages the current view if it is different from a control that provides the current view.</span></span> <span data-ttu-id="da021-113">Par exemple, l’Explorateur Windows contient un contrôle List pour le contenu du dossier actuel, tandis que la vue du contrôle est gérée à partir de l’application de l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="da021-113">For example, Windows Explorer contains a List control for the current folder content while the view for the control is managed from the Windows Explorer application.</span></span>  
  
- <span data-ttu-id="da021-114">Un contrôle qui est en mesure de trier son contenu n’est pas censé prendre en charge plusieurs vues.</span><span class="sxs-lookup"><span data-stu-id="da021-114">A control that is able to sort its content is not considered to support multiple views.</span></span>  
  
- <span data-ttu-id="da021-115">La collection de vues doit être identique sur l’ensemble des instances.</span><span class="sxs-lookup"><span data-stu-id="da021-115">The collection of views must be identical across instances.</span></span>  
  
- <span data-ttu-id="da021-116">Les noms des vues doivent pouvoir être utilisés dans le cadre de la synthèse vocale, de l’écriture en Braille et dans d’autres applications lisibles par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="da021-116">View names must be suitable for use in Text to Speech, Braille, and other human-readable applications.</span></span>  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a><span data-ttu-id="da021-117">Membres requis pour IMultipleViewProvider</span><span class="sxs-lookup"><span data-stu-id="da021-117">Required Members for IMultipleViewProvider</span></span>  
 <span data-ttu-id="da021-118">Les propriétés et méthodes suivantes sont requises pour implémenter IMultipleViewProvider.</span><span class="sxs-lookup"><span data-stu-id="da021-118">The following properties and methods are required for implementing IMultipleViewProvider.</span></span>  
  
|<span data-ttu-id="da021-119">Membres nécessaires</span><span class="sxs-lookup"><span data-stu-id="da021-119">Required members</span></span>|<span data-ttu-id="da021-120">Type de membre</span><span class="sxs-lookup"><span data-stu-id="da021-120">Member type</span></span>|<span data-ttu-id="da021-121">Notes</span><span class="sxs-lookup"><span data-stu-id="da021-121">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|<span data-ttu-id="da021-122">Property</span><span class="sxs-lookup"><span data-stu-id="da021-122">Property</span></span>|<span data-ttu-id="da021-123">aucune.</span><span class="sxs-lookup"><span data-stu-id="da021-123">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|<span data-ttu-id="da021-124">Méthode</span><span class="sxs-lookup"><span data-stu-id="da021-124">Method</span></span>|<span data-ttu-id="da021-125">aucune.</span><span class="sxs-lookup"><span data-stu-id="da021-125">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|<span data-ttu-id="da021-126">Méthode</span><span class="sxs-lookup"><span data-stu-id="da021-126">Method</span></span>|<span data-ttu-id="da021-127">aucune.</span><span class="sxs-lookup"><span data-stu-id="da021-127">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|<span data-ttu-id="da021-128">Méthode</span><span class="sxs-lookup"><span data-stu-id="da021-128">Method</span></span>|<span data-ttu-id="da021-129">aucune.</span><span class="sxs-lookup"><span data-stu-id="da021-129">None</span></span>|  
  
 <span data-ttu-id="da021-130">Aucun événement n’est associé à ce modèle de contrôle.</span><span class="sxs-lookup"><span data-stu-id="da021-130">There are no events associated with this control pattern.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="da021-131">Exceptions</span><span class="sxs-lookup"><span data-stu-id="da021-131">Exceptions</span></span>  
 <span data-ttu-id="da021-132">Le fournisseur doit lever les exceptions suivantes.</span><span class="sxs-lookup"><span data-stu-id="da021-132">Provider must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="da021-133">Type d'exception</span><span class="sxs-lookup"><span data-stu-id="da021-133">Exception type</span></span>|<span data-ttu-id="da021-134">Condition</span><span class="sxs-lookup"><span data-stu-id="da021-134">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<span data-ttu-id="da021-135">Quand la méthode <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> ou <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> est appelée avec un paramètre qui n’est pas membre de la collection de vues prises en charge.</span><span class="sxs-lookup"><span data-stu-id="da021-135">When either <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> or <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> is called with a parameter that is not a member of the supported views collection.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da021-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da021-136">See also</span></span>

- [<span data-ttu-id="da021-137">Vue d’ensemble des modèles de contrôle UI Automation</span><span class="sxs-lookup"><span data-stu-id="da021-137">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="da021-138">Prendre en charge des modèles de contrôle dans un fournisseur UI Automation</span><span class="sxs-lookup"><span data-stu-id="da021-138">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="da021-139">Modèles de contrôle UI Automation pour les clients</span><span class="sxs-lookup"><span data-stu-id="da021-139">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="da021-140">Présentation de l’arborescence UI Automation</span><span class="sxs-lookup"><span data-stu-id="da021-140">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="da021-141">Utiliser la mise en cache dans UI Automation</span><span class="sxs-lookup"><span data-stu-id="da021-141">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
