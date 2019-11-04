---
title: Dépannage de la création de contrôles et de composants
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9ee9df41e6f0a4e37164760a2e40740e31530121
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459072"
---
# <a name="troubleshoot-control-and-component-authoring"></a><span data-ttu-id="28197-102">Résoudre les problèmes de création de contrôles et de composants</span><span class="sxs-lookup"><span data-stu-id="28197-102">Troubleshoot Control and Component Authoring</span></span>

<span data-ttu-id="28197-103">Cette rubrique répertorie les problèmes courants suivants qui se produisent lors du développement de composants et de contrôles :</span><span class="sxs-lookup"><span data-stu-id="28197-103">This topic lists the following common problems that arise when developing components and controls:</span></span>

- <span data-ttu-id="28197-104">Impossible d’ajouter le contrôle à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="28197-104">Cannot Add Control to Toolbox</span></span>

- <span data-ttu-id="28197-105">Impossible de déboguer le composant ou contrôle utilisateur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="28197-105">Cannot Debug the Windows Forms User Control or Component</span></span>

- <span data-ttu-id="28197-106">Un événement est généré deux fois dans le composant ou le contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="28197-106">Event Is Raised Twice in Inherited Control or Component</span></span>

- <span data-ttu-id="28197-107">Erreur au moment de la conception : « Impossible de créer le composant '*Nom du composant*' »</span><span class="sxs-lookup"><span data-stu-id="28197-107">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>

- <span data-ttu-id="28197-108">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="28197-108">STAThreadAttribute</span></span>

- <span data-ttu-id="28197-109">L’icône du composant n’apparaît pas dans la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="28197-109">Component Icon Does Not Appear in Toolbox</span></span>

## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="28197-110">Impossible d’ajouter le contrôle à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="28197-110">Cannot Add Control to Toolbox</span></span>

<span data-ttu-id="28197-111">Si vous souhaitez ajouter un contrôle personnalisé que vous avez créé dans un autre projet ou un contrôle tiers pour la **boîte à outils**, vous devez le faire manuellement.</span><span class="sxs-lookup"><span data-stu-id="28197-111">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="28197-112">Si le projet actuel contient votre contrôle ou composant, il doit apparaître automatiquement dans la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="28197-112">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="28197-113">Pour plus d’informations, consultez [Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="28197-113">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="28197-114">Pour ajouter un contrôle à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="28197-114">To add a control to the Toolbox</span></span>

1. <span data-ttu-id="28197-115">Cliquez avec le bouton droit sur la **boîte à outils** et sélectionnez **Choisir les éléments** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="28197-115">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>

2. <span data-ttu-id="28197-116">Dans la boîte de dialogue **Choisir des éléments de boîte à outils**, ajoutez le composant :</span><span class="sxs-lookup"><span data-stu-id="28197-116">In the **Choose Toolbox Items** dialog box, add the component:</span></span>

    - <span data-ttu-id="28197-117">Si vous souhaitez ajouter un contrôle ou un composant .NET Framework, cliquez sur l’onglet **Composants .NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="28197-117">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>

         <span data-ttu-id="28197-118">– ou –</span><span class="sxs-lookup"><span data-stu-id="28197-118">– or –</span></span>

    - <span data-ttu-id="28197-119">Si vous souhaitez ajouter un composant COM ou un contrôle ActiveX, cliquez sur l’onglet **Composants COM**.</span><span class="sxs-lookup"><span data-stu-id="28197-119">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>

3. <span data-ttu-id="28197-120">Si votre contrôle est répertorié dans la boîte de dialogue, vérifiez qu’il est sélectionné, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="28197-120">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>

     <span data-ttu-id="28197-121">Le contrôle est ajouté à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="28197-121">The control is added to the **Toolbox**.</span></span>

4. <span data-ttu-id="28197-122">Si votre contrôle n’est pas répertorié dans la boîte de dialogue, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="28197-122">If your control is not listed in the dialog box, do the following:</span></span>

    1. <span data-ttu-id="28197-123">Cliquez sur le bouton **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="28197-123">Click the **Browse** button.</span></span>

    2. <span data-ttu-id="28197-124">Accédez au dossier contenant le fichier .dll qui contient votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="28197-124">Browse to the folder that contains the .dll file that contains your control.</span></span>

    3. <span data-ttu-id="28197-125">Sélectionnez le fichier .dll et cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="28197-125">Select the .dll file and click **Open**.</span></span>

         <span data-ttu-id="28197-126">Votre contrôle s’affiche dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="28197-126">Your control appears in the dialog box.</span></span>

    4. <span data-ttu-id="28197-127">Vérifiez que votre contrôle est sélectionné, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="28197-127">Confirm that your control is selected, and then click **OK**.</span></span>

         <span data-ttu-id="28197-128">Le contrôle est ajouté à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="28197-128">Your control is added to the **Toolbox**.</span></span>

## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="28197-129">Impossible de déboguer le composant ou contrôle utilisateur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="28197-129">Cannot Debug the Windows Forms User Control or Component</span></span>

<span data-ttu-id="28197-130">Si votre contrôle dérive de la classe <xref:System.Windows.Forms.UserControl>, vous pouvez déboguer son comportement au moment de l’exécution avec le conteneur de test.</span><span class="sxs-lookup"><span data-stu-id="28197-130">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="28197-131">Pour plus d’informations, consultez l’article [Comment : tester le comportement d’un UserControl au moment de l’exécution](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="28197-131">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

<span data-ttu-id="28197-132">Les autres composants et contrôles personnalisés ne sont pas des projets autonomes.</span><span class="sxs-lookup"><span data-stu-id="28197-132">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="28197-133">Ils doivent être hébergés par une application, telle qu’un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="28197-133">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="28197-134">Pour déboguer un contrôle ou un composant, vous devez l’ajouter à un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="28197-134">To debug a control or component, you must add it to a Windows Forms project.</span></span>

### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="28197-135">Pour déboguer un contrôle ou un composant</span><span class="sxs-lookup"><span data-stu-id="28197-135">To debug a control or component</span></span>

1. <span data-ttu-id="28197-136">Dans le menu **Générer**, cliquez sur **Générer la solution** pour générer votre solution.</span><span class="sxs-lookup"><span data-stu-id="28197-136">From the **Build** menu, click **Build Solution** to build your solution.</span></span>

2. <span data-ttu-id="28197-137">Dans le menu **Fichier**, choisissez **Ajouter**, puis **Nouveau projet** pour ajouter un projet de test à votre application.</span><span class="sxs-lookup"><span data-stu-id="28197-137">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>

3. <span data-ttu-id="28197-138">Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez **Application Windows** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="28197-138">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>

4. <span data-ttu-id="28197-139">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="28197-139">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="28197-140">Dans le menu contextuel, cliquez sur **Ajouter une référence** pour ajouter une référence au projet contenant le contrôle ou le composant.</span><span class="sxs-lookup"><span data-stu-id="28197-140">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>

5. <span data-ttu-id="28197-141">Créez une instance de votre contrôle ou composant dans le projet de test.</span><span class="sxs-lookup"><span data-stu-id="28197-141">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="28197-142">Si votre composant se trouve dans la **boîte à outils**, vous pouvez le faire glisser vers votre aire de concepteur, ou vous pouvez créer l’instance par programmation, comme illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="28197-142">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>

    ```vb
    Dim Component1 As New MyNeatComponent()
    ```

    ```csharp
    MyNeatComponent Component1 = new MyNeatComponent();
    ```

   <span data-ttu-id="28197-143">Vous pouvez maintenant déboguer votre contrôle ou composant comme vous le faites habituellement.</span><span class="sxs-lookup"><span data-stu-id="28197-143">You can now debug your control or component as usual.</span></span>

<span data-ttu-id="28197-144">Pour plus d’informations sur le débogage, consultez les articles [Débogage dans Visual Studio](/visualstudio/debugger/debugger-feature-tour) et [Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="28197-144">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugger-feature-tour) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>

## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="28197-145">Un événement est généré deux fois dans le composant ou le contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="28197-145">Event Is Raised Twice in Inherited Control or Component</span></span>

<span data-ttu-id="28197-146">Cela est probablement dû à une clause `Handles` dupliquée.</span><span class="sxs-lookup"><span data-stu-id="28197-146">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="28197-147">Pour plus d’informations, consultez l’article [Dépannage des gestionnaires d’événements hérités dans Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="28197-147">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="28197-148">Erreur au moment de la conception : « Impossible de créer le composant 'Nom du composant' »</span><span class="sxs-lookup"><span data-stu-id="28197-148">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>

<span data-ttu-id="28197-149">Votre composant ou contrôle doit fournir un constructeur sans paramètre sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="28197-149">Your component or control must provide a parameterless constructor with no parameters.</span></span> <span data-ttu-id="28197-150">Lorsque l’environnement de design crée une instance de votre composant ou de votre contrôle, il n’essaie pas de fournir des paramètres aux surcharges de constructeur qui prennent des paramètres.</span><span class="sxs-lookup"><span data-stu-id="28197-150">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>

## <a name="stathreadattribute"></a><span data-ttu-id="28197-151">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="28197-151">STAThreadAttribute</span></span>

<span data-ttu-id="28197-152">Le <xref:System.STAThreadAttribute> informe le common language runtime (CLR) que Windows Forms utilise le modèle à thread unique cloisonné.</span><span class="sxs-lookup"><span data-stu-id="28197-152">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="28197-153">Vous pouvez constater un comportement inattendu si vous n’appliquez pas cet attribut à la méthode `Main` de votre application Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="28197-153">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="28197-154">Par exemple, les images d’arrière-plan peuvent ne pas apparaître pour les contrôles tels que <xref:System.Windows.Forms.ListView>.</span><span class="sxs-lookup"><span data-stu-id="28197-154">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="28197-155">Certains contrôles peuvent également avoir besoin de cet attribut pour fournir un comportement approprié de saisie semi-automatique et de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="28197-155">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>

## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="28197-156">L’icône du composant n’apparaît pas dans la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="28197-156">Component Icon Does Not Appear in Toolbox</span></span>

<span data-ttu-id="28197-157">Lorsque vous utilisez <xref:System.Drawing.ToolboxBitmapAttribute> pour associer une icône à votre composant personnalisé, la bitmap n’apparaît pas dans la boîte à outils pour les composants générés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="28197-157">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="28197-158">Pour afficher l’image bitmap, rechargez le contrôle par le biais de la boîte de dialogue **Choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="28197-158">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="28197-159">Pour plus d’informations, consultez l’article [Comment : fournir une image bitmap pour un contrôle en vue de l’afficher dans la boîte à outils](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span><span class="sxs-lookup"><span data-stu-id="28197-159">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="28197-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28197-160">See also</span></span>

- [<span data-ttu-id="28197-161">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="28197-161">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="28197-162">Procédure pas à pas : remplissage automatique de la boîte à outils avec des composants personnalisés</span><span class="sxs-lookup"><span data-stu-id="28197-162">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="28197-163">Comment : tester le comportement d’un UserControl au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="28197-163">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="28197-164">Procédure pas à pas : débogage des contrôles Windows Forms personnalisés au moment du design</span><span class="sxs-lookup"><span data-stu-id="28197-164">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
