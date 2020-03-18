---
title: 'Procédure pas à pas : Intégrer les types d’assemblages gérés dans Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: f11fbedad766753ee462c5f597b823493cdaf7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75338554"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="c5570-102">Procédure pas à pas : Intégrer les types d’assemblages gérés dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c5570-102">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="c5570-103">Si vous incorporez des informations de type d’un assembly managé avec nom fort, vous pouvez coupler faiblement des types dans une application pour obtenir une indépendance de version.</span><span class="sxs-lookup"><span data-stu-id="c5570-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="c5570-104">Autrement dit, votre programme peut être écrit pour utiliser des types de n’importe quelle version d’une bibliothèque gérée sans avoir à être recompilé pour chaque nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="c5570-104">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="c5570-105">L’incorporation de type est fréquemment utilisée avec COM Interop, par exemple pour une application qui utilise des objets Automation de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="c5570-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="c5570-106">L’incorporation des informations de type permet à la même build d’un programme de fonctionner avec différentes versions de Microsoft Office sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="c5570-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="c5570-107">Cependant, vous pouvez également utiliser l’intégration de type avec des solutions entièrement gérées.</span><span class="sxs-lookup"><span data-stu-id="c5570-107">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="c5570-108">Après avoir spécifé les interfaces publiques qui peuvent être intégrées, vous créez des classes de temps d’exécution qui implémentent ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="c5570-108">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="c5570-109">Un programme client peut intégrer les informations de type pour les interfaces au moment de `Embed Interop Types` la conception `True`en faisant référence à l’assemblage qui contient les interfaces publiques et en définissant la propriété de la référence à .</span><span class="sxs-lookup"><span data-stu-id="c5570-109">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="c5570-110">Le programme client peut ensuite charger les instances des objets en temps d’exécution tapés comme ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="c5570-110">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="c5570-111">Cela équivaut à utiliser le compilateur de la ligne de commande et le référencement de l’assemblage en utilisant [l’option compilateur -lien](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="c5570-111">This is equivalent to using the command line compiler and referencing the assembly by using the [-link compiler option](../../csharp/language-reference/compiler-options/link-compiler-option.md).</span></span>

<span data-ttu-id="c5570-112">Si vous créez une nouvelle version de votre assemblage de temps d’exécution fort, le programme client n’a pas besoin d’être recompilé.</span><span class="sxs-lookup"><span data-stu-id="c5570-112">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="c5570-113">Le programme client continue d’utiliser n’importe quelle version de l’assemblage de temps d’exécution qui lui est disponible, en utilisant les informations de type intégrée pour les interfaces publiques.</span><span class="sxs-lookup"><span data-stu-id="c5570-113">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="c5570-114">Lors de cette procédure pas à pas, vous allez effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="c5570-114">In this walkthrough, you:</span></span>

1. <span data-ttu-id="c5570-115">Créez un assemblage fort avec une interface publique contenant des informations de type qui peuvent être intégrées.</span><span class="sxs-lookup"><span data-stu-id="c5570-115">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="c5570-116">Créez un assemblage de temps d’exécution fort qui implémente l’interface publique.</span><span class="sxs-lookup"><span data-stu-id="c5570-116">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="c5570-117">Créer un programme client qui incorpore les informations de type de l’interface publique et crée une instance de la classe à partir de l’assembly runtime.</span><span class="sxs-lookup"><span data-stu-id="c5570-117">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="c5570-118">Modifier et régénérer l’assembly runtime.</span><span class="sxs-lookup"><span data-stu-id="c5570-118">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="c5570-119">Exécutez le programme client pour s’en rendre compte qu’il utilise la nouvelle version de l’assemblage en temps d’exécution sans avoir à être recompilé.</span><span class="sxs-lookup"><span data-stu-id="c5570-119">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="c5570-120">Conditions et limitations</span><span class="sxs-lookup"><span data-stu-id="c5570-120">Conditions and limitations</span></span>

<span data-ttu-id="c5570-121">Vous pouvez intégrer des informations de type à partir d’un assemblage dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="c5570-121">You can embed type information from an assembly under the following conditions:</span></span>

- <span data-ttu-id="c5570-122">L’assembly expose au moins une interface publique.</span><span class="sxs-lookup"><span data-stu-id="c5570-122">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="c5570-123">Les interfaces intégrées sont `ComImport` annotées avec des attributs et `Guid` des attributs avec des GUID uniques.</span><span class="sxs-lookup"><span data-stu-id="c5570-123">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="c5570-124">L’assembly est annoté avec l’attribut `ImportedFromTypeLib` ou l’attribut `PrimaryInteropAssembly` et un attribut `Guid` au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c5570-124">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="c5570-125">Les modèles de projet Visual C et Visual `Guid` Basic comprennent un attribut de niveau d’assemblage par défaut.</span><span class="sxs-lookup"><span data-stu-id="c5570-125">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="c5570-126">Étant donné que la fonction principale de l’intégration de type est de prendre en charge les assemblages interop COM, les limitations suivantes s’appliquent lorsque vous intégrez des informations de type dans une solution entièrement gérée :</span><span class="sxs-lookup"><span data-stu-id="c5570-126">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="c5570-127">Seuls les attributs spécifiques à COM interop sont intégrés.</span><span class="sxs-lookup"><span data-stu-id="c5570-127">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="c5570-128">D’autres attributs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="c5570-128">Other attributes are ignored.</span></span>
- <span data-ttu-id="c5570-129">Si un type utilise des paramètres génériques et que le type de paramètre générique est un type intégré, ce type ne peut pas être utilisé à travers une limite d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="c5570-129">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="c5570-130">Parmi les exemples de franchissement d’une limite d’assemblage, mentionnons l’appel d’une méthode d’un autre assemblage ou la suppression d’un type d’un type défini dans un autre assemblage.</span><span class="sxs-lookup"><span data-stu-id="c5570-130">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="c5570-131">Les constantes ne sont pas incorporées.</span><span class="sxs-lookup"><span data-stu-id="c5570-131">Constants are not embedded.</span></span>
- <span data-ttu-id="c5570-132">La classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ne prend pas en charge un type incorporé comme clé.</span><span class="sxs-lookup"><span data-stu-id="c5570-132">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="c5570-133">Vous pouvez implémenter votre propre type de dictionnaire pour prendre en charge un type incorporé comme clé.</span><span class="sxs-lookup"><span data-stu-id="c5570-133">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="c5570-134">Créer une interface</span><span class="sxs-lookup"><span data-stu-id="c5570-134">Create an interface</span></span>

<span data-ttu-id="c5570-135">La première étape consiste à créer le type d’assemblage d’interface d’équivalence.</span><span class="sxs-lookup"><span data-stu-id="c5570-135">The first step is to create the type equivalence interface assembly.</span></span>

1. <span data-ttu-id="c5570-136">Dans Visual Studio, sélectionnez **File** > **New** > **Project**.</span><span class="sxs-lookup"><span data-stu-id="c5570-136">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="c5570-137">Dans la boîte de dialogue **Créer un nouveau projet,** *type bibliothèque de classe* dans la boîte de recherche **de modèles.**</span><span class="sxs-lookup"><span data-stu-id="c5570-137">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="c5570-138">Sélectionnez le modèle de bibliothèque de classe de base visuelle **(.NET Framework)** de la liste, puis sélectionnez **Next**.</span><span class="sxs-lookup"><span data-stu-id="c5570-138">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="c5570-139">Dans la configuration de votre nouvelle boîte de dialogue **de projet,** sous **le nom de projet**, *tapez TypeEquivalenceInterface*, puis sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="c5570-139">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="c5570-140">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="c5570-140">The new project is created.</span></span>

1. <span data-ttu-id="c5570-141">Dans **Solution Explorer**, cliquez à droite sur le fichier *Class1.cs* ou *Class1.vb,* **sélectionnez Rename**, et renommez le fichier de *classe1* à *ISampleInterface*.</span><span class="sxs-lookup"><span data-stu-id="c5570-141">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="c5570-142">Répondre **Oui** à l’invite de également `ISampleInterface`renommer la classe à .</span><span class="sxs-lookup"><span data-stu-id="c5570-142">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="c5570-143">Cette classe représente l’interface publique de la classe.</span><span class="sxs-lookup"><span data-stu-id="c5570-143">This class represents the public interface for the class.</span></span>

1. <span data-ttu-id="c5570-144">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceInterface,** puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c5570-144">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span>

1. <span data-ttu-id="c5570-145">Sélectionnez **Construire** sur la vitre gauche de l’écran **Propriétés,** et définissez le **chemin de sortie** à un emplacement sur votre ordinateur, tels que *C: 'TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="c5570-145">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="c5570-146">Vous utilisez le même emplacement tout au long de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="c5570-146">You use the same location throughout this walkthrough.</span></span>

1. <span data-ttu-id="c5570-147">Sélectionnez **Signature** sur la vitre gauche de l’écran **Propriétés,** puis sélectionnez le Signe de la case à cocher **d’assemblage.**</span><span class="sxs-lookup"><span data-stu-id="c5570-147">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="c5570-148">Dans le dropdown pour **Choisissez un fichier clé de nom fort**, sélectionnez **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="c5570-148">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="c5570-149">Dans le **dialogue Create Strong Name Key,** sous le nom de fichier **Key**, type *key.snk*.</span><span class="sxs-lookup"><span data-stu-id="c5570-149">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="c5570-150">Déséllectez le **Fichier Protégez mon fichier clé avec une** case à cocher par mot de passe, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5570-150">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="c5570-151">Ouvrez le fichier de classe *ISampleInterface* dans l’éditeur de `ISampleInterface` code, et remplacez son contenu par le code suivant pour créer l’interface :</span><span class="sxs-lookup"><span data-stu-id="c5570-151">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>

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

1. <span data-ttu-id="c5570-152">Sur le menu **Tools,** sélectionnez **Create Guid**, et dans la boîte de dialogue **Create GUID,** sélectionnez **Format d’enregistrement**.</span><span class="sxs-lookup"><span data-stu-id="c5570-152">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="c5570-153">Sélectionnez **La copie,** puis sélectionnez **Exit**.</span><span class="sxs-lookup"><span data-stu-id="c5570-153">Select **Copy**, and then select **Exit**.</span></span>

1. <span data-ttu-id="c5570-154">Dans `Guid` l’attribut de votre code, remplacez l’échantillon GUID par le GUID que vous avez copié, et retirez les accolades **(**.</span><span class="sxs-lookup"><span data-stu-id="c5570-154">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>

1. <span data-ttu-id="c5570-155">Dans **Solution Explorer**, étendre le dossier **Propriétés** et sélectionnez le fichier *AssemblyInfo.cs* ou *AssemblyInfo.vb.*</span><span class="sxs-lookup"><span data-stu-id="c5570-155">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="c5570-156">Dans l’éditeur de code, ajoutez l’attribut suivant au fichier :</span><span class="sxs-lookup"><span data-stu-id="c5570-156">In the code editor, add the following attribute to the file:</span></span>

   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```

   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```

1. <span data-ttu-id="c5570-157">Sélectionnez **Fichier** > **Enregistrer tous** ou appuyez sur **Ctrl**+**Shift**+**S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="c5570-157">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="c5570-158">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceInterface** et sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="c5570-158">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="c5570-159">Le fichier DLL de bibliothèque de classe est compilé et enregistré sur le chemin de sortie de construction spécifié, par exemple *C : 'TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="c5570-159">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="c5570-160">Créer une classe de temps d’exécution</span><span class="sxs-lookup"><span data-stu-id="c5570-160">Create a runtime class</span></span>

<span data-ttu-id="c5570-161">Ensuite, créez la classe de runtime d’équivalence type.</span><span class="sxs-lookup"><span data-stu-id="c5570-161">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="c5570-162">Dans Visual Studio, sélectionnez **File** > **New** > **Project**.</span><span class="sxs-lookup"><span data-stu-id="c5570-162">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="c5570-163">Dans la boîte de dialogue **Créer un nouveau projet,** *type bibliothèque de classe* dans la boîte de recherche **de modèles.**</span><span class="sxs-lookup"><span data-stu-id="c5570-163">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="c5570-164">Sélectionnez le modèle de bibliothèque de classe de base visuelle **(.NET Framework)** de la liste, puis sélectionnez **Next**.</span><span class="sxs-lookup"><span data-stu-id="c5570-164">Select either the C# or Visual Basic **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="c5570-165">Dans la configuration de votre nouvelle boîte de dialogue **de projet,** sous **le nom de projet**, type *TypeEquivalenceRuntime*, puis sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="c5570-165">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="c5570-166">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="c5570-166">The new project is created.</span></span>

1. <span data-ttu-id="c5570-167">Dans **Solution Explorer**, cliquez à droite sur le fichier *Class1.cs* ou *Class1.vb,* **sélectionnez Rename**, et renommez le fichier de *Class1* à *SampleClass*.</span><span class="sxs-lookup"><span data-stu-id="c5570-167">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="c5570-168">Répondre **Oui** à l’invite de également `SampleClass`renommer la classe à .</span><span class="sxs-lookup"><span data-stu-id="c5570-168">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="c5570-169">Cette classe implémente l’interface `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="c5570-169">This class implements the `ISampleInterface` interface.</span></span>

1. <span data-ttu-id="c5570-170">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceInterface** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c5570-170">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="c5570-171">Sélectionnez **Construire** sur le volet gauche de l’écran **Propriétés,** puis définir le **chemin de sortie** au même endroit que vous avez utilisé pour le projet TypeEquivalenceInterface, par exemple, *C: 'TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="c5570-171">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="c5570-172">Sélectionnez **Signature** sur la vitre gauche de l’écran **Propriétés,** puis sélectionnez le Signe de la case à cocher **d’assemblage.**</span><span class="sxs-lookup"><span data-stu-id="c5570-172">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="c5570-173">Dans le dropdown pour **Choisissez un fichier clé de nom fort**, sélectionnez **Nouveau**.</span><span class="sxs-lookup"><span data-stu-id="c5570-173">In the dropdown for **Choose a strong name key file**, select **New**.</span></span>

1. <span data-ttu-id="c5570-174">Dans le **dialogue Create Strong Name Key,** sous le nom de fichier **Key**, type *key.snk*.</span><span class="sxs-lookup"><span data-stu-id="c5570-174">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="c5570-175">Déséllectez le **Fichier Protégez mon fichier clé avec une** case à cocher par mot de passe, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5570-175">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>

1. <span data-ttu-id="c5570-176">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceRuntime** et **sélectionnez Ajouter** > **référence**.</span><span class="sxs-lookup"><span data-stu-id="c5570-176">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="c5570-177">Dans le dialogue **de Reference Manager,** **sélectionnez Parcourir** et naviguez vers le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="c5570-177">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="c5570-178">Sélectionnez le fichier *TypeEquivalenceInterface.dll,* sélectionnez **Ajouter,** puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5570-178">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>

1. <span data-ttu-id="c5570-179">Dans **Solution Explorer**, élargissez le dossier **Références** et sélectionnez la référence **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="c5570-179">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="c5570-180">Dans le volet **Propriétés,** définissez **la version spécifique** à **False** si ce n’est pas déjà le cas.</span><span class="sxs-lookup"><span data-stu-id="c5570-180">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>

1. <span data-ttu-id="c5570-181">Ouvrez le fichier de classe *SampleClass* dans l’éditeur de `SampleClass` code et remplacez son contenu par le code suivant pour créer la classe :</span><span class="sxs-lookup"><span data-stu-id="c5570-181">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="c5570-182">Sélectionnez **Fichier** > **Enregistrer tous** ou appuyez sur **Ctrl**+**Shift**+**S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="c5570-182">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="c5570-183">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceRuntime** et sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="c5570-183">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="c5570-184">Le fichier DLL de bibliothèque de classe est compilé et enregistré sur le chemin de sortie de construction spécifié.</span><span class="sxs-lookup"><span data-stu-id="c5570-184">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="c5570-185">Créer un projet client</span><span class="sxs-lookup"><span data-stu-id="c5570-185">Create a client project</span></span>

<span data-ttu-id="c5570-186">Enfin, créez un programme client d’équivalence type qui fait référence à l’assemblage de l’interface.</span><span class="sxs-lookup"><span data-stu-id="c5570-186">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="c5570-187">Dans Visual Studio, sélectionnez **File** > **New** > **Project**.</span><span class="sxs-lookup"><span data-stu-id="c5570-187">In Visual Studio, select **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="c5570-188">Dans la boîte de dialogue **Créer un nouveau projet,** *typez la console* dans la boîte de recherche de **modèles.**</span><span class="sxs-lookup"><span data-stu-id="c5570-188">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="c5570-189">Sélectionnez le modèle C ou Visual Basic **Console App (.NET Framework)** de la liste, puis sélectionnez **Next**.</span><span class="sxs-lookup"><span data-stu-id="c5570-189">Select either the C# or Visual Basic **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span>

1. <span data-ttu-id="c5570-190">Dans la configuration de votre nouvelle boîte de dialogue **de projet,** sous **le nom de projet**, type *TypeEquivalenceClient*, puis sélectionnez **Créer**.</span><span class="sxs-lookup"><span data-stu-id="c5570-190">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="c5570-191">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="c5570-191">The new project is created.</span></span>

1. <span data-ttu-id="c5570-192">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceClient** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c5570-192">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span>

1. <span data-ttu-id="c5570-193">Sélectionnez **Construire** sur le volet gauche de l’écran **Propriétés,** puis définir le **chemin de sortie** au même endroit que vous avez utilisé pour le projet TypeEquivalenceInterface, par exemple, *C: 'TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="c5570-193">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>

1. <span data-ttu-id="c5570-194">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceClient** et **sélectionnez Ajouter** > **référence**.</span><span class="sxs-lookup"><span data-stu-id="c5570-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span>

1. <span data-ttu-id="c5570-195">Dans le dialogue **du gestionnaire de référence,** si le fichier **TypeEquivalenceInterface.dll** est déjà répertorié, sélectionnez-le.</span><span class="sxs-lookup"><span data-stu-id="c5570-195">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="c5570-196">Si ce n’est pas le cas, **sélectionnez Parcourir,** naviguez vers le dossier de sortie, sélectionnez le fichier *TypeEquivalenceInterface.dll* (pas le *TypeEquivalenceRuntime.dll*), et sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="c5570-196">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="c5570-197">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5570-197">Select **OK**.</span></span>

1. <span data-ttu-id="c5570-198">Dans **Solution Explorer**, élargissez le dossier **Références** et sélectionnez la référence **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="c5570-198">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="c5570-199">Dans le volet **Propriétés,** mettre **Embed Interop Types** à **True**.</span><span class="sxs-lookup"><span data-stu-id="c5570-199">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>

1. <span data-ttu-id="c5570-200">Ouvrez le *fichier Program.cs* ou *Module1.vb* dans l’éditeur de code, et remplacez son contenu par le code suivant pour créer le programme client :</span><span class="sxs-lookup"><span data-stu-id="c5570-200">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>

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

1. <span data-ttu-id="c5570-201">Sélectionnez **Fichier** > **Enregistrer tous** ou appuyez sur **Ctrl**+**Shift**+**S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="c5570-201">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="c5570-202">Appuyez sur **Ctrl**+**F5** pour construire et exécuter le programme.</span><span class="sxs-lookup"><span data-stu-id="c5570-202">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="c5570-203">Notez que la sortie de la console renvoie la version d’assemblage **1.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="c5570-203">Note that the console output returns the assembly version **1.0.0.0**.</span></span>

## <a name="modify-the-interface"></a><span data-ttu-id="c5570-204">Modifier l’interface</span><span class="sxs-lookup"><span data-stu-id="c5570-204">Modify the interface</span></span>

<span data-ttu-id="c5570-205">Maintenant, modifiez l’assemblage de l’interface et modifiez sa version.</span><span class="sxs-lookup"><span data-stu-id="c5570-205">Now, modify the interface assembly, and change its version.</span></span>

1. <span data-ttu-id="c5570-206">Dans Visual Studio, sélectionnez **File** > **Open** > **Project/Solution**et ouvrez le projet **TypeEquivalenceInterface.**</span><span class="sxs-lookup"><span data-stu-id="c5570-206">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>

1. <span data-ttu-id="c5570-207">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceInterface** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c5570-207">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span>

1. <span data-ttu-id="c5570-208">Sélectionnez **l’application** sur le volet gauche de l’écran **propriétés,** puis sélectionnez **l’information d’assemblage**.</span><span class="sxs-lookup"><span data-stu-id="c5570-208">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="c5570-209">Dans la boîte de dialogue **d’information de l’Assemblée,** modifiez les valeurs de la **version de l’Assemblée** et **de la version Fichier** à *2.0.0.0*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5570-209">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="c5570-210">Ouvrez le *fichier SampleInterface.cs* ou *SampleInterface.vb,* et ajoutez la `ISampleInterface` ligne de code suivante à l’interface :</span><span class="sxs-lookup"><span data-stu-id="c5570-210">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>

   ```csharp
   DateTime GetDate();
   ```

   ```vb
   Function GetDate() As Date
   ```

1. <span data-ttu-id="c5570-211">Sélectionnez **Fichier** > **Enregistrer tous** ou appuyez sur **Ctrl**+**Shift**+**S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="c5570-211">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="c5570-212">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceInterface** et sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="c5570-212">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="c5570-213">Une nouvelle version du fichier DLL de bibliothèque de classe est compilée et enregistrée sur le chemin de sortie de construction.</span><span class="sxs-lookup"><span data-stu-id="c5570-213">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="c5570-214">Modifier la classe de temps d’exécution</span><span class="sxs-lookup"><span data-stu-id="c5570-214">Modify the runtime class</span></span>

<span data-ttu-id="c5570-215">Modifiez également la classe de temps d’exécution et mettez à jour sa version.</span><span class="sxs-lookup"><span data-stu-id="c5570-215">Also modify the runtime class and update its version.</span></span>

1. <span data-ttu-id="c5570-216">Dans Visual Studio, sélectionnez **File** > **Open** > **Project/Solution**et ouvrez le projet **TypeEquivalenceRuntime.**</span><span class="sxs-lookup"><span data-stu-id="c5570-216">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>

1. <span data-ttu-id="c5570-217">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceRuntime** et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c5570-217">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span>

1. <span data-ttu-id="c5570-218">Sélectionnez **l’application** sur le volet gauche de l’écran **propriétés,** puis sélectionnez **l’information d’assemblage**.</span><span class="sxs-lookup"><span data-stu-id="c5570-218">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span>

1. <span data-ttu-id="c5570-219">Dans la boîte de dialogue **d’information de l’Assemblée,** modifiez les valeurs de la **version de l’Assemblée** et **de la version Fichier** à *2.0.0.0*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="c5570-219">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>

1. <span data-ttu-id="c5570-220">Ouvrez le fichier *SampleClass.cs* ou *SampleClass.vb,* et ajoutez `SampleClass` le code suivant à la classe :</span><span class="sxs-lookup"><span data-stu-id="c5570-220">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>

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

1. <span data-ttu-id="c5570-221">Sélectionnez **Fichier** > **Enregistrer tous** ou appuyez sur **Ctrl**+**Shift**+**S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="c5570-221">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>

1. <span data-ttu-id="c5570-222">Dans **Solution Explorer**, cliquez à droite sur le projet **TypeEquivalenceRuntime** et sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="c5570-222">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="c5570-223">Une nouvelle version du fichier DLL de bibliothèque de classe est compilée et enregistrée sur le chemin de sortie de construction.</span><span class="sxs-lookup"><span data-stu-id="c5570-223">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="c5570-224">Exécuter le programme client mis à jour</span><span class="sxs-lookup"><span data-stu-id="c5570-224">Run the updated client program</span></span>

<span data-ttu-id="c5570-225">Aller à l’emplacement du dossier de sortie de construction et exécuter *TypeEquivalenceClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="c5570-225">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="c5570-226">Notez que la sortie de la `TypeEquivalenceRuntime` console reflète désormais la nouvelle version de l’assemblage, *2.0.0.0*, sans que le programme soit recompilé.</span><span class="sxs-lookup"><span data-stu-id="c5570-226">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="c5570-227">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5570-227">See also</span></span>

- [<span data-ttu-id="c5570-228">-link (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="c5570-228">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="c5570-229">-lien (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5570-229">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="c5570-230">Guide de programmation CMD</span><span class="sxs-lookup"><span data-stu-id="c5570-230">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c5570-231">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c5570-231">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="c5570-232">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="c5570-232">Assemblies in .NET</span></span>](index.md)
