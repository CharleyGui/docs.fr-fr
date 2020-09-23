---
title: 'Procédure pas à pas : Création d’objets COM'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 90a21b70b45902a9f4fd559a97e777f26043fffb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075614"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a><span data-ttu-id="1dd26-102">Procédure pas à pas : création d'objets COM avec Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dd26-102">Walkthrough: Creating COM Objects with Visual Basic</span></span>

<span data-ttu-id="1dd26-103">Lors de la création d’applications ou de composants, il est préférable de créer des assemblys .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1dd26-103">When creating new applications or components, it is best to create .NET Framework assemblies.</span></span> <span data-ttu-id="1dd26-104">Toutefois, Visual Basic permet également d’exposer facilement un composant .NET Framework à COM.</span><span class="sxs-lookup"><span data-stu-id="1dd26-104">However, Visual Basic also makes it easy to expose a .NET Framework component to COM.</span></span> <span data-ttu-id="1dd26-105">Cela vous permet de fournir de nouveaux composants pour les suites d’applications antérieures qui requièrent des composants COM.</span><span class="sxs-lookup"><span data-stu-id="1dd26-105">This enables you to provide new components for earlier application suites that require COM components.</span></span> <span data-ttu-id="1dd26-106">Cette procédure pas à pas montre comment utiliser Visual Basic pour exposer des objets .NET Framework en tant qu’objets COM, avec et sans le modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="1dd26-106">This walkthrough demonstrates how to use Visual Basic to expose .NET Framework objects as COM objects, both with and without the COM class template.</span></span>  
  
 <span data-ttu-id="1dd26-107">Le moyen le plus simple d’exposer des objets COM consiste à utiliser le modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="1dd26-107">The easiest way to expose COM objects is by using the COM class template.</span></span> <span data-ttu-id="1dd26-108">Ce modèle crée une nouvelle classe, configure votre projet pour générer la classe avec une couche d’interopérabilité comme un objet COM et l’enregistre auprès du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="1dd26-108">This template creates a new class, then configures your project to generate the class with an interoperability layer as a COM object, and register it with the operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1dd26-109">Bien que vous puissiez également exposer une classe créée dans Visual Basic en tant qu’objet COM pour le code non managé à utiliser, il ne s’agit pas d’un objet COM réel et ne peut pas être utilisé par Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1dd26-109">Although you can also expose a class created in Visual Basic as a COM object for unmanaged code to use, it is not a true COM object and cannot be used by Visual Basic.</span></span> <span data-ttu-id="1dd26-110">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="1dd26-110">For more information, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a><span data-ttu-id="1dd26-111">Pour créer un objet COM à l’aide du modèle de classe COM</span><span class="sxs-lookup"><span data-stu-id="1dd26-111">To create a COM object by using the COM class template</span></span>  
  
1. <span data-ttu-id="1dd26-112">Ouvrez un nouveau projet d’application Windows à partir du menu **fichier** en cliquant sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="1dd26-112">Open a new Windows Application project from the **File** menu by clicking **New Project**.</span></span>  
  
2. <span data-ttu-id="1dd26-113">Dans la boîte de dialogue **nouveau projet** , sous le champ **types de projets** , vérifiez que Windows est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="1dd26-113">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="1dd26-114">Sélectionnez **bibliothèque de classes** dans la liste **modèles** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1dd26-114">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="1dd26-115">Le nouveau projet s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1dd26-115">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="1dd26-116">Dans le menu **projet** , sélectionnez **Ajouter un nouvel élément** .</span><span class="sxs-lookup"><span data-stu-id="1dd26-116">Select **Add New Item** from the **Project** menu.</span></span> <span data-ttu-id="1dd26-117">La boîte de dialogue **Ajouter un nouvel élément** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1dd26-117">The **Add New Item** dialog box is displayed.</span></span>  
  
4. <span data-ttu-id="1dd26-118">Sélectionnez **classe com** dans la liste **modèles** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="1dd26-118">Select **COM Class** from the **Templates** list, and then click **Add**.</span></span> <span data-ttu-id="1dd26-119">Visual Basic ajoute une nouvelle classe et configure le nouveau projet pour COM Interop.</span><span class="sxs-lookup"><span data-stu-id="1dd26-119">Visual Basic adds a new class and configures the new project for COM interop.</span></span>  
  
5. <span data-ttu-id="1dd26-120">Ajoutez du code, tel que des propriétés, des méthodes et des événements, à la classe COM.</span><span class="sxs-lookup"><span data-stu-id="1dd26-120">Add code such as properties, methods, and events to the COM class.</span></span>  
  
6. <span data-ttu-id="1dd26-121">Sélectionnez **générer ClassLibrary1** dans le menu **générer** .</span><span class="sxs-lookup"><span data-stu-id="1dd26-121">Select **Build ClassLibrary1** from the **Build** menu.</span></span> <span data-ttu-id="1dd26-122">Visual Basic génère l’assembly et inscrit l’objet COM auprès du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="1dd26-122">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
## <a name="creating-com-objects-without-the-com-class-template"></a><span data-ttu-id="1dd26-123">Création d’objets COM sans le modèle de classe COM</span><span class="sxs-lookup"><span data-stu-id="1dd26-123">Creating COM Objects without the COM Class Template</span></span>  

 <span data-ttu-id="1dd26-124">Vous pouvez également créer une classe COM manuellement au lieu d’utiliser le modèle de classe COM.</span><span class="sxs-lookup"><span data-stu-id="1dd26-124">You can also create a COM class manually instead of using the COM class template.</span></span> <span data-ttu-id="1dd26-125">Cette procédure est utile lorsque vous travaillez à partir de la ligne de commande ou lorsque vous souhaitez plus de contrôle sur la façon dont les objets COM sont définis.</span><span class="sxs-lookup"><span data-stu-id="1dd26-125">This procedure is helpful when you are working from the command line or when you want more control over how COM objects are defined.</span></span>  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a><span data-ttu-id="1dd26-126">Pour configurer votre projet afin de générer un objet COM</span><span class="sxs-lookup"><span data-stu-id="1dd26-126">To set up your project to generate a COM object</span></span>  
  
1. <span data-ttu-id="1dd26-127">Ouvrez un nouveau projet d’application Windows à partir du menu **fichier** en cliquant sur **NewProject**.</span><span class="sxs-lookup"><span data-stu-id="1dd26-127">Open a new Windows Application project from the **File** menu by clicking **NewProject**.</span></span>  
  
2. <span data-ttu-id="1dd26-128">Dans la boîte de dialogue **nouveau projet** , sous le champ **types de projets** , vérifiez que Windows est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="1dd26-128">In the **New Project** dialog box under the **Project Types** field, check that Windows is selected.</span></span> <span data-ttu-id="1dd26-129">Sélectionnez **bibliothèque de classes** dans la liste **modèles** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1dd26-129">Select **Class Library** from the **Templates** list, and then click **OK**.</span></span> <span data-ttu-id="1dd26-130">Le nouveau projet s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1dd26-130">The new project is displayed.</span></span>  
  
3. <span data-ttu-id="1dd26-131">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1dd26-131">In **Solution Explorer**, right-click your project, and then click **Properties**.</span></span> <span data-ttu-id="1dd26-132">Le **Concepteur de projets** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="1dd26-132">The **Project Designer** is displayed.</span></span>  
  
4. <span data-ttu-id="1dd26-133">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="1dd26-133">Click the **Compile** tab.</span></span>  
  
5. <span data-ttu-id="1dd26-134">Activez la case à cocher **inscrire pour COM Interop** .</span><span class="sxs-lookup"><span data-stu-id="1dd26-134">Select the **Register for COM Interop** check box.</span></span>  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a><span data-ttu-id="1dd26-135">Pour configurer le code de votre classe afin de créer un objet COM</span><span class="sxs-lookup"><span data-stu-id="1dd26-135">To set up the code in your class to create a COM object</span></span>  
  
1. <span data-ttu-id="1dd26-136">Dans **Explorateur de solutions**, double-cliquez sur **Class1. vb** pour afficher son code.</span><span class="sxs-lookup"><span data-stu-id="1dd26-136">In **Solution Explorer**, double-click **Class1.vb** to display its code.</span></span>  
  
2. <span data-ttu-id="1dd26-137">Renommez la classe en `ComClass1`.</span><span class="sxs-lookup"><span data-stu-id="1dd26-137">Rename the class to `ComClass1`.</span></span>  
  
3. <span data-ttu-id="1dd26-138">Ajoutez les constantes suivantes à `ComClass1` .</span><span class="sxs-lookup"><span data-stu-id="1dd26-138">Add the following constants to `ComClass1`.</span></span> <span data-ttu-id="1dd26-139">Ils stockent les constantes d’identificateur global unique (GUID) que les objets COM doivent avoir.</span><span class="sxs-lookup"><span data-stu-id="1dd26-139">They will store the Globally Unique Identifier (GUID) constants that the COM objects are required to have.</span></span>  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="1dd26-140">Dans le menu **Outils**, cliquez sur **Créer un Guid**.</span><span class="sxs-lookup"><span data-stu-id="1dd26-140">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="1dd26-141">Dans la boîte de dialogue **Créer un Guid**, cliquez sur **Format du Registre**, puis sur **Copier**.</span><span class="sxs-lookup"><span data-stu-id="1dd26-141">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="1dd26-142">Cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="1dd26-142">Click **Exit**.</span></span>  
  
5. <span data-ttu-id="1dd26-143">Remplacez la chaîne vide pour `ClassId` par le GUID, en supprimant les accolades de début et de fin.</span><span class="sxs-lookup"><span data-stu-id="1dd26-143">Replace the empty string for the `ClassId` with the GUID, removing the leading and trailing braces.</span></span> <span data-ttu-id="1dd26-144">Par exemple, si le GUID fourni par Guidgen est, `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` votre code doit se présenter comme suit.</span><span class="sxs-lookup"><span data-stu-id="1dd26-144">For example, if the GUID provided by Guidgen is `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` then your code should appear as follows.</span></span>  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. <span data-ttu-id="1dd26-145">Répétez les étapes précédentes pour `InterfaceId` les `EventsId` constantes et, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1dd26-145">Repeat the previous steps for the `InterfaceId` and `EventsId` constants, as in the following example.</span></span>  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > <span data-ttu-id="1dd26-146">Assurez-vous que les GUID sont nouveaux et uniques. dans le cas contraire, votre composant COM risque d’entrer en conflit avec d’autres composants COM.</span><span class="sxs-lookup"><span data-stu-id="1dd26-146">Make sure that the GUIDs are new and unique; otherwise, your COM component could conflict with other COM components.</span></span>  
  
7. <span data-ttu-id="1dd26-147">Ajoutez l' `ComClass` attribut à `ComClass1` , en spécifiant les GUID pour l’ID de classe, l’ID d’interface et l’ID d’événements, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="1dd26-147">Add the `ComClass` attribute to `ComClass1`, specifying the GUIDs for the Class ID, Interface ID, and Events ID as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. <span data-ttu-id="1dd26-148">Les classes COM doivent avoir un constructeur sans paramètre `Public Sub New()` ou la classe ne sera pas inscrite correctement.</span><span class="sxs-lookup"><span data-stu-id="1dd26-148">COM classes must have a parameterless `Public Sub New()` constructor, or the class will not register correctly.</span></span> <span data-ttu-id="1dd26-149">Ajoutez un constructeur sans paramètre à la classe :</span><span class="sxs-lookup"><span data-stu-id="1dd26-149">Add a parameterless constructor to the class:</span></span>  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. <span data-ttu-id="1dd26-150">Ajoutez des propriétés, des méthodes et des événements à la classe, en la terminant par une `End Class` instruction.</span><span class="sxs-lookup"><span data-stu-id="1dd26-150">Add properties, methods, and events to the class, ending it with an `End Class` statement.</span></span> <span data-ttu-id="1dd26-151">Dans le menu **générer** , sélectionnez **générer la solution** .</span><span class="sxs-lookup"><span data-stu-id="1dd26-151">Select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="1dd26-152">Visual Basic génère l’assembly et inscrit l’objet COM auprès du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="1dd26-152">Visual Basic builds the assembly and registers the COM object with the operating system.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1dd26-153">Les objets COM que vous générez avec Visual Basic ne peuvent pas être utilisés par d’autres applications Visual Basic, car il ne s’agit pas d’objets COM véritables.</span><span class="sxs-lookup"><span data-stu-id="1dd26-153">The COM objects you generate with Visual Basic cannot be used by other Visual Basic applications because they are not true COM objects.</span></span> <span data-ttu-id="1dd26-154">Toute tentative d’ajout de références à ces objets COM génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="1dd26-154">Attempts to add references to such COM objects will raise an error.</span></span> <span data-ttu-id="1dd26-155">Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="1dd26-155">For details, see [COM Interoperability in .NET Framework Applications](com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd26-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dd26-156">See also</span></span>

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [<span data-ttu-id="1dd26-157">COM Interop</span><span class="sxs-lookup"><span data-stu-id="1dd26-157">COM Interop</span></span>](index.md)
- [<span data-ttu-id="1dd26-158">Procédure pas à pas : Implémentation de l’héritage avec les objets COM</span><span class="sxs-lookup"><span data-stu-id="1dd26-158">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="1dd26-159">#Region directive</span><span class="sxs-lookup"><span data-stu-id="1dd26-159">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="1dd26-160">Interopérabilité COM dans les applications .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1dd26-160">COM Interoperability in .NET Framework Applications</span></span>](com-interoperability-in-net-framework-applications.md)
- [<span data-ttu-id="1dd26-161">Dépannage de l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="1dd26-161">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
