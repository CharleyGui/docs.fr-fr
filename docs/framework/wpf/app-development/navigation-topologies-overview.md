---
title: Vue d'ensemble des topologies de navigation
ms.date: 03/30/2017
helpviewer_keywords:
- linear topology [WPF]
- fixed hierarchical topology [WPF]
- fixed linear topology [WPF]
- topologies [WPF]
- navigation topologies [WPF]
- dynamically-generated topology
ms.assetid: 5d5ee837-629a-4933-869a-186dc22ac43d
ms.openlocfilehash: 08f6342095706e5ffe9479f5236457d21474152a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174197"
---
# <a name="navigation-topologies-overview"></a><span data-ttu-id="dc88a-102">Vue d'ensemble des topologies de navigation</span><span class="sxs-lookup"><span data-stu-id="dc88a-102">Navigation Topologies Overview</span></span>
<a name="introduction"></a><span data-ttu-id="dc88a-103">Cette vue d’ensemble fournit une introduction aux topologies de navigation dans WPF.</span><span class="sxs-lookup"><span data-stu-id="dc88a-103">This overview provides an introduction to navigation topologies in WPF.</span></span> <span data-ttu-id="dc88a-104">Trois topologies de navigation courantes, avec des exemples, sont abordées dans cet article.</span><span class="sxs-lookup"><span data-stu-id="dc88a-104">Three common navigation topologies, with samples, are subsequently discussed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc88a-105">Avant de lire ce sujet, vous devez être familier avec le concept de navigation structurée dans WPF en utilisant des fonctions de page.</span><span class="sxs-lookup"><span data-stu-id="dc88a-105">Before reading this topic, you should be familiar with the concept of structured navigation in WPF using page functions.</span></span> <span data-ttu-id="dc88a-106">Pour plus d’informations sur ces deux sujets, voir [Aperçu de la navigation structurée](structured-navigation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dc88a-106">For more information on both of these topics, see [Structured Navigation Overview](structured-navigation-overview.md).</span></span>  
  
 <span data-ttu-id="dc88a-107">Cette rubrique contient les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="dc88a-107">This topic contains the following sections:</span></span>  
  
- [<span data-ttu-id="dc88a-108">Topologies de navigation</span><span class="sxs-lookup"><span data-stu-id="dc88a-108">Navigation Topologies</span></span>](#Navigation_Topologies)  
  
- [<span data-ttu-id="dc88a-109">Topologies de navigation structurée</span><span class="sxs-lookup"><span data-stu-id="dc88a-109">Structured Navigation Topologies</span></span>](#Structured_Navigation_Topologies)  
  
- [<span data-ttu-id="dc88a-110">Navigation sur une topologie linéaire fixe</span><span class="sxs-lookup"><span data-stu-id="dc88a-110">Navigation over a Fixed Linear Topology</span></span>](#Navigation_over_a_Fixed_Linear_Topology)  
  
- [<span data-ttu-id="dc88a-111">Navigation dynamique sur une topologie hiérarchique fixe</span><span class="sxs-lookup"><span data-stu-id="dc88a-111">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>](#Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology)  
  
- [<span data-ttu-id="dc88a-112">Navigation sur une topologie générée de manière dynamique</span><span class="sxs-lookup"><span data-stu-id="dc88a-112">Navigation over a Dynamically Generated Topology</span></span>](#Navigation_over_a_Dynamically_Generated_Topology)  
  
<a name="Navigation_Topologies"></a>
## <a name="navigation-topologies"></a><span data-ttu-id="dc88a-113">Topologies de navigation</span><span class="sxs-lookup"><span data-stu-id="dc88a-113">Navigation Topologies</span></span>  
 <span data-ttu-id="dc88a-114">Dans WPF, la navigation<xref:System.Windows.Controls.Page>se compose généralement<xref:System.Windows.Documents.Hyperlink>de pages ( ) avec hyperliens ( ) qui naviguent vers d’autres pages lorsqu’elles sont cliqués.</span><span class="sxs-lookup"><span data-stu-id="dc88a-114">In WPF, navigation typically consists of pages (<xref:System.Windows.Controls.Page>) with hyperlinks (<xref:System.Windows.Documents.Hyperlink>) that navigate to other pages when clicked.</span></span> <span data-ttu-id="dc88a-115">Les pages qui sont parcourues sont consultées par des identificateurs de ressources uniformes (ITI) (voir [URI Pack dans WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="dc88a-115">Pages that are navigated to are identified by uniform resource identifiers (URIs) (see [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span> <span data-ttu-id="dc88a-116">Prenons l’exemple simple suivant qui montre les pages, les hyperliens et les identificateurs de ressources uniformes (IERR) :</span><span class="sxs-lookup"><span data-stu-id="dc88a-116">Consider the following simple example that shows pages, hyperlinks, and uniform resource identifiers (URIs):</span></span>  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page1.xaml#page1)]  
  
 [!code-xaml[NavigationTopologiesOverviewSnippets#Page2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationTopologiesOverviewSnippets/CS/Page2.xaml#page2)]  
  
 <span data-ttu-id="dc88a-117">Ces pages sont disposées dans une *topologie de navigation* dont la structure est déterminée par la façon dont vous pouvez naviguer entre les pages.</span><span class="sxs-lookup"><span data-stu-id="dc88a-117">These pages are arranged in a *navigation topology* whose structure is determined by how you can navigate between the pages.</span></span> <span data-ttu-id="dc88a-118">Cette topologie de navigation particulière convient aux scénarios simples, bien que la navigation puisse nécessiter des topologies plus complexes, dont certaines peuvent être définies uniquement quand une application est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="dc88a-118">This particular navigation topology is suitable in simple scenarios, although navigation can require more complex topologies, some of which can only be defined when an application is running.</span></span>  
  
 <span data-ttu-id="dc88a-119">Ce sujet couvre trois topologies communes de navigation : *fixe linéaire,* *hiérarchique fixe,* et *dynamiquement générée.*</span><span class="sxs-lookup"><span data-stu-id="dc88a-119">This topic covers three common navigation topologies: *fixed linear*, *fixed hierarchical*, and *dynamically generated*.</span></span> <span data-ttu-id="dc88a-120">Chaque topologie de navigation est démontrée avec un échantillon qui a un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] comme celui qui est montré dans la figure suivante:</span><span class="sxs-lookup"><span data-stu-id="dc88a-120">Each navigation topology is demonstrated with a sample that has a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] like the one that is shown in the following figure:</span></span>  
  
 ![Pages de tâches avec des éléments de données et des boutons de navigation.](./media/navigation-topologies-overview/navigation-topology-data-items.png)  
  
<a name="Structured_Navigation_Topologies"></a>
## <a name="structured-navigation-topologies"></a><span data-ttu-id="dc88a-122">Topologies de navigation structurée</span><span class="sxs-lookup"><span data-stu-id="dc88a-122">Structured Navigation Topologies</span></span>  
 <span data-ttu-id="dc88a-123">Il existe deux grands types de topologies de navigation :</span><span class="sxs-lookup"><span data-stu-id="dc88a-123">There are two broad types of navigation topologies:</span></span>  
  
- <span data-ttu-id="dc88a-124">**Topologie fixe** : elle est définie au moment de la compilation et ne change pas au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="dc88a-124">**Fixed Topology**: defined at compile time and does not change at run time.</span></span> <span data-ttu-id="dc88a-125">Les topologies fixes sont utiles pour la navigation parmi une séquence fixe de pages dans un ordre linéaire ou hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="dc88a-125">Fixed topologies are useful for navigation through a fixed sequence of pages in either a linear or hierarchical order.</span></span>  
  
- <span data-ttu-id="dc88a-126">**Topologie dynamique** : elle est définie au moment de l’exécution en fonction des informations recueillies auprès de l’utilisateur, de l’application ou du système.</span><span class="sxs-lookup"><span data-stu-id="dc88a-126">**Dynamic Topology**: defined at run time based on input that is collected from the user, the application, or the system.</span></span> <span data-ttu-id="dc88a-127">Les topologies dynamiques sont utiles quand les pages peuvent être parcourues dans différentes séquences.</span><span class="sxs-lookup"><span data-stu-id="dc88a-127">Dynamic topologies are useful when pages can be navigated in different sequences.</span></span>  
  
 <span data-ttu-id="dc88a-128">Bien qu’il soit possible de créer des topologies de navigation à l’aide de pages, les exemples utilisent des fonctions de page car elles fournissent une prise en charge supplémentaire qui simplifie la prise en charge de la transmission et du retour de données par l’intermédiaire des pages d’une topologie.</span><span class="sxs-lookup"><span data-stu-id="dc88a-128">Although it is possible to create navigation topologies using pages, the samples use page functions because they provide additional support that simplifies support for passing and returning data through the pages of a topology.</span></span>  
  
<a name="Navigation_over_a_Fixed_Linear_Topology"></a>
## <a name="navigation-over-a-fixed-linear-topology"></a><span data-ttu-id="dc88a-129">Navigation sur une topologie linéaire fixe</span><span class="sxs-lookup"><span data-stu-id="dc88a-129">Navigation over a Fixed Linear Topology</span></span>  
 <span data-ttu-id="dc88a-130">Une topologie linéaire fixe est analogue à la structure d’un Assistant qui a une ou plusieurs pages parcourues dans une séquence fixe.</span><span class="sxs-lookup"><span data-stu-id="dc88a-130">A fixed linear topology is analogous to the structure of a wizard that has one or more wizard pages that are navigated in a fixed sequence.</span></span> <span data-ttu-id="dc88a-131">La figure suivante montre la structure de haut niveau et le flux d’un sorcier avec une topologie linéaire fixe:</span><span class="sxs-lookup"><span data-stu-id="dc88a-131">The following figure shows the high-level structure and flow of a wizard with a fixed linear topology:</span></span>  
  
 ![Diagramme qui montre une topologie linéaire fixe.](./media/navigation-topologies-overview/navigation-topology-fixed-linear.png)  
  
 <span data-ttu-id="dc88a-133">Les comportements types de navigation dans une topologie linéaire fixe sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="dc88a-133">The typical behaviors for navigating over a fixed linear topology include the following:</span></span>  
  
- <span data-ttu-id="dc88a-134">Navigation de la page appelante vers une page de lancement qui initialise l’Assistant et accède à sa première page.</span><span class="sxs-lookup"><span data-stu-id="dc88a-134">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="dc88a-135">Une page de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]lanceur (un -moins) <xref:System.Windows.Navigation.PageFunction%601>n’est pas nécessaire, puisqu’une page d’appel peut appeler directement la première page d’assistant.</span><span class="sxs-lookup"><span data-stu-id="dc88a-135">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="dc88a-136">Une page de lancement vous permet toutefois de simplifier l’initialisation de l’Assistant, en particulier si l’initialisation est complexe.</span><span class="sxs-lookup"><span data-stu-id="dc88a-136">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="dc88a-137">Les utilisateurs peuvent naviguer parmi les pages à l’aide de boutons Précédent et Suivant (ou de liens hypertexte).</span><span class="sxs-lookup"><span data-stu-id="dc88a-137">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="dc88a-138">Les utilisateurs peuvent naviguer parmi les pages à l’aide du journal.</span><span class="sxs-lookup"><span data-stu-id="dc88a-138">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="dc88a-139">Les utilisateurs peuvent annuler l’Assistant à partir de n’importe laquelle de ses pages en appuyant sur un bouton Annuler.</span><span class="sxs-lookup"><span data-stu-id="dc88a-139">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="dc88a-140">Les utilisateurs peuvent accepter l’Assistant dans sa dernière page en appuyant sur un bouton Terminer.</span><span class="sxs-lookup"><span data-stu-id="dc88a-140">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="dc88a-141">Si un Assistant est annulé, il retourne un résultat approprié et ne retourne aucune donnée.</span><span class="sxs-lookup"><span data-stu-id="dc88a-141">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="dc88a-142">Si un utilisateur accepte un Assistant, celui-ci retourne un résultat approprié et retourne les données recueillies.</span><span class="sxs-lookup"><span data-stu-id="dc88a-142">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="dc88a-143">Une fois l’Assistant terminé (accepté ou annulé), les pages que comporte l’Assistant sont supprimées du journal.</span><span class="sxs-lookup"><span data-stu-id="dc88a-143">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="dc88a-144">Ainsi, chaque instance de l’Assistant est isolée, ce qui évite les anomalies de données ou d’état potentielles.</span><span class="sxs-lookup"><span data-stu-id="dc88a-144">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Dynamic_Navigation_over_a_Fixed_Hierarchical_Topology"></a>
## <a name="dynamic-navigation-over-a-fixed-hierarchical-topology"></a><span data-ttu-id="dc88a-145">Navigation dynamique sur une topologie hiérarchique fixe</span><span class="sxs-lookup"><span data-stu-id="dc88a-145">Dynamic Navigation over a Fixed Hierarchical Topology</span></span>  
 <span data-ttu-id="dc88a-146">Dans certaines applications, les pages permettent la navigation à deux ou plusieurs autres pages, comme le montre le chiffre suivant :</span><span class="sxs-lookup"><span data-stu-id="dc88a-146">In some applications, pages allow navigation to two or more other pages, as shown in the following figure:</span></span>
  
 ![Diagramme qui affiche une page qui peut naviguer vers plusieurs pages.](./media/navigation-topologies-overview/navigation-topology-multiple-pages.png)  
  
 <span data-ttu-id="dc88a-148">Cette structure porte le nom de topologie hiérarchique fixe, et la séquence dans laquelle la hiérarchie est parcourue est souvent déterminée au moment de l’exécution par l’application ou l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="dc88a-148">This structure is known as a fixed hierarchical topology, and the sequence in which the hierarchy is traversed is often determined at run time by either the application or the user.</span></span> <span data-ttu-id="dc88a-149">Au moment de l’exécution, chaque page de la hiérarchie qui autorise la navigation vers plusieurs autres pages recueille les données nécessaires pour déterminer la page à atteindre.</span><span class="sxs-lookup"><span data-stu-id="dc88a-149">At run time, each page in the hierarchy that allows navigation to two or more other pages gathers the data required to determine which page to navigate to.</span></span> <span data-ttu-id="dc88a-150">Le chiffre suivant illustre l’une des nombreuses séquences de navigation possibles basées sur le chiffre précédent :</span><span class="sxs-lookup"><span data-stu-id="dc88a-150">The following figure illustrates one of several possible navigation sequences based on the previous figure:</span></span>  
  
 ![Diagramme qui montre une séquence de navigation possible.](./media/navigation-topologies-overview/navigation-topology-fixed-hierarchical.png)  
  
 <span data-ttu-id="dc88a-152">Bien que la séquence dans laquelle les pages d’une structure hiérarchique fixe sont parcourues soit déterminée au moment de l’exécution, l’expérience utilisateur est identique à celle d’une topologie linéaire fixe :</span><span class="sxs-lookup"><span data-stu-id="dc88a-152">Even though the sequence in which pages in a fixed hierarchical structure are navigated is determined at run time, the user experience is the same as the user experience for a fixed linear topology:</span></span>  
  
- <span data-ttu-id="dc88a-153">Navigation de la page appelante vers une page de lancement qui initialise l’Assistant et accède à sa première page.</span><span class="sxs-lookup"><span data-stu-id="dc88a-153">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="dc88a-154">Une page de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]lanceur (un -moins) <xref:System.Windows.Navigation.PageFunction%601>n’est pas nécessaire, puisqu’une page d’appel peut appeler directement la première page d’assistant.</span><span class="sxs-lookup"><span data-stu-id="dc88a-154">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="dc88a-155">Une page de lancement vous permet toutefois de simplifier l’initialisation de l’Assistant, en particulier si l’initialisation est complexe.</span><span class="sxs-lookup"><span data-stu-id="dc88a-155">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="dc88a-156">Les utilisateurs peuvent naviguer parmi les pages à l’aide de boutons Précédent et Suivant (ou de liens hypertexte).</span><span class="sxs-lookup"><span data-stu-id="dc88a-156">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="dc88a-157">Les utilisateurs peuvent naviguer parmi les pages à l’aide du journal.</span><span class="sxs-lookup"><span data-stu-id="dc88a-157">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="dc88a-158">Les utilisateurs peuvent changer la séquence de navigation s’ils reviennent en arrière dans le journal.</span><span class="sxs-lookup"><span data-stu-id="dc88a-158">Users can change the navigation sequence if they navigate back through the journal.</span></span>  
  
- <span data-ttu-id="dc88a-159">Les utilisateurs peuvent annuler l’Assistant à partir de n’importe laquelle de ses pages en appuyant sur un bouton Annuler.</span><span class="sxs-lookup"><span data-stu-id="dc88a-159">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="dc88a-160">Les utilisateurs peuvent accepter l’Assistant dans sa dernière page en appuyant sur un bouton Terminer.</span><span class="sxs-lookup"><span data-stu-id="dc88a-160">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="dc88a-161">Si un Assistant est annulé, il retourne un résultat approprié et ne retourne aucune donnée.</span><span class="sxs-lookup"><span data-stu-id="dc88a-161">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="dc88a-162">Si un utilisateur accepte un Assistant, celui-ci retourne un résultat approprié et retourne les données recueillies.</span><span class="sxs-lookup"><span data-stu-id="dc88a-162">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="dc88a-163">Une fois l’Assistant terminé (accepté ou annulé), les pages que comporte l’Assistant sont supprimées du journal.</span><span class="sxs-lookup"><span data-stu-id="dc88a-163">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="dc88a-164">Ainsi, chaque instance de l’Assistant est isolée, ce qui évite les anomalies de données ou d’état potentielles.</span><span class="sxs-lookup"><span data-stu-id="dc88a-164">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
<a name="Navigation_over_a_Dynamically_Generated_Topology"></a>
## <a name="navigation-over-a-dynamically-generated-topology"></a><span data-ttu-id="dc88a-165">Navigation sur une topologie générée de manière dynamique</span><span class="sxs-lookup"><span data-stu-id="dc88a-165">Navigation over a Dynamically Generated Topology</span></span>  
 <span data-ttu-id="dc88a-166">Dans certaines applications, la séquence dans laquelle plusieurs pages sont parcourues peut être déterminée uniquement au moment de l’exécution, que ce soit par l’utilisateur, par l’application ou par des données externes.</span><span class="sxs-lookup"><span data-stu-id="dc88a-166">In some applications, the sequence in which two or more pages are navigated can only be determined at run time, whether by the user, the application, or external data.</span></span> <span data-ttu-id="dc88a-167">Le chiffre suivant illustre un ensemble de pages avec une séquence de navigation indéterminée :</span><span class="sxs-lookup"><span data-stu-id="dc88a-167">The following figure illustrates a set of pages with an undetermined navigation sequence:</span></span>  
  
 ![Un ensemble de pages avec une séquence de navigation indéterminée.](./media/navigation-topologies-overview/navigation-topology-dynamically-generated.png)  
  
 <span data-ttu-id="dc88a-169">Le personnage suivant illustre une séquence de navigation qui a été choisie par l’utilisateur au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="dc88a-169">The next figure illustrates a navigation sequence that was chosen by the user at run time:</span></span>  
  
 ![Diagramme qui montre une séquence de navigation choisie au moment de l’exécution.](./media/navigation-topologies-overview/navigation-topology-sequence-chosen-run-time.png)  
  
 <span data-ttu-id="dc88a-171">Cette séquence de navigation est une topologie générée de manière dynamique.</span><span class="sxs-lookup"><span data-stu-id="dc88a-171">The navigation sequence is known as a dynamically generated topology.</span></span> <span data-ttu-id="dc88a-172">Pour l’utilisateur, comme avec les autres topologies de navigation, l’expérience utilisateur est la même qu’avec les topologies précédentes :</span><span class="sxs-lookup"><span data-stu-id="dc88a-172">For the user, as with the other navigation topologies, the user experience is the same as it is for the previous topologies:</span></span>  
  
- <span data-ttu-id="dc88a-173">Navigation de la page appelante vers une page de lancement qui initialise l’Assistant et accède à sa première page.</span><span class="sxs-lookup"><span data-stu-id="dc88a-173">Navigating from the calling page to a launcher page that initializes the wizard and navigates to the first wizard page.</span></span> <span data-ttu-id="dc88a-174">Une page de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]lanceur (un -moins) <xref:System.Windows.Navigation.PageFunction%601>n’est pas nécessaire, puisqu’une page d’appel peut appeler directement la première page d’assistant.</span><span class="sxs-lookup"><span data-stu-id="dc88a-174">A launcher page (a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]-less <xref:System.Windows.Navigation.PageFunction%601>) is not required, since a calling page can call the first wizard page directly.</span></span> <span data-ttu-id="dc88a-175">Une page de lancement vous permet toutefois de simplifier l’initialisation de l’Assistant, en particulier si l’initialisation est complexe.</span><span class="sxs-lookup"><span data-stu-id="dc88a-175">Using a launcher page, however, can simplify wizard initialization, particularly if initialization is complex.</span></span>  
  
- <span data-ttu-id="dc88a-176">Les utilisateurs peuvent naviguer parmi les pages à l’aide de boutons Précédent et Suivant (ou de liens hypertexte).</span><span class="sxs-lookup"><span data-stu-id="dc88a-176">Users can navigate between pages by using Back and Forward buttons (or hyperlinks).</span></span>  
  
- <span data-ttu-id="dc88a-177">Les utilisateurs peuvent naviguer parmi les pages à l’aide du journal.</span><span class="sxs-lookup"><span data-stu-id="dc88a-177">Users can navigate between pages using the journal.</span></span>  
  
- <span data-ttu-id="dc88a-178">Les utilisateurs peuvent annuler l’Assistant à partir de n’importe laquelle de ses pages en appuyant sur un bouton Annuler.</span><span class="sxs-lookup"><span data-stu-id="dc88a-178">Users can cancel the wizard from any wizard page by pressing a Cancel button.</span></span>  
  
- <span data-ttu-id="dc88a-179">Les utilisateurs peuvent accepter l’Assistant dans sa dernière page en appuyant sur un bouton Terminer.</span><span class="sxs-lookup"><span data-stu-id="dc88a-179">Users can accept the wizard on the last wizard page by pressing a Finish button.</span></span>  
  
- <span data-ttu-id="dc88a-180">Si un Assistant est annulé, il retourne un résultat approprié et ne retourne aucune donnée.</span><span class="sxs-lookup"><span data-stu-id="dc88a-180">If a wizard is canceled, the wizard returns an appropriate result, and does not return any data.</span></span>  
  
- <span data-ttu-id="dc88a-181">Si un utilisateur accepte un Assistant, celui-ci retourne un résultat approprié et retourne les données recueillies.</span><span class="sxs-lookup"><span data-stu-id="dc88a-181">If a user accepts a wizard, the wizard returns an appropriate result, and returns the data it collected.</span></span>  
  
- <span data-ttu-id="dc88a-182">Une fois l’Assistant terminé (accepté ou annulé), les pages que comporte l’Assistant sont supprimées du journal.</span><span class="sxs-lookup"><span data-stu-id="dc88a-182">When the wizard is complete (accepted or canceled), the pages that the wizard comprises are removed from the journal.</span></span> <span data-ttu-id="dc88a-183">Ainsi, chaque instance de l’Assistant est isolée, ce qui évite les anomalies de données ou d’état potentielles.</span><span class="sxs-lookup"><span data-stu-id="dc88a-183">This keeps each instance of the wizard isolated, thereby avoiding potential data or state anomalies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc88a-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc88a-184">See also</span></span>

- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.PageFunction%601>
- <xref:System.Windows.Navigation.NavigationService>
- [<span data-ttu-id="dc88a-185">Vue d’ensemble de la navigation structurée</span><span class="sxs-lookup"><span data-stu-id="dc88a-185">Structured Navigation Overview</span></span>](structured-navigation-overview.md)
