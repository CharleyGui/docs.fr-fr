---
title: 'Procédure pas à pas : Incorporer des types d’assemblys managés dans Visual Studio'
description: Cette procédure pas à pas vous montre comment incorporer des types à partir d’assemblys managés dans .NET à l’aide de Visual Studio. Les types incorporés peuvent prendre en charge l’indépendance des versions.
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 636e5f8095b64cd0f445555c96d00945ccf7eaf8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378989"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="d7974-104">Procédure pas à pas : Incorporer des types d’assemblys managés dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d7974-104">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="d7974-105">Si vous incorporez des informations de type d’un assembly managé avec nom fort, vous pouvez coupler faiblement des types dans une application pour obtenir une indépendance de version.</span><span class="sxs-lookup"><span data-stu-id="d7974-105">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="d7974-106">Autrement dit, votre programme peut être écrit pour utiliser des types à partir de n’importe quelle version d’une bibliothèque managée sans devoir être recompilé pour chaque nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="d7974-106">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="d7974-107">L’incorporation de type est fréquemment utilisée avec COM Interop, par exemple pour une application qui utilise des objets Automation de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="d7974-107">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="d7974-108">L’incorporation des informations de type permet à la même build d’un programme de fonctionner avec différentes versions de Microsoft Office sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="d7974-108">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="d7974-109">Toutefois, vous pouvez également utiliser l’incorporation de type avec des solutions entièrement managées.</span><span class="sxs-lookup"><span data-stu-id="d7974-109">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="d7974-110">Une fois que vous avez spécifié les interfaces publiques qui peuvent être incorporées, vous créez des classes d’exécution qui implémentent ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="d7974-110">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="d7974-111">Un programme client peut incorporer les informations de type pour les interfaces au moment du design en référençant l’assembly qui contient les interfaces publiques et en affectant `Embed Interop Types` à la propriété de la référence la valeur `True` .</span><span class="sxs-lookup"><span data-stu-id="d7974-111">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="d7974-112">Le programme client peut ensuite charger les instances des objets de Runtime tapés comme ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="d7974-112">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="d7974-113">Cela équivaut à utiliser le compilateur de ligne de commande et à référencer l’assembly à l’aide de l' [option de compilateur-Link](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="d7974-113">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="d7974-114">Si vous créez une nouvelle version de votre assembly de Runtime avec nom fort, le programme client n’a pas besoin d’être recompilé.</span><span class="sxs-lookup"><span data-stu-id="d7974-114">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="d7974-115">Le programme client continue à utiliser la version de l’assembly de Runtime qui lui est accessible, à l’aide des informations de type incorporées pour les interfaces publiques.</span><span class="sxs-lookup"><span data-stu-id="d7974-115">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="d7974-116">Lors de cette procédure pas à pas, vous allez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d7974-116">In this walkthrough, you:</span></span>

1. <span data-ttu-id="d7974-117">Créez un assembly avec nom fort avec une interface publique contenant les informations de type qui peuvent être incorporées.</span><span class="sxs-lookup"><span data-stu-id="d7974-117">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="d7974-118">Créez un assembly de Runtime avec nom fort qui implémente l’interface publique.</span><span class="sxs-lookup"><span data-stu-id="d7974-118">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="d7974-119">Créer un programme client qui incorpore les informations de type de l’interface publique et crée une instance de la classe à partir de l’assembly runtime.</span><span class="sxs-lookup"><span data-stu-id="d7974-119">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="d7974-120">Modifier et régénérer l’assembly runtime.</span><span class="sxs-lookup"><span data-stu-id="d7974-120">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="d7974-121">Exécutez le programme client pour voir qu’il utilise la nouvelle version de l’assembly du runtime sans devoir être recompilé.</span><span class="sxs-lookup"><span data-stu-id="d7974-121">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="d7974-122">Conditions et limitations</span><span class="sxs-lookup"><span data-stu-id="d7974-122">Conditions and limitations</span></span>

<span data-ttu-id="d7974-123">Vous pouvez incorporer des informations de type à partir d’un assembly dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="d7974-123">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="d7974-124">L’assembly expose au moins une interface publique.</span><span class="sxs-lookup"><span data-stu-id="d7974-124">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="d7974-125">Les interfaces incorporées sont annotées avec des `ComImport` attributs et `Guid` des attributs avec des GUID uniques.</span><span class="sxs-lookup"><span data-stu-id="d7974-125">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="d7974-126">L’assembly est annoté avec l’attribut `ImportedFromTypeLib` ou l’attribut `PrimaryInteropAssembly` et un attribut `Guid` au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d7974-126">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="d7974-127">Les modèles de projet Visual C# et Visual Basic incluent par défaut un attribut au niveau de l’assembly `Guid` .</span><span class="sxs-lookup"><span data-stu-id="d7974-127">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="d7974-128">Étant donné que la fonction principale de l’incorporation de type consiste à prendre en charge les assemblys COM Interop, les limitations suivantes s’appliquent quand vous incorporez des informations de type dans une solution entièrement managée :</span><span class="sxs-lookup"><span data-stu-id="d7974-128">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="d7974-129">Seuls les attributs spécifiques aux COM Interop sont incorporés.</span><span class="sxs-lookup"><span data-stu-id="d7974-129">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="d7974-130">Les autres attributs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="d7974-130">Other attributes are ignored.</span></span>
- <span data-ttu-id="d7974-131">Si un type utilise des paramètres génériques et que le type du paramètre générique est un type incorporé, ce type ne peut pas être utilisé dans les limites d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="d7974-131">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="d7974-132">Les exemples de franchissement d’une limite d’assembly incluent l’appel d’une méthode à partir d’un autre assembly ou la dérivation d’un type d’un type défini dans un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="d7974-132">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="d7974-133">Les constantes ne sont pas incorporées.</span><span class="sxs-lookup"><span data-stu-id="d7974-133">Constants are not embedded.</span></span>
- <span data-ttu-id="d7974-134">La classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ne prend pas en charge un type incorporé comme clé.</span><span class="sxs-lookup"><span data-stu-id="d7974-134">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="d7974-135">Vous pouvez implémenter votre propre type de dictionnaire pour prendre en charge un type incorporé comme clé.</span><span class="sxs-lookup"><span data-stu-id="d7974-135">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="d7974-136">Créer une interface</span><span class="sxs-lookup"><span data-stu-id="d7974-136">Create an interface</span></span>

<span data-ttu-id="d7974-137">La première étape consiste à créer l’assembly de l’interface d’équivalence de type.</span><span class="sxs-lookup"><span data-stu-id="d7974-137">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="d7974-138">Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="d7974-138">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="d7974-139">Dans la boîte de dialogue **créer un nouveau projet** , tapez *bibliothèque de classes* dans la zone **Rechercher des modèles** .</span><span class="sxs-lookup"><span data-stu-id="d7974-139">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="d7974-140">Sélectionnez le modèle de bibliothèque de classes C# ou Visual Basic **(.NET Framework)** dans la liste, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="d7974-140">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="d7974-141">Dans la boîte de dialogue **configurer votre nouveau projet** , sous **nom du projet**, tapez *TypeEquivalenceInterface*, puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="d7974-141">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="d7974-142">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="d7974-142">The new project is created.</span></span>

1. <span data-ttu-id="d7974-143">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Class1.cs* ou *Class1. vb* , sélectionnez **Renommer**, puis renommez le fichier de *Class1* en *ISampleInterface*.</span><span class="sxs-lookup"><span data-stu-id="d7974-143">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="d7974-144">Répondez **Oui** à l’invite pour renommer la classe en `ISampleInterface` .</span><span class="sxs-lookup"><span data-stu-id="d7974-144">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="d7974-145">Cette classe représente l’interface publique de la classe.</span><span class="sxs-lookup"><span data-stu-id="d7974-145">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="d7974-146">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** , puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d7974-146">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="d7974-147">Sélectionnez **Build** dans le volet gauche de l’écran **Propriétés** , puis définissez le **chemin de sortie** sur un emplacement sur votre ordinateur, par exemple *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="d7974-147">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="d7974-148">Vous utilisez le même emplacement dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="d7974-148">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="d7974-149">Sélectionnez **signature** dans le volet gauche de l’écran **Propriétés** , puis activez la case à cocher **signer l’assembly** .</span><span class="sxs-lookup"><span data-stu-id="d7974-149">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="d7974-150">Dans la liste déroulante **choisir un fichier de clé de nom fort**, sélectionnez **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="d7974-150">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="d7974-151">Dans la boîte de dialogue **créer une clé de nom fort** , sous **nom du fichier de clé**, tapez *Key. snk*.</span><span class="sxs-lookup"><span data-stu-id="d7974-151">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="d7974-152">Désactivez la case à cocher **protéger le fichier de clé avec un mot de passe** , puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7974-152">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="d7974-153">Ouvrez le fichier de la classe *ISampleInterface* dans l’éditeur de code, puis remplacez son contenu par le code suivant pour créer l' `ISampleInterface` interface :</span><span class="sxs-lookup"><span data-stu-id="d7974-153">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

   ```csharp
   using System;
   using System.Runtime.InteropServices;

   namespace TypeEquivalenceInterface
   {
       [ComImport]
       [Guid("8DA56996-A151-4136-B474-32784559F6DF")]
       public interface ISampleInterface
       {
           void GetUserInput();
           string UserInput { get; }
       }
   }
   ```

   ```vb
   Imports System.Runtime.InteropServices

   <ComImport()>
   <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
   Public Interface ISampleInterface
       Sub GetUserInput()
       ReadOnly Property UserInput As String
   End Interface
   ```

1. <span data-ttu-id="d7974-154">Dans le menu **Outils** , sélectionnez **créer un GUID**, puis dans la boîte de dialogue créer un **GUID** , sélectionnez **format du Registre**.</span><span class="sxs-lookup"><span data-stu-id="d7974-154">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="d7974-155">Sélectionnez **copier**, puis **quitter**.</span><span class="sxs-lookup"><span data-stu-id="d7974-155">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="d7974-156">Dans l' `Guid` attribut de votre code, remplacez l’exemple de GUID par le GUID que vous avez copié et supprimez les accolades (**{}**).</span><span class="sxs-lookup"><span data-stu-id="d7974-156">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="d7974-157">Dans **Explorateur de solutions**, développez le dossier **Propriétés** et sélectionnez le fichier *AssemblyInfo.cs* ou *AssemblyInfo. vb* .</span><span class="sxs-lookup"><span data-stu-id="d7974-157">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="d7974-158">Dans l’éditeur de code, ajoutez l’attribut suivant au fichier :</span><span class="sxs-lookup"><span data-stu-id="d7974-158">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="d7974-159">Sélectionnez **fichier**  >  **enregistrer tout** ou appuyez sur **CTRL** + **MAJ** + **S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="d7974-159">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="d7974-160">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** , puis sélectionnez **générer**.</span><span class="sxs-lookup"><span data-stu-id="d7974-160">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="d7974-161">Le fichier DLL de la bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié, par exemple *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="d7974-161">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="d7974-162">Créer une classe d’exécution</span><span class="sxs-lookup"><span data-stu-id="d7974-162">Create a runtime class</span></span>

<span data-ttu-id="d7974-163">Ensuite, créez la classe d’exécution d’équivalence de type.</span><span class="sxs-lookup"><span data-stu-id="d7974-163">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="d7974-164">Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="d7974-164">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="d7974-165">Dans la boîte de dialogue **créer un nouveau projet** , tapez *bibliothèque de classes* dans la zone **Rechercher des modèles** .</span><span class="sxs-lookup"><span data-stu-id="d7974-165">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="d7974-166">Sélectionnez le modèle de bibliothèque de classes C# ou Visual Basic **(.NET Framework)** dans la liste, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="d7974-166">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="d7974-167">Dans la boîte de dialogue **configurer votre nouveau projet** , sous **nom du projet**, tapez *TypeEquivalenceRuntime*, puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="d7974-167">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="d7974-168">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="d7974-168">The new project is created.</span></span>

1. <span data-ttu-id="d7974-169">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Class1.cs* ou *Class1. vb* , sélectionnez **Renommer**, puis renommez le fichier de *Class1* en *SampleClass*.</span><span class="sxs-lookup"><span data-stu-id="d7974-169">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="d7974-170">Répondez **Oui** à l’invite pour renommer la classe en `SampleClass` .</span><span class="sxs-lookup"><span data-stu-id="d7974-170">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="d7974-171">Cette classe implémente l’interface `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="d7974-171">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="d7974-172">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d7974-172">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="d7974-173">Sélectionnez **Build** dans le volet gauche de l’écran **Propriétés** , puis définissez le **chemin de sortie** sur le même emplacement que celui que vous avez utilisé pour le projet TypeEquivalenceInterface, par exemple *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="d7974-173">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="d7974-174">Sélectionnez **signature** dans le volet gauche de l’écran **Propriétés** , puis activez la case à cocher **signer l’assembly** .</span><span class="sxs-lookup"><span data-stu-id="d7974-174">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="d7974-175">Dans la liste déroulante **choisir un fichier de clé de nom fort**, sélectionnez **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="d7974-175">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="d7974-176">Dans la boîte de dialogue **créer une clé de nom fort** , sous **nom du fichier de clé**, tapez *Key. snk*.</span><span class="sxs-lookup"><span data-stu-id="d7974-176">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="d7974-177">Désactivez la case à cocher **protéger le fichier de clé avec un mot de passe** , puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7974-177">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="d7974-178">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** , puis sélectionnez **Ajouter**une  >  **référence**.</span><span class="sxs-lookup"><span data-stu-id="d7974-178">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="d7974-179">Dans la boîte de dialogue **Gestionnaire de références** , sélectionnez **Parcourir** et accédez au dossier du chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="d7974-179">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="d7974-180">Sélectionnez le fichier *TypeEquivalenceInterface. dll* , sélectionnez **Ajouter**, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7974-180">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="d7974-181">Dans **Explorateur de solutions**, développez le dossier **références** et sélectionnez la référence **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="d7974-181">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="d7974-182">Dans le volet **Propriétés** , affectez à **version spécifique** la **valeur false** si ce n’est pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="d7974-182">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="d7974-183">Ouvrez le fichier de classe *SampleClass* dans l’éditeur de code, puis remplacez son contenu par le code suivant pour créer la `SampleClass` classe :</span><span class="sxs-lookup"><span data-stu-id="d7974-183">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

   ```csharp
   using System;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceRuntime
   {
       public class SampleClass : ISampleInterface
       {
           private string p_UserInput;
           public string UserInput { get { return p_UserInput; } }

           public void GetUserInput()
           {
               Console.WriteLine("Please enter a value:");
               p_UserInput = Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports TypeEquivalenceInterface

   Public Class SampleClass
       Implements ISampleInterface

       Private p_UserInput As String
       Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput
           Get
               Return p_UserInput
           End Get
       End Property

       Public Sub GetUserInput() Implements ISampleInterface.GetUserInput
           Console.WriteLine("Please enter a value:")
           p_UserInput = Console.ReadLine()
       End Sub
   End Class
   ```

1. <span data-ttu-id="d7974-184">Sélectionnez **fichier**  >  **enregistrer tout** ou appuyez sur **CTRL** + **MAJ** + **S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="d7974-184">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="d7974-185">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** et sélectionnez **générer**.</span><span class="sxs-lookup"><span data-stu-id="d7974-185">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="d7974-186">Le fichier DLL de la bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié.</span><span class="sxs-lookup"><span data-stu-id="d7974-186">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="d7974-187">Créer un projet client</span><span class="sxs-lookup"><span data-stu-id="d7974-187">Create a client project</span></span>

<span data-ttu-id="d7974-188">Enfin, créez un programme client d’équivalence de type qui référence l’assembly d’interface.</span><span class="sxs-lookup"><span data-stu-id="d7974-188">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="d7974-189">Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="d7974-189">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="d7974-190">Dans la boîte de dialogue **créer un nouveau projet** , tapez *console* dans la zone **Rechercher des modèles** .</span><span class="sxs-lookup"><span data-stu-id="d7974-190">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="d7974-191">Sélectionnez le modèle application console C# ou Visual Basic **(.NET Framework)** dans la liste, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="d7974-191">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="d7974-192">Dans la boîte de dialogue **configurer votre nouveau projet** , sous **nom du projet**, tapez *TypeEquivalenceClient,*, puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="d7974-192">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="d7974-193">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="d7974-193">The new project is created.</span></span>

1. <span data-ttu-id="d7974-194">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceClient,** , puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d7974-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="d7974-195">Sélectionnez **Build** dans le volet gauche de l’écran **Propriétés** , puis définissez le **chemin de sortie** sur le même emplacement que celui que vous avez utilisé pour le projet TypeEquivalenceInterface, par exemple *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="d7974-195">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="d7974-196">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceClient,** , puis sélectionnez **Ajouter**une  >  **référence**.</span><span class="sxs-lookup"><span data-stu-id="d7974-196">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="d7974-197">Dans la boîte de dialogue **Gestionnaire de références** , si le fichier **TypeEquivalenceInterface. dll** est déjà listé, sélectionnez-le.</span><span class="sxs-lookup"><span data-stu-id="d7974-197">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="d7974-198">Si ce n’est pas le cas, sélectionnez **Parcourir**, accédez au dossier du chemin de sortie, sélectionnez le fichier *TypeEquivalenceInterface. dll* (pas le fichier *TypeEquivalenceRuntime. dll*), puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d7974-198">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="d7974-199">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7974-199">Select **OK**.</span></span>

1. <span data-ttu-id="d7974-200">Dans **Explorateur de solutions**, développez le dossier **références** et sélectionnez la référence **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="d7974-200">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="d7974-201">Dans le volet **Propriétés** , affectez à **incorporer les types d’interopérabilité** la **valeur true**.</span><span class="sxs-lookup"><span data-stu-id="d7974-201">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="d7974-202">Ouvrez le fichier *Program.cs* ou *Module1. vb* dans l’éditeur de code, puis remplacez son contenu par le code suivant pour créer le programme client :</span><span class="sxs-lookup"><span data-stu-id="d7974-202">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

   ```csharp
   using System;
   using System.Reflection;
   using TypeEquivalenceInterface;

   namespace TypeEquivalenceClient
   {
       class Program
       {
           static void Main(string[] args)
           {
               Assembly sampleAssembly = Assembly.Load("TypeEquivalenceRuntime");
               ISampleInterface sampleClass =
                   (ISampleInterface)sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass");
               sampleClass.GetUserInput();
               Console.WriteLine(sampleClass.UserInput);
               Console.WriteLine(sampleAssembly.GetName().Version.ToString());
               Console.ReadLine();
           }
       }
   }
   ```

   ```vb
   Imports System.Reflection
   Imports TypeEquivalenceInterface

   Module Module1

       Sub Main()
           Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")
           Dim sampleClass As ISampleInterface = CType( _
               sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)
           sampleClass.GetUserInput()
           Console.WriteLine(sampleClass.UserInput)
           Console.WriteLine(sampleAssembly.GetName().Version)
           Console.ReadLine()
       End Sub

   End Module
   ```

1. <span data-ttu-id="d7974-203">Sélectionnez **fichier**  >  **enregistrer tout** ou appuyez sur **CTRL** + **MAJ** + **S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="d7974-203">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="d7974-204">Appuyez sur **CTRL** + **F5** pour générer et exécuter le programme.</span><span class="sxs-lookup"><span data-stu-id="d7974-204">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="d7974-205">Notez que la sortie de la console retourne la version de l’assembly **1.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="d7974-205">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="d7974-206">Modifier l’interface</span><span class="sxs-lookup"><span data-stu-id="d7974-206">Modify the interface</span></span>

<span data-ttu-id="d7974-207">À présent, modifiez l’assembly d’interface et modifiez sa version.</span><span class="sxs-lookup"><span data-stu-id="d7974-207">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="d7974-208">Dans Visual Studio, sélectionnez **fichier**  >  **ouvrir**  >  un**projet/une solution**, puis ouvrez le projet **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="d7974-208">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="d7974-209">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d7974-209">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="d7974-210">Sélectionnez **application** dans le volet gauche de l’écran **Propriétés** , puis sélectionnez informations de l' **assembly**.</span><span class="sxs-lookup"><span data-stu-id="d7974-210">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="d7974-211">Dans la boîte de dialogue informations de l' **assembly** , modifiez les valeurs version de l' **assembly** et **version du fichier** sur *2.0.0.0*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7974-211">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="d7974-212">Ouvrez le fichier *SampleInterface.cs* ou *SampleInterface. vb* et ajoutez la ligne de code suivante à l' `ISampleInterface` interface :</span><span class="sxs-lookup"><span data-stu-id="d7974-212">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="d7974-213">Sélectionnez **fichier**  >  **enregistrer tout** ou appuyez sur **CTRL** + **MAJ** + **S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="d7974-213">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="d7974-214">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** , puis sélectionnez **générer**.</span><span class="sxs-lookup"><span data-stu-id="d7974-214">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="d7974-215">Une nouvelle version du fichier DLL de la bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération.</span><span class="sxs-lookup"><span data-stu-id="d7974-215">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="d7974-216">Modifier la classe d’exécution</span><span class="sxs-lookup"><span data-stu-id="d7974-216">Modify the runtime class</span></span>

<span data-ttu-id="d7974-217">Modifiez également la classe Runtime et mettez à jour sa version.</span><span class="sxs-lookup"><span data-stu-id="d7974-217">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="d7974-218">Dans Visual Studio, sélectionnez **fichier**  >  **ouvrir**  >  un**projet/une solution**, puis ouvrez le projet **TypeEquivalenceRuntime** .</span><span class="sxs-lookup"><span data-stu-id="d7974-218">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="d7974-219">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d7974-219">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="d7974-220">Sélectionnez **application** dans le volet gauche de l’écran **Propriétés** , puis sélectionnez informations de l' **assembly**.</span><span class="sxs-lookup"><span data-stu-id="d7974-220">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="d7974-221">Dans la boîte de dialogue informations de l' **assembly** , modifiez les valeurs version de l' **assembly** et **version du fichier** sur *2.0.0.0*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="d7974-221">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="d7974-222">Ouvrez le fichier *SampleClass.cs* ou *SampleClass. vb* , puis ajoutez le code suivant à la `SampleClass` classe :</span><span class="sxs-lookup"><span data-stu-id="d7974-222">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

   ```csharp
    public DateTime GetDate()
    {
        return DateTime.Now;
    }
   ```

   ```vb
   Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
       Return Now
   End Function
   ```

1. <span data-ttu-id="d7974-223">Sélectionnez **fichier**  >  **enregistrer tout** ou appuyez sur **CTRL** + **MAJ** + **S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="d7974-223">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="d7974-224">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** et sélectionnez **générer**.</span><span class="sxs-lookup"><span data-stu-id="d7974-224">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="d7974-225">Une nouvelle version du fichier DLL de la bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération.</span><span class="sxs-lookup"><span data-stu-id="d7974-225">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="d7974-226">Exécuter le programme client mis à jour</span><span class="sxs-lookup"><span data-stu-id="d7974-226">Run the updated client program</span></span>

<span data-ttu-id="d7974-227">Accédez à l’emplacement du dossier de sortie de la génération et exécutez *TypeEquivalenceClient,. exe*.</span><span class="sxs-lookup"><span data-stu-id="d7974-227">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="d7974-228">Notez que la sortie de la console reflète désormais la nouvelle version de l' `TypeEquivalenceRuntime` assembly, *2.0.0.0*, sans le programme en cours de recompilation.</span><span class="sxs-lookup"><span data-stu-id="d7974-228">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7974-229">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7974-229">See also</span></span>

- [<span data-ttu-id="d7974-230">-link (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="d7974-230">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="d7974-231">-Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7974-231">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="d7974-232">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="d7974-232">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d7974-233">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d7974-233">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="d7974-234">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="d7974-234">Assemblies in .NET</span></span>](index.md)
