---
title: 'Procédure : tester le comportement au moment de l’exécution d’un UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 110036e5031a2956375b1edf0689237661522d39
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180204"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="9368a-102">Procédure : Tester le comportement d’un UserControl au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="9368a-102">How to: Test the run-time behavior of a UserControl</span></span>

<span data-ttu-id="9368a-103">Lorsque vous développez un <xref:System.Windows.Forms.UserControl>, vous devez tester son comportement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9368a-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="9368a-104">Vous pouvez créer un projet d’application Windows distinct et placer votre contrôle sur un formulaire de test, mais cette procédure est peu commode.</span><span class="sxs-lookup"><span data-stu-id="9368a-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="9368a-105">Un moyen plus rapide et plus simple consiste à utiliser le **conteneur de test UserControl** fourni par Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9368a-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="9368a-106">Ce conteneur de test démarre directement à partir de votre projet de bibliothèque de contrôles Windows.</span><span class="sxs-lookup"><span data-stu-id="9368a-106">This test container starts directly from your Windows control library project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9368a-107">Pour que le conteneur de test charge votre <xref:System.Windows.Forms.UserControl>, le contrôle doit avoir au moins un constructeur public.</span><span class="sxs-lookup"><span data-stu-id="9368a-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="9368a-108">Un contrôle C++ visuel ne peut pas être testé à l’aide du **conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="9368a-108">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="9368a-109">Tester le comportement d’un UserControl au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="9368a-109">Test the run-time behavior of a UserControl</span></span>

1. <span data-ttu-id="9368a-110">Dans Visual Studio, créez un projet de bibliothèque de contrôles Windows, puis nommez-le **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="9368a-110">In Visual Studio, create a Windows control library project, and name it **TestContainerExample**.</span></span>

2. <span data-ttu-id="9368a-111">Dans le **Concepteur Windows Forms**, faites glisser un contrôle <xref:System.Windows.Forms.Label> de la **boîte à outils** vers l’aire de conception du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9368a-111">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="9368a-112">Appuyez sur <kbd>F5</kbd> pour générer le projet et exécuter le **conteneur de test UserControl**.</span><span class="sxs-lookup"><span data-stu-id="9368a-112">Press <kbd>F5</kbd> to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="9368a-113">Le conteneur de test s’affiche avec votre <xref:System.Windows.Forms.UserControl> dans le volet de **visualisation** .</span><span class="sxs-lookup"><span data-stu-id="9368a-113">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="9368a-114">Sélectionnez la propriété <xref:System.Windows.Forms.Control.BackColor%2A> affichée dans le contrôle <xref:System.Windows.Forms.PropertyGrid> à droite du volet de **visualisation** .</span><span class="sxs-lookup"><span data-stu-id="9368a-114">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="9368a-115">Remplacez sa valeur par **ControlDark**.</span><span class="sxs-lookup"><span data-stu-id="9368a-115">Change its value to **ControlDark**.</span></span> <span data-ttu-id="9368a-116">Notez que le contrôle passe à une couleur plus sombre.</span><span class="sxs-lookup"><span data-stu-id="9368a-116">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="9368a-117">Essayez de modifier d’autres valeurs de propriété et observez l’effet sur votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="9368a-117">Try changing other property values and observe the effect on your control.</span></span>

5. <span data-ttu-id="9368a-118">Activez la case à cocher **ancrer remplir le contrôle utilisateur** sous le volet de **visualisation** .</span><span class="sxs-lookup"><span data-stu-id="9368a-118">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="9368a-119">Notez que le contrôle est redimensionné pour remplir le volet.</span><span class="sxs-lookup"><span data-stu-id="9368a-119">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="9368a-120">Redimensionnez le conteneur de test et observez que le contrôle est redimensionné avec le volet.</span><span class="sxs-lookup"><span data-stu-id="9368a-120">Resize the test container and observe that the control is resized with the pane.</span></span>

6. <span data-ttu-id="9368a-121">Fermez le conteneur de test.</span><span class="sxs-lookup"><span data-stu-id="9368a-121">Close the test container.</span></span>

7. <span data-ttu-id="9368a-122">Ajoutez un autre contrôle utilisateur au projet **TestContainerExample** .</span><span class="sxs-lookup"><span data-stu-id="9368a-122">Add another user control to the **TestContainerExample** project.</span></span>

8. <span data-ttu-id="9368a-123">Dans le **Concepteur Windows Forms**, faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **boîte à outils** vers l’aire de conception du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9368a-123">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>

9. <span data-ttu-id="9368a-124">Appuyez sur <kbd>F5</kbd> pour générer le projet et exécuter le conteneur de test.</span><span class="sxs-lookup"><span data-stu-id="9368a-124">Press <kbd>F5</kbd> to build the project and run the test container.</span></span>

10. <span data-ttu-id="9368a-125">Cliquez sur l' @no__t **Sélectionner un contrôle utilisateur** -1 pour basculer entre les deux contrôles utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9368a-125">Click the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>

## <a name="test-user-controls-from-another-project"></a><span data-ttu-id="9368a-126">Tester des contrôles utilisateur à partir d’un autre projet</span><span class="sxs-lookup"><span data-stu-id="9368a-126">Test user controls from another project</span></span>

<span data-ttu-id="9368a-127">Vous pouvez tester des contrôles utilisateur à partir d’autres projets dans le conteneur de test de votre projet actuel.</span><span class="sxs-lookup"><span data-stu-id="9368a-127">You can test user controls from other projects in your current project's test container.</span></span>

1. <span data-ttu-id="9368a-128">Dans Visual Studio, créez un projet de bibliothèque de contrôles Windows, puis nommez-le **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="9368a-128">In Visual Studio, create a Windows control library project, and name it **TestContainerExample2**.</span></span>

2. <span data-ttu-id="9368a-129">Dans le **Concepteur Windows Forms**, faites glisser un contrôle <xref:System.Windows.Forms.RadioButton> de la **boîte à outils** vers l’aire de conception du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9368a-129">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>

3. <span data-ttu-id="9368a-130">Appuyez sur <kbd>F5</kbd> pour générer le projet et exécuter le conteneur de test.</span><span class="sxs-lookup"><span data-stu-id="9368a-130">Press <kbd>F5</kbd> to build the project and run the test container.</span></span> <span data-ttu-id="9368a-131">Le conteneur de test s’affiche avec votre <xref:System.Windows.Forms.UserControl> dans le volet de **visualisation** .</span><span class="sxs-lookup"><span data-stu-id="9368a-131">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>

4. <span data-ttu-id="9368a-132">Cliquez sur le bouton **charger** .</span><span class="sxs-lookup"><span data-stu-id="9368a-132">Click the **Load** button.</span></span>

5. <span data-ttu-id="9368a-133">Dans la boîte de dialogue **ouvrir** , accédez à *TestContainerExample. dll*, que vous avez créé dans la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="9368a-133">In the **Open** dialog box, navigate to *TestContainerExample.dll*, which you built in the previous procedure.</span></span> <span data-ttu-id="9368a-134">Sélectionnez *TestContainerExample. dll* , puis cliquez sur le bouton **ouvrir** pour charger les contrôles utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9368a-134">Select *TestContainerExample.dll* and click the **Open** button to load the user controls.</span></span>

6. <span data-ttu-id="9368a-135">Utilisez l' @no__t de **sélection de contrôle utilisateur** -1 pour basculer entre les deux contrôles utilisateur du projet **TestContainerExample** .</span><span class="sxs-lookup"><span data-stu-id="9368a-135">Use the **Select User Control** <xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>

## <a name="see-also"></a><span data-ttu-id="9368a-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9368a-136">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <span data-ttu-id="9368a-137">[Guide pratique : Créer des contrôles composites @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="9368a-137">[How to: Author Composite Controls](how-to-author-composite-controls.md)</span></span>
- <span data-ttu-id="9368a-138">[Procédure pas à pas : Création d’un contrôle composite @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="9368a-138">[Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span></span>
- <span data-ttu-id="9368a-139">[Concepteur de contrôles utilisateur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9368a-139">[User Control Designer](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))</span></span>
