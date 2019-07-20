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
ms.openlocfilehash: 6494a154b9b4bd5bf29fc0e2fbd0b4e5e84550ff
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364165"
---
# <a name="troubleshooting-control-and-component-authoring"></a><span data-ttu-id="89723-102">Dépannage de la création de contrôles et de composants</span><span class="sxs-lookup"><span data-stu-id="89723-102">Troubleshooting Control and Component Authoring</span></span>
<span data-ttu-id="89723-103">Cette rubrique répertorie les problèmes courants suivants qui surviennent lors du développement de composants et de contrôles.</span><span class="sxs-lookup"><span data-stu-id="89723-103">This topic lists the following common problems that arise when developing components and controls.</span></span> <span data-ttu-id="89723-104">Pour plus d’informations, consultez l’article [Programmation à l’aide de composants](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="89723-104">For more information, see [Programming with Components](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120)).</span></span>  
  
- <span data-ttu-id="89723-105">Impossible d’ajouter le contrôle à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="89723-105">Cannot Add Control to Toolbox</span></span>  
  
- <span data-ttu-id="89723-106">Impossible de déboguer le composant ou contrôle utilisateur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89723-106">Cannot Debug the Windows Forms User Control or Component</span></span>  
  
- <span data-ttu-id="89723-107">Un événement est généré deux fois dans le composant ou le contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="89723-107">Event Is Raised Twice in Inherited Control or Component</span></span>  
  
- <span data-ttu-id="89723-108">Erreur au moment de la conception: «Impossible de créer le composant'*nom du composant*'»</span><span class="sxs-lookup"><span data-stu-id="89723-108">Design-Time Error: "Failed to Create Component '*Component Name*'"</span></span>  
  
- <span data-ttu-id="89723-109">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="89723-109">STAThreadAttribute</span></span>  
  
- <span data-ttu-id="89723-110">L’icône du composant n’apparaît pas dans la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="89723-110">Component Icon Does Not Appear in Toolbox</span></span>  
  
## <a name="cannot-add-control-to-toolbox"></a><span data-ttu-id="89723-111">Impossible d’ajouter le contrôle à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="89723-111">Cannot Add Control to Toolbox</span></span>  
 <span data-ttu-id="89723-112">Si vous souhaitez ajouter un contrôle personnalisé que vous avez créé dans un autre projet ou un contrôle tiers pour la **boîte à outils**, vous devez le faire manuellement.</span><span class="sxs-lookup"><span data-stu-id="89723-112">If you want to add a custom control that you created in another project or a third-party control to the **Toolbox**, you must do so manually.</span></span> <span data-ttu-id="89723-113">Si le projet actuel contient votre contrôle ou composant, il doit apparaître automatiquement dans la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="89723-113">If the current project contains your control or component, it should appear in the **Toolbox** automatically.</span></span> <span data-ttu-id="89723-114">Pour plus d’informations, consultez [Procédure pas à pas : Remplissage automatique de la boîte à outils](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)avec des composants personnalisés.</span><span class="sxs-lookup"><span data-stu-id="89723-114">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
#### <a name="to-add-a-control-to-the-toolbox"></a><span data-ttu-id="89723-115">Pour ajouter un contrôle à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="89723-115">To add a control to the Toolbox</span></span>  
  
1. <span data-ttu-id="89723-116">Cliquez avec le bouton droit sur la **boîte à outils** et sélectionnez **Choisir les éléments** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="89723-116">Right-click the **Toolbox** and from the shortcut menu, select **Choose Items**.</span></span>  
  
2. <span data-ttu-id="89723-117">Dans la boîte de dialogue **Choisir des éléments de boîte à outils**, ajoutez le composant :</span><span class="sxs-lookup"><span data-stu-id="89723-117">In the **Choose Toolbox Items** dialog box, add the component:</span></span>  
  
    - <span data-ttu-id="89723-118">Si vous souhaitez ajouter un contrôle ou un composant .NET Framework, cliquez sur l’onglet **Composants .NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="89723-118">If you want to add a .NET Framework component or control, click the **.NET Framework Components** tab.</span></span>  
  
         <span data-ttu-id="89723-119">– ou –</span><span class="sxs-lookup"><span data-stu-id="89723-119">– or –</span></span>  
  
    - <span data-ttu-id="89723-120">Si vous souhaitez ajouter un composant COM ou un contrôle ActiveX, cliquez sur l’onglet **Composants COM**.</span><span class="sxs-lookup"><span data-stu-id="89723-120">If you want to add a COM component or ActiveX control, click the **COM Components** tab.</span></span>  
  
3. <span data-ttu-id="89723-121">Si votre contrôle est répertorié dans la boîte de dialogue, vérifiez qu’il est sélectionné, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="89723-121">If your control is listed in the dialog box, confirm it is selected, and then click **OK**.</span></span>  
  
     <span data-ttu-id="89723-122">Le contrôle est ajouté à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="89723-122">The control is added to the **Toolbox**.</span></span>  
  
4. <span data-ttu-id="89723-123">Si votre contrôle n’est pas répertorié dans la boîte de dialogue, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="89723-123">If your control is not listed in the dialog box, do the following:</span></span>  
  
    1. <span data-ttu-id="89723-124">Cliquez sur le bouton **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="89723-124">Click the **Browse** button.</span></span>  
  
    2. <span data-ttu-id="89723-125">Accédez au dossier contenant le fichier .dll qui contient votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="89723-125">Browse to the folder that contains the .dll file that contains your control.</span></span>  
  
    3. <span data-ttu-id="89723-126">Sélectionnez le fichier .dll et cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="89723-126">Select the .dll file and click **Open**.</span></span>  
  
         <span data-ttu-id="89723-127">Votre contrôle s’affiche dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="89723-127">Your control appears in the dialog box.</span></span>  
  
    4. <span data-ttu-id="89723-128">Vérifiez que votre contrôle est sélectionné, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="89723-128">Confirm that your control is selected, and then click **OK**.</span></span>  
  
         <span data-ttu-id="89723-129">Le contrôle est ajouté à la **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="89723-129">Your control is added to the **Toolbox**.</span></span>  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a><span data-ttu-id="89723-130">Impossible de déboguer le composant ou contrôle utilisateur Windows Forms</span><span class="sxs-lookup"><span data-stu-id="89723-130">Cannot Debug the Windows Forms User Control or Component</span></span>  
 <span data-ttu-id="89723-131">Si votre contrôle dérive de la <xref:System.Windows.Forms.UserControl> classe, vous pouvez déboguer son comportement au moment de l’exécution avec le conteneur de test.</span><span class="sxs-lookup"><span data-stu-id="89723-131">If your control derives from the <xref:System.Windows.Forms.UserControl> class, you can debug its run-time behavior with the test container.</span></span> <span data-ttu-id="89723-132">Pour plus d'informations, voir [Procédure : Tester le comportement d’un UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="89723-132">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
 <span data-ttu-id="89723-133">Les autres composants et contrôles personnalisés ne sont pas des projets autonomes.</span><span class="sxs-lookup"><span data-stu-id="89723-133">Other custom controls and components are not stand-alone projects.</span></span> <span data-ttu-id="89723-134">Ils doivent être hébergés par une application, telle qu’un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="89723-134">They must be hosted by an application such as a Windows Forms project.</span></span> <span data-ttu-id="89723-135">Pour déboguer un contrôle ou un composant, vous devez l’ajouter à un projet Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="89723-135">To debug a control or component, you must add it to a Windows Forms project.</span></span>  
  
#### <a name="to-debug-a-control-or-component"></a><span data-ttu-id="89723-136">Pour déboguer un contrôle ou un composant</span><span class="sxs-lookup"><span data-stu-id="89723-136">To debug a control or component</span></span>  
  
1. <span data-ttu-id="89723-137">Dans le menu **Générer**, cliquez sur **Générer la solution** pour générer votre solution.</span><span class="sxs-lookup"><span data-stu-id="89723-137">From the **Build** menu, click **Build Solution** to build your solution.</span></span>  
  
2. <span data-ttu-id="89723-138">Dans le menu **Fichier**, choisissez **Ajouter**, puis **Nouveau projet** pour ajouter un projet de test à votre application.</span><span class="sxs-lookup"><span data-stu-id="89723-138">From the **File** menu, choose **Add**, and then **New Project** to add a test project to your application.</span></span>  
  
3. <span data-ttu-id="89723-139">Dans la boîte de dialogue **Ajouter un nouveau projet**, sélectionnez **Application Windows** comme type de projet.</span><span class="sxs-lookup"><span data-stu-id="89723-139">In the **Add New Project** dialog box choose **Windows Application** for the type of project.</span></span>  
  
4. <span data-ttu-id="89723-140">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références** de votre nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="89723-140">In **Solution Explorer**, right-click the **References** node for the new project.</span></span> <span data-ttu-id="89723-141">Dans le menu contextuel, cliquez sur **Ajouter une référence** pour ajouter une référence au projet contenant le contrôle ou le composant.</span><span class="sxs-lookup"><span data-stu-id="89723-141">On the shortcut menu, click **Add Reference** to add a reference to the project containing the control or component.</span></span>  
  
5. <span data-ttu-id="89723-142">Créez une instance de votre contrôle ou composant dans le projet de test.</span><span class="sxs-lookup"><span data-stu-id="89723-142">Create an instance of your control or component in the test project.</span></span> <span data-ttu-id="89723-143">Si votre composant se trouve dans la **boîte à outils**, vous pouvez le faire glisser vers votre aire de concepteur, ou vous pouvez créer l’instance par programmation, comme illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="89723-143">If your component is in the **Toolbox**, you can drag it to your designer surface, or you can create the instance programmatically, as shown in the following code example.</span></span>  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     <span data-ttu-id="89723-144">Vous pouvez maintenant déboguer votre contrôle ou composant comme vous le faites habituellement.</span><span class="sxs-lookup"><span data-stu-id="89723-144">You can now debug your control or component as usual.</span></span>  
  
 <span data-ttu-id="89723-145">Pour plus d’informations sur le débogage, consultez débogage [dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) et [procédure pas à pas: Débogage des contrôles de Windows Forms personnalisés au moment](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)du Design.</span><span class="sxs-lookup"><span data-stu-id="89723-145">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio) and [Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md).</span></span>  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a><span data-ttu-id="89723-146">Un événement est généré deux fois dans le composant ou le contrôle hérité</span><span class="sxs-lookup"><span data-stu-id="89723-146">Event Is Raised Twice in Inherited Control or Component</span></span>  
 <span data-ttu-id="89723-147">Cela est probablement dû à une clause `Handles` dupliquée.</span><span class="sxs-lookup"><span data-stu-id="89723-147">This is likely due to a duplicated `Handles` clause.</span></span> <span data-ttu-id="89723-148">Pour plus d’informations, consultez l’article [Dépannage des gestionnaires d’événements hérités dans Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="89723-148">For more information, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a><span data-ttu-id="89723-149">Erreur au moment de la conception: «Impossible de créer le composant’nom du composant'»</span><span class="sxs-lookup"><span data-stu-id="89723-149">Design-Time Error: "Failed to Create Component 'Component Name'"</span></span>  
 <span data-ttu-id="89723-150">Votre composant ou contrôle doit fournir un constructeur sans paramètre sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="89723-150">Your component or control must provide a parameterless constructor with no parameters.</span></span> <span data-ttu-id="89723-151">Lorsque l’environnement de design crée une instance de votre composant ou de votre contrôle, il n’essaie pas de fournir des paramètres aux surcharges de constructeur qui prennent des paramètres.</span><span class="sxs-lookup"><span data-stu-id="89723-151">When the design environment creates an instance of your component or control, it does not attempt to provide any parameters to constructor overloads that take parameters.</span></span>  
  
## <a name="stathreadattribute"></a><span data-ttu-id="89723-152">STAThreadAttribute</span><span class="sxs-lookup"><span data-stu-id="89723-152">STAThreadAttribute</span></span>  
 <span data-ttu-id="89723-153"><xref:System.STAThreadAttribute> Informe le Common Language Runtime (CLR) qui Windows Forms utilise le modèle à thread unique cloisonné.</span><span class="sxs-lookup"><span data-stu-id="89723-153">The <xref:System.STAThreadAttribute> informs the common language runtime (CLR) that Windows Forms uses the single-threaded apartment model.</span></span> <span data-ttu-id="89723-154">Vous pouvez constater un comportement inattendu si vous n’appliquez pas cet attribut à la méthode `Main` de votre application Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="89723-154">You may notice unintended behavior if you do not apply this attribute to your Windows Forms application's `Main` method.</span></span> <span data-ttu-id="89723-155">Par exemple, les images d’arrière-plan peuvent ne <xref:System.Windows.Forms.ListView>pas apparaître pour les contrôles tels que.</span><span class="sxs-lookup"><span data-stu-id="89723-155">For example, background images may not appear for controls like <xref:System.Windows.Forms.ListView>.</span></span> <span data-ttu-id="89723-156">Certains contrôles peuvent également avoir besoin de cet attribut pour fournir un comportement approprié de saisie semi-automatique et de glisser-déplacer.</span><span class="sxs-lookup"><span data-stu-id="89723-156">Some controls may also require this attribute for correct AutoComplete and drag-and-drop behavior.</span></span>  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a><span data-ttu-id="89723-157">L’icône du composant n’apparaît pas dans la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="89723-157">Component Icon Does Not Appear in Toolbox</span></span>  
 <span data-ttu-id="89723-158">Lorsque vous utilisez <xref:System.Drawing.ToolboxBitmapAttribute> pour associer une icône à votre composant personnalisé, la bitmap n’apparaît pas dans la boîte à outils pour les composants générés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="89723-158">When you use <xref:System.Drawing.ToolboxBitmapAttribute> to associate an icon with your custom component, the bitmap does not appear in the Toolbox for autogenerated components.</span></span> <span data-ttu-id="89723-159">Pour afficher l’image bitmap, rechargez le contrôle par le biais de la boîte de dialogue **Choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="89723-159">To see the bitmap, reload the control by using the **Choose Toolbox Items** dialog box.</span></span> <span data-ttu-id="89723-160">Pour plus d’informations, consultez [Guide pratique pour Fournissez une image bitmap de boîte](how-to-provide-a-toolbox-bitmap-for-a-control.md)à outils pour un contrôle.</span><span class="sxs-lookup"><span data-stu-id="89723-160">For more information, see [How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89723-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89723-161">See also</span></span>

- [<span data-ttu-id="89723-162">Développement de contrôles Windows Forms au moment du design</span><span class="sxs-lookup"><span data-stu-id="89723-162">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
- [<span data-ttu-id="89723-163">Procédure pas à pas : Remplissage automatique de la boîte à outils avec des composants personnalisés</span><span class="sxs-lookup"><span data-stu-id="89723-163">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [<span data-ttu-id="89723-164">Guide pratique pour Tester le comportement d’un UserControl au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="89723-164">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="89723-165">Procédure pas à pas : Débogage des contrôles Windows Forms personnalisés au moment du design</span><span class="sxs-lookup"><span data-stu-id="89723-165">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- <span data-ttu-id="89723-166">[Création de composants](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="89723-166">[Component Authoring](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))</span></span>
- <span data-ttu-id="89723-167">[Dépannage du développement au moment du design](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="89723-167">[Troubleshooting Design-Time Development](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))</span></span>
