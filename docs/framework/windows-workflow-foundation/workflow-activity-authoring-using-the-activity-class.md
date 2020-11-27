---
title: Création de l'activité de workflow à l'aide de la classe d'activité
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 21f1c8b1249d41029fa7a19360e96ad866c823a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293843"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a><span data-ttu-id="db1d0-102">Création de l'activité de workflow à l'aide de la classe d'activité</span><span class="sxs-lookup"><span data-stu-id="db1d0-102">Workflow Activity Authoring Using the Activity Class</span></span>

<span data-ttu-id="db1d0-103">La méthode la plus simple pour créer une activité à l’aide de Windows Workflow Foundation (WF) dans [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] consiste à créer une classe qui hérite de <xref:System.Activities.Activity> qui crée des fonctionnalités en assemblant des activités ou activités personnalisées à partir de la [bibliothèque d’activités intégrée](net-framework-4-5-built-in-activity-library.md).</span><span class="sxs-lookup"><span data-stu-id="db1d0-103">The most basic way to create an activity using Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] is to create a class that inherits from <xref:System.Activities.Activity> that creates functionality by assembling custom activities or activities from the [Built-In Activity Library](net-framework-4-5-built-in-activity-library.md).</span></span> <span data-ttu-id="db1d0-104">Cette rubrique montre comment créer une activité qui écrit deux messages sur la console.</span><span class="sxs-lookup"><span data-stu-id="db1d0-104">This topic demonstrates how to create an activity that writes two messages to the console.</span></span>

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a><span data-ttu-id="db1d0-105">Pour créer une activité personnalisée à l'aide du concepteur d'activités</span><span class="sxs-lookup"><span data-stu-id="db1d0-105">To create a custom Activity using the activity designer</span></span>

1. <span data-ttu-id="db1d0-106">Ouvrez Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="db1d0-106">Open Visual Studio 2012.</span></span>

2. <span data-ttu-id="db1d0-107">Sélectionnez Fichier, Nouveau, puis Projet.</span><span class="sxs-lookup"><span data-stu-id="db1d0-107">Select File, New, Project.</span></span> <span data-ttu-id="db1d0-108">Sélectionnez **Workflow 4,0** sous **Visual C#** dans la fenêtre **types de projets** , puis sélectionnez le nœud **v2010** .</span><span class="sxs-lookup"><span data-stu-id="db1d0-108">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="db1d0-109">Sélectionnez **bibliothèque d’activités** dans la fenêtre **modèles** .</span><span class="sxs-lookup"><span data-stu-id="db1d0-109">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="db1d0-110">Nommez le nouveau projet HelloActivity.</span><span class="sxs-lookup"><span data-stu-id="db1d0-110">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="db1d0-111">Ouvrez la nouvelle activité.</span><span class="sxs-lookup"><span data-stu-id="db1d0-111">Open the new activity.</span></span>  <span data-ttu-id="db1d0-112">Faites glisser une activité <xref:System.Activities.Statements.Sequence> de la boîte à outils jusqu'à l'aire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="db1d0-112">Drag a <xref:System.Activities.Statements.Sequence> activity from the toolbox onto the designer surface.</span></span>

4. <span data-ttu-id="db1d0-113">Faites glisser une activité <xref:System.Activities.Statements.WriteLine> dans l'activité <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="db1d0-113">Drag a <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="db1d0-114">Entrez `"Hello World"` (avec des guillemets) dans le champ de **texte** .</span><span class="sxs-lookup"><span data-stu-id="db1d0-114">Enter `"Hello World"` (with quotes) into the **Text** field.</span></span>

5. <span data-ttu-id="db1d0-115">Faites glisser une deuxième activité <xref:System.Activities.Statements.WriteLine> dans l'activité <xref:System.Activities.Statements.Sequence>, en dessous de la première.</span><span class="sxs-lookup"><span data-stu-id="db1d0-115">Drag a second <xref:System.Activities.Statements.WriteLine> activity into the <xref:System.Activities.Statements.Sequence> activity, below the first one.</span></span> <span data-ttu-id="db1d0-116">Entrez `"Goodbye"` (avec des guillemets) dans le champ de **texte** .</span><span class="sxs-lookup"><span data-stu-id="db1d0-116">Enter `"Goodbye"` (with quotes) into the **Text** field.</span></span>
