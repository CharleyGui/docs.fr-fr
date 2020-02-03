---
title: 'Comment : créer des contrôles'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 169104f51898f9bda08efa08685207e50406a7ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746720"
---
# <a name="how-to-author-controls-for-windows-forms"></a><span data-ttu-id="d0930-102">Comment : créer des contrôles pour Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d0930-102">How to: Author controls for Windows Forms</span></span>

<span data-ttu-id="d0930-103">Un contrôle désigne un lien graphique entre l’utilisateur et le programme.</span><span class="sxs-lookup"><span data-stu-id="d0930-103">A control represents a graphical link between the user and the program.</span></span> <span data-ttu-id="d0930-104">Un contrôle peut fournir ou traiter des données, accepter des entrées d’utilisateur, répondre à des événements ou effectuer de nombreuses autres fonctions afin de connecter l’utilisateur et l’application.</span><span class="sxs-lookup"><span data-stu-id="d0930-104">A control can provide or process data, accept user input, respond to events, or perform any number of other functions that connect the user and the application.</span></span> <span data-ttu-id="d0930-105">Un contrôle étant essentiellement un composant doté d’une interface graphique, il peut servir n’importe quelle fonction d’un composant, mais aussi fournir une interaction utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d0930-105">Because a control is essentially a component with a graphical interface, it can serve any function that a component does, as well as provide user interaction.</span></span> <span data-ttu-id="d0930-106">Les contrôles sont utilisés à des fins spécifiques, et la création de contrôles représente simplement une autre tâche de programmation.</span><span class="sxs-lookup"><span data-stu-id="d0930-106">Controls are created to serve specific purposes, and authoring controls is just another programming task.</span></span> <span data-ttu-id="d0930-107">Dans cette optique, les étapes suivantes constituent une vue d’ensemble du processus de création de contrôle.</span><span class="sxs-lookup"><span data-stu-id="d0930-107">With that in mind, the following steps represent an overview of the control authoring process.</span></span> <span data-ttu-id="d0930-108">Les liens renvoient vers des informations supplémentaires concernant les étapes individuelles.</span><span class="sxs-lookup"><span data-stu-id="d0930-108">Links provide additional information on the individual steps.</span></span>

## <a name="to-author-a-control"></a><span data-ttu-id="d0930-109">Pour créer un contrôle</span><span class="sxs-lookup"><span data-stu-id="d0930-109">To author a control</span></span>

1. <span data-ttu-id="d0930-110">Déterminez ce que votre contrôle devra accomplir ou le rôle qu’il jouera dans votre application.</span><span class="sxs-lookup"><span data-stu-id="d0930-110">Determine what you want your control to accomplish, or what part it will play in your application.</span></span> <span data-ttu-id="d0930-111">Tenez compte des facteurs suivants :</span><span class="sxs-lookup"><span data-stu-id="d0930-111">Factors to consider are:</span></span>

    - <span data-ttu-id="d0930-112">De quel type d’interface graphique avez-vous besoin ?</span><span class="sxs-lookup"><span data-stu-id="d0930-112">What kind of graphical interface do you need?</span></span>

    - <span data-ttu-id="d0930-113">Quelles interactions utilisateur spécifiques ce contrôle gérera-t-il ?</span><span class="sxs-lookup"><span data-stu-id="d0930-113">What specific user interactions will this control handle?</span></span>

    - <span data-ttu-id="d0930-114">La fonctionnalité dont vous avez besoin est-elle fournie par des contrôles existants ?</span><span class="sxs-lookup"><span data-stu-id="d0930-114">Is the functionality you need provided by any existing controls?</span></span>

    - <span data-ttu-id="d0930-115">Pouvez-vous obtenir la fonctionnalité dont vous avez besoin en combinant plusieurs contrôles Windows Forms ?</span><span class="sxs-lookup"><span data-stu-id="d0930-115">Can you get the functionality you need by combining several Windows Forms controls?</span></span>

2. <span data-ttu-id="d0930-116">Si vous avez besoin d’un modèle d’objet pour votre contrôle, déterminez comment la fonctionnalité sera distribuée dans tout le modèle d’objet et répartissez-la entre le contrôle et les éventuels sous-objets.</span><span class="sxs-lookup"><span data-stu-id="d0930-116">If you need an object model for your control, determine how functionality will be distributed throughout the object model, and divide up functionality between the control and any subobjects.</span></span> <span data-ttu-id="d0930-117">Un modèle d’objet peut être utile si vous prévoyez un contrôle complexe ou si vous souhaitez incorporer plusieurs fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="d0930-117">An object model may be useful if you are planning a complex control, or want to incorporate several functionalities.</span></span>

3. <span data-ttu-id="d0930-118">Déterminez le type de contrôle (par exemple, contrôle utilisateur, contrôle personnalisé, contrôle Windows Forms hérité) dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="d0930-118">Determine the type of control (for example, user control, custom control, inherited Windows Forms control) you need.</span></span> <span data-ttu-id="d0930-119">Pour plus d’informations, consultez [Recommandations relatives au type du contrôle](control-type-recommendations.md) et [Variétés de contrôles personnalisés](varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d0930-119">For details, see [Control Type Recommendations](control-type-recommendations.md) and [Varieties of Custom Controls](varieties-of-custom-controls.md).</span></span>

4. <span data-ttu-id="d0930-120">Présentez les fonctionnalités en tant que propriétés, méthodes et événements du contrôle et de ses sous-objets ou structures secondaires, et assignez des niveaux d’accès appropriés (par exemple, public, protégé, etc.).</span><span class="sxs-lookup"><span data-stu-id="d0930-120">Express functionality as properties, methods, and events of the control and its subobjects or subsidiary structures, and assign appropriate access levels (for example, public, protected, and so on).</span></span>

5. <span data-ttu-id="d0930-121">Si vous avez besoin d’une peinture personnalisée pour votre contrôle, ajoutez du code.</span><span class="sxs-lookup"><span data-stu-id="d0930-121">If you need custom painting for your control, add code for it.</span></span> <span data-ttu-id="d0930-122">Pour plus d’informations, consultez [Peinture et rendu personnalisés des contrôles](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="d0930-122">For details, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

6. <span data-ttu-id="d0930-123">Si votre contrôle hérite de <xref:System.Windows.Forms.UserControl>, vous pouvez tester son comportement d’exécution en générant le projet de contrôle et en l’exécutant dans le **conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="d0930-123">If your control inherits from <xref:System.Windows.Forms.UserControl>, you can test its runtime behavior by building the control project and running it in the **UserControl Test Container**.</span></span> <span data-ttu-id="d0930-124">Pour plus d’informations, consultez l’article [Comment : tester le comportement d’un UserControl au moment de l’exécution](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="d0930-124">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

7. <span data-ttu-id="d0930-125">Vous pouvez également tester et déboguer votre contrôle en créant un projet, comme une application Windows, et en le plaçant dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="d0930-125">You can also test and debug your control by creating a new project, such as a Windows Application, and placing it into a container.</span></span> <span data-ttu-id="d0930-126">Ce processus est illustré dans le cadre de la [procédure pas à pas : création d’un contrôle composite](walkthrough-authoring-a-composite-control-with-visual-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="d0930-126">This process is demonstrated as part of [Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md).</span></span>

8. <span data-ttu-id="d0930-127">À chaque ajout de fonctionnalité, ajoutez des fonctionnalités à votre projet de test pour tester cette nouvelle fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="d0930-127">As you add each feature, add features to your test project to exercise the new functionality.</span></span>

9. <span data-ttu-id="d0930-128">Répétez l’opération en affinant le design.</span><span class="sxs-lookup"><span data-stu-id="d0930-128">Repeat, refining the design.</span></span>

10. <span data-ttu-id="d0930-129">Empaquetez et déployez votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="d0930-129">Package and deploy your control.</span></span> <span data-ttu-id="d0930-130">Pour plus d’informations, consultez [premier aperçu du déploiement dans Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).</span><span class="sxs-lookup"><span data-stu-id="d0930-130">For details, see [First look at deployment in Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).</span></span>

## <a name="see-also"></a><span data-ttu-id="d0930-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0930-131">See also</span></span>

- [<span data-ttu-id="d0930-132">Comment : hériter de la classe UserControl</span><span class="sxs-lookup"><span data-stu-id="d0930-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="d0930-133">Guide pratique pour hériter de la classe du contrôle</span><span class="sxs-lookup"><span data-stu-id="d0930-133">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="d0930-134">Guide pratique pour hériter de contrôles Windows Forms existants</span><span class="sxs-lookup"><span data-stu-id="d0930-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="d0930-135">Guide pratique pour tester le comportement d'un UserControl au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="d0930-135">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="d0930-136">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="d0930-136">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
