---
title: 'Comment : créer des contrôles composites'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], creating composite controls
- user controls [Windows Forms], creating
- user controls [Windows Forms], inheriting from
- composite controls [Windows Forms], creating
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 42ea424507b89576df8099fd4849dd2665135a55
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459439"
---
# <a name="how-to-author-composite-controls"></a><span data-ttu-id="054a7-102">Comment : créer des contrôles composites</span><span class="sxs-lookup"><span data-stu-id="054a7-102">How to: Author composite controls</span></span>

<span data-ttu-id="054a7-103">Les contrôles composites peuvent être utilisés de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="054a7-103">Composite controls can be employed in many ways.</span></span> <span data-ttu-id="054a7-104">Vous pouvez les créer dans le cadre d’un projet d’application de bureau Windows et les utiliser uniquement sur les formulaires du projet.</span><span class="sxs-lookup"><span data-stu-id="054a7-104">You can author them as part of a Windows desktop application project, and use them only on forms in the project.</span></span> <span data-ttu-id="054a7-105">Ou vous pouvez les créer dans un projet de bibliothèque de contrôles Windows, compiler le projet dans un assembly et utiliser les contrôles dans d’autres projets.</span><span class="sxs-lookup"><span data-stu-id="054a7-105">Or you can author them in a Windows Control Library project, compile the project into an assembly, and use the controls in other projects.</span></span> <span data-ttu-id="054a7-106">Vous pouvez même hériter de ces éléments et utiliser l’héritage visuel pour les personnaliser rapidement à des fins spéciales.</span><span class="sxs-lookup"><span data-stu-id="054a7-106">You can even inherit from them and use visual inheritance to customize them quickly for special purposes.</span></span>

## <a name="to-author-a-composite-control"></a><span data-ttu-id="054a7-107">Pour créer un contrôle composite</span><span class="sxs-lookup"><span data-stu-id="054a7-107">To author a composite control</span></span>

1. <span data-ttu-id="054a7-108">Dans Visual Studio, créez un nouveau projet d' **application Windows** et nommez-le **DemoControlHost**.</span><span class="sxs-lookup"><span data-stu-id="054a7-108">In Visual Studio, create a new **Windows Application** project, and name it **DemoControlHost**.</span></span>

2. <span data-ttu-id="054a7-109">Dans le menu **Projet** , cliquez sur **Ajouter un contrôle utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="054a7-109">On the **Project** menu, click **Add User Control**.</span></span>

3. <span data-ttu-id="054a7-110">Dans la boîte de dialogue **Ajouter un nouvel élément**, donnez au fichier de classe (fichier .vb ou .cs) le nom que vous souhaitez pour le contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="054a7-110">In the **Add New Item** dialog box, give the class file (.vb or .cs file) the name you want the composite control to have.</span></span>

4. <span data-ttu-id="054a7-111">Sélectionnez le bouton **Ajouter** pour créer le fichier de classe pour le contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="054a7-111">Select the **Add** button to create the class file for the composite control.</span></span>

5. <span data-ttu-id="054a7-112">Utilisez la **boîte à outils** pour ajouter des contrôles à la surface du contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="054a7-112">Add controls from the **Toolbox** to the composite control surface.</span></span>

6. <span data-ttu-id="054a7-113">Placez le code dans des procédures événementielles afin de gérer les événements déclenchés par le contrôle composite ou par ses contrôles constitutifs.</span><span class="sxs-lookup"><span data-stu-id="054a7-113">Place code in event procedures, to handle events raised by the composite control or by its constituent controls.</span></span>

7. <span data-ttu-id="054a7-114">Fermez le concepteur du contrôle composite et enregistrez le fichier lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="054a7-114">Close the designer for the composite control, and save the file when you are prompted.</span></span>

8. <span data-ttu-id="054a7-115">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="054a7-115">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="054a7-116">Le projet doit être généré de sorte que les contrôles personnalisés apparaissent dans la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="054a7-116">The project must be built in order for custom controls to appear in the **Toolbox**.</span></span>

9. <span data-ttu-id="054a7-117">Utilisez l’onglet **DemoControlHost** de la **boîte à outils** pour ajouter des instances de votre contrôle sur `Form1`.</span><span class="sxs-lookup"><span data-stu-id="054a7-117">Use the **DemoControlHost** tab of the **Toolbox** to add instances of your control to `Form1`.</span></span>

## <a name="to-author-a-control-class-library"></a><span data-ttu-id="054a7-118">Pour créer une bibliothèque de classes de contrôle</span><span class="sxs-lookup"><span data-stu-id="054a7-118">To author a control class library</span></span>

1. <span data-ttu-id="054a7-119">Ouvrez un nouveau projet de **bibliothèque de contrôles Windows**.</span><span class="sxs-lookup"><span data-stu-id="054a7-119">Open a new **Windows Control Library** project.</span></span>

     <span data-ttu-id="054a7-120">Par défaut, le projet contient un contrôle composite.</span><span class="sxs-lookup"><span data-stu-id="054a7-120">By default, the project contains a composite control.</span></span>

2. <span data-ttu-id="054a7-121">Ajoutez des contrôles et du code, comme décrit dans la procédure ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="054a7-121">Add controls and code as described in the procedure above.</span></span>

3. <span data-ttu-id="054a7-122">Sélectionnez un contrôle dont vous ne souhaitez pas modifier les classes qui héritent, puis définissez la propriété **Modifiers** de ce contrôle sur **Private**.</span><span class="sxs-lookup"><span data-stu-id="054a7-122">Choose a control you do not want inheriting classes to change, and set the **Modifiers** property of this control to **Private**.</span></span>

4. <span data-ttu-id="054a7-123">Créez la DLL.</span><span class="sxs-lookup"><span data-stu-id="054a7-123">Build the DLL.</span></span>

## <a name="to-inherit-from-a-composite-control-in-a-control-class-library"></a><span data-ttu-id="054a7-124">Pour hériter d’un contrôle composite dans une bibliothèque de classes de contrôle</span><span class="sxs-lookup"><span data-stu-id="054a7-124">To inherit from a composite control in a control class library</span></span>

1. <span data-ttu-id="054a7-125">Dans le menu **Fichier**, pointez sur **Ajouter** et sélectionnez **Nouveau projet** pour ajouter un nouveau projet d’**application Windows** à la solution.</span><span class="sxs-lookup"><span data-stu-id="054a7-125">On the **File** menu, point to **Add** and select **New Project** to add a new **Windows Application** project to the solution.</span></span>

2. <span data-ttu-id="054a7-126">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le dossier **References** du nouveau projet, puis sélectionnez **Ajouter une référence** pour ouvrir la boîte de dialogue **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="054a7-126">In **Solution Explorer**, right-click the **References** folder for the new project and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

3. <span data-ttu-id="054a7-127">Sélectionnez l’onglet **Projets** et double-cliquez sur votre projet de bibliothèque de contrôles.</span><span class="sxs-lookup"><span data-stu-id="054a7-127">Select the **Projects** tab and double-click your control library project.</span></span>

4. <span data-ttu-id="054a7-128">Dans le menu **Générer** , cliquez sur **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="054a7-128">On the **Build** menu, click **Build Solution**.</span></span>

5. <span data-ttu-id="054a7-129">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet de bibliothèque de contrôles, puis sélectionnez **Ajouter un nouvel élément** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="054a7-129">In **Solution Explorer**, right-click your control library project and select **Add New Item** from the shortcut menu.</span></span>

6. <span data-ttu-id="054a7-130">Sélectionnez le modèle **Contrôle utilisateur hérité** dans la boîte de dialogue **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="054a7-130">Select the **Inherited User Control** template from the **Add New Item** dialog box.</span></span>

7. <span data-ttu-id="054a7-131">Dans la boîte de dialogue **Sélecteur d’héritage**, double-cliquez sur le contrôle dont vous voulez hériter.</span><span class="sxs-lookup"><span data-stu-id="054a7-131">In the **Inheritance Picker** dialog box, double-click the control you want to inherit from.</span></span>

     <span data-ttu-id="054a7-132">Un nouveau contrôle est ajouté à votre projet.</span><span class="sxs-lookup"><span data-stu-id="054a7-132">A new control is added to your project.</span></span>

8. <span data-ttu-id="054a7-133">Ouvrez le concepteur visuel du nouveau contrôle et ajoutez d’autres contrôles constitutifs.</span><span class="sxs-lookup"><span data-stu-id="054a7-133">Open the visual designer for the new control and add additional constituent controls.</span></span>

     <span data-ttu-id="054a7-134">Vous pouvez voir les contrôles constitutifs hérités du contrôle composite dans votre DLL, et vous pouvez modifier les propriétés des contrôles dont la propriété **Modifiers** est définie sur **Public**.</span><span class="sxs-lookup"><span data-stu-id="054a7-134">You can see the constituent controls that were inherited from the composite control in your DLL, and you can alter the properties of controls whose **Modifiers** property is **Public**.</span></span> <span data-ttu-id="054a7-135">Vous ne pouvez pas modifier les propriétés du contrôle dont la propriété **Modifiers** est définie sur **Private**.</span><span class="sxs-lookup"><span data-stu-id="054a7-135">You cannot change the properties of the control whose **Modifiers** property is **Private**.</span></span>

## <a name="see-also"></a><span data-ttu-id="054a7-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="054a7-136">See also</span></span>

- [<span data-ttu-id="054a7-137">Procédure pas à pas : création d’un contrôle composite</span><span class="sxs-lookup"><span data-stu-id="054a7-137">Walkthrough: Authoring a Composite Control</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [<span data-ttu-id="054a7-138">Procédure pas à pas : héritage d’un contrôle Windows Forms</span><span class="sxs-lookup"><span data-stu-id="054a7-138">Walkthrough: Inheriting from a Windows Forms Control</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)
- [<span data-ttu-id="054a7-139">Recommandations relatives au type de contrôle</span><span class="sxs-lookup"><span data-stu-id="054a7-139">Control Type Recommendations</span></span>](control-type-recommendations.md)
- [<span data-ttu-id="054a7-140">Guide pratique pour créer des contrôles pour des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="054a7-140">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="054a7-141">Variétés de contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="054a7-141">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
