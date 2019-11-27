---
title: 'Procédure pas à pas : création d’objets COM'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 5d00aff07358a0c40159fde9c12c70e0842d848b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338617"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="1045c-102">Procédure pas à pas : création d'objets COM avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1045c-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>
<span data-ttu-id="1045c-103">Lors de la création d’applications ou de composants, il est préférable de créer des assemblys .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1045c-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="1045c-104">Toutefois, Visual Basic permet également d’exposer facilement un composant .NET Framework à COM.</span><span class="sxs-lookup"><span data-stu-id="1045c-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="1045c-105">Cela vous permet de fournir de nouveaux composants pour les suites d’applications antérieures qui requièrent des composants COM.</span><span class="sxs-lookup"><span data-stu-id="1045c-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="1045c-106">Cette procédure pas à pas montre comment utiliser Visual Basic pour exposer des objets .NET Framework en tant qu’objets COM, avec et sans le modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="1045c-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="1045c-107">Le moyen le plus simple d’exposer des objets COM consiste à utiliser le modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="1045c-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="1045c-108">Le modèle de classe COM crée une nouvelle classe, puis configure votre projet pour générer la couche d’interopérabilité et la classe en tant qu’objet COM et l’inscrire auprès du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="1045c-108">The COM class template creates a new class, and then configures your project to generate the class and interoperability layer as a COM object and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1045c-109">Bien que vous puissiez également exposer une classe créée dans Visual Basic en tant qu’objet COM pour le code non managé à utiliser, il ne s’agit pas d’un objet COM réel et ne peut pas être utilisé par Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1045c-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="1045c-110">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="1045c-110">For more information, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="1045c-111">Pour créer un objet COM à l’aide du modèle de classe COM</span><span class="sxs-lookup"><span data-stu-id="1045c-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="1045c-112">Ouvrez un nouveau projet d’application Windows à partir du menu **fichier** en cliquant sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="1045c-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="1045c-113">Dans la boîte de dialogue **nouveau projet** , sous le champ **types de projets** , vérifiez que Windows est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="1045c-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="1045c-114">Sélectionnez **bibliothèque de classes** dans la liste **modèles** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1045c-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="1045c-115">Le nouveau projet s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1045c-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="1045c-116">Dans le menu **projet** , sélectionnez **Ajouter un nouvel élément** .</span><span class="sxs-lookup"><span data-stu-id="1045c-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="1045c-117">La boîte de dialogue **Ajouter un nouvel élément** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1045c-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="1045c-118">Sélectionnez **classe com** dans la liste **modèles** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="1045c-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="1045c-119">Visual Basic ajoute une nouvelle classe et configure le nouveau projet pour COM Interop.</span><span class="sxs-lookup"><span data-stu-id="1045c-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="1045c-120">Ajoutez du code, tel que des propriétés, des méthodes et des événements, à la classe COM.</span><span class="sxs-lookup"><span data-stu-id="1045c-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="1045c-121">Sélectionnez **générer ClassLibrary1** dans le menu **générer** .</span><span class="sxs-lookup"><span data-stu-id="1045c-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="1045c-122">Visual Basic génère l’assembly et inscrit l’objet COM auprès du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="1045c-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="1045c-123">Création d’objets COM sans le modèle de classe COM</span><span class="sxs-lookup"><span data-stu-id="1045c-123">Creating COM Objects without the COM Class Template</span></span>  
 <span data-ttu-id="1045c-124">Vous pouvez également créer une classe COM manuellement au lieu d’utiliser le modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="1045c-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="1045c-125">Cette procédure est utile lorsque vous travaillez à partir de la ligne de commande ou lorsque vous souhaitez plus de contrôle sur la façon dont les objets COM sont définis.</span><span class="sxs-lookup"><span data-stu-id="1045c-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="1045c-126">Pour configurer votre projet afin de générer un objet COM</span><span class="sxs-lookup"><span data-stu-id="1045c-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="1045c-127">Ouvrez un nouveau projet d’application Windows à partir du menu **fichier** en cliquant sur **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="1045c-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="1045c-128">Dans la boîte de dialogue **nouveau projet** , sous le champ **types de projets** , vérifiez que Windows est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="1045c-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="1045c-129">Sélectionnez **bibliothèque de classes** dans la liste **modèles** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1045c-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="1045c-130">Le nouveau projet s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1045c-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="1045c-131">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1045c-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="1045c-132">Le **Concepteur de projets** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1045c-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="1045c-133">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="1045c-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="1045c-134">Activez la case à cocher **inscrire pour COM Interop** .</span><span class="sxs-lookup"><span data-stu-id="1045c-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="1045c-135">Pour configurer le code de votre classe afin de créer un objet COM</span><span class="sxs-lookup"><span data-stu-id="1045c-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="1045c-136">Dans **Explorateur de solutions**, double-cliquez sur **Class1. vb** pour afficher son code.</span><span class="sxs-lookup"><span data-stu-id="1045c-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="1045c-137">Renommez la classe `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="1045c-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="1045c-138">Ajoutez les constantes suivantes à `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="1045c-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="1045c-139">Ils stockent les constantes d’identificateur global unique (GUID) que les objets COM doivent avoir.</span><span class="sxs-lookup"><span data-stu-id="1045c-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="1045c-140">Dans le menu **Outils**, cliquez sur **Créer un Guid**.</span><span class="sxs-lookup"><span data-stu-id="1045c-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="1045c-141">Dans la boîte de dialogue **Créer un Guid**, cliquez sur **Format du Registre**, puis sur **Copier**.</span><span class="sxs-lookup"><span data-stu-id="1045c-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="1045c-142">Cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="1045c-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="1045c-143">Remplacez la chaîne vide du `ClassId` par le GUID, en supprimant les accolades de début et de fin.</span><span class="sxs-lookup"><span data-stu-id="1045c-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="1045c-144">Par exemple, si le GUID fourni par Guidgen est `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`, votre code doit se présenter comme suit.</span><span class="sxs-lookup"><span data-stu-id="1045c-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="1045c-145">Répétez les étapes précédentes pour les constantes `InterfaceId` et `EventsId`, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1045c-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="1045c-146">Assurez-vous que les GUID sont nouveaux et uniques. dans le cas contraire, votre composant COM risque d’entrer en conflit avec d’autres composants COM.</span><span class="sxs-lookup"><span data-stu-id="1045c-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="1045c-147">Ajoutez l’attribut `ComClass` à `ComClass1`, en spécifiant les GUID pour l’ID de classe, l’ID d’interface et l’ID des événements, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1045c-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="1045c-148">Les classes COM doivent avoir un constructeur `Public Sub New()` sans paramètre ou la classe ne sera pas inscrite correctement.</span><span class="sxs-lookup"><span data-stu-id="1045c-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="1045c-149">Ajoutez un constructeur sans paramètre à la classe :</span><span class="sxs-lookup"><span data-stu-id="1045c-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="1045c-150">Ajoutez des propriétés, des méthodes et des événements à la classe, en la terminant par une instruction `End Class`.</span><span class="sxs-lookup"><span data-stu-id="1045c-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="1045c-151">Dans le menu **générer** , sélectionnez **générer la solution** .</span><span class="sxs-lookup"><span data-stu-id="1045c-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="1045c-152">Visual Basic génère l’assembly et inscrit l’objet COM auprès du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="1045c-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1045c-153">Les objets COM que vous générez avec Visual Basic ne peuvent pas être utilisés par d’autres applications Visual Basic, car il ne s’agit pas d’objets COM véritables.</span><span class="sxs-lookup"><span data-stu-id="1045c-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="1045c-154">Toute tentative d’ajout de références à ces objets COM génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="1045c-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="1045c-155">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="1045c-155">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1045c-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1045c-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="1045c-157">COM Interop</span><span class="sxs-lookup"><span data-stu-id="1045c-157">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="1045c-158">Procédure pas à pas : implémentation de l’héritage avec les objets COM</span><span class="sxs-lookup"><span data-stu-id="1045c-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="1045c-159">#Region (directive)</span><span class="sxs-lookup"><span data-stu-id="1045c-159">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="1045c-160">Interopérabilité COM dans les applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1045c-160">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="1045c-161">Dépannage des problèmes liés à l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="1045c-161">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
