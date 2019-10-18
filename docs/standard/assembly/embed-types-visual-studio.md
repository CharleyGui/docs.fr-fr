---
title: 'Procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio'
ms.date: 08/19/2019
ms.assetid: 55ed13c9-c5bb-4bc2-bcd8-0587eb568864
dev_langs:
- csharp
- vb
ms.openlocfilehash: 1a37a3bcc3b1bc352d6a2f59691819e0b2403d3d
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523897"
---
# <a name="walkthrough-embed-types-from-managed-assemblies-in-visual-studio"></a><span data-ttu-id="58d7c-102">Procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="58d7c-102">Walkthrough: Embed types from managed assemblies in Visual Studio</span></span>

<span data-ttu-id="58d7c-103">Si vous incorporez des informations de type d’un assembly managé avec nom fort, vous pouvez coupler faiblement des types dans une application pour obtenir une indépendance de version.</span><span class="sxs-lookup"><span data-stu-id="58d7c-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="58d7c-104">Autrement dit, votre programme peut être écrit pour utiliser des types à partir de n’importe quelle version d’une bibliothèque managée sans devoir être recompilé pour chaque nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="58d7c-104">That is, your program can be written to use types from any version of a managed library without having to be recompiled for each new version.</span></span>

<span data-ttu-id="58d7c-105">L’incorporation de type est fréquemment utilisée avec COM Interop, par exemple pour une application qui utilise des objets Automation de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="58d7c-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="58d7c-106">L’incorporation des informations de type permet à la même build d’un programme de fonctionner avec différentes versions de Microsoft Office sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="58d7c-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="58d7c-107">Toutefois, vous pouvez également utiliser l’incorporation de type avec des solutions entièrement managées.</span><span class="sxs-lookup"><span data-stu-id="58d7c-107">However, you can also use type embedding with fully managed solutions.</span></span>

<span data-ttu-id="58d7c-108">Une fois que vous avez spécifié les interfaces publiques qui peuvent être incorporées, vous créez des classes d’exécution qui implémentent ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="58d7c-108">After you specify the public interfaces that can be embedded, you create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="58d7c-109">Un programme client peut incorporer les informations de type pour les interfaces au moment du design en référençant l’assembly qui contient les interfaces publiques et en affectant à la propriété `Embed Interop Types` de la référence la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="58d7c-109">A client program can embed the type information for the interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="58d7c-110">Le programme client peut ensuite charger les instances des objets de Runtime tapés comme ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="58d7c-110">The client program can then load instances of the runtime objects typed as those interfaces.</span></span> <span data-ttu-id="58d7c-111">Cela revient à utiliser le compilateur de ligne de commande et à référencer l’assembly à l’aide de l’option de compilateur `/link`.</span><span class="sxs-lookup"><span data-stu-id="58d7c-111">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> 

<span data-ttu-id="58d7c-112">Si vous créez une nouvelle version de votre assembly de Runtime avec nom fort, le programme client n’a pas besoin d’être recompilé.</span><span class="sxs-lookup"><span data-stu-id="58d7c-112">If you create a new version of your strong-named runtime assembly, the client program doesn't have to be recompiled.</span></span> <span data-ttu-id="58d7c-113">Le programme client continue à utiliser la version de l’assembly de Runtime qui lui est accessible, à l’aide des informations de type incorporées pour les interfaces publiques.</span><span class="sxs-lookup"><span data-stu-id="58d7c-113">The client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="58d7c-114">Dans cette procédure pas à pas, vous allez :</span><span class="sxs-lookup"><span data-stu-id="58d7c-114">In this walkthrough, you:</span></span>

1. <span data-ttu-id="58d7c-115">Créez un assembly avec nom fort avec une interface publique contenant les informations de type qui peuvent être incorporées.</span><span class="sxs-lookup"><span data-stu-id="58d7c-115">Create a strong-named assembly with a public interface containing type information that can be embedded.</span></span>
1. <span data-ttu-id="58d7c-116">Créez un assembly de Runtime avec nom fort qui implémente l’interface publique.</span><span class="sxs-lookup"><span data-stu-id="58d7c-116">Create a strong-named runtime assembly that implements the public interface.</span></span>
1. <span data-ttu-id="58d7c-117">Créer un programme client qui incorpore les informations de type de l’interface publique et crée une instance de la classe à partir de l’assembly runtime.</span><span class="sxs-lookup"><span data-stu-id="58d7c-117">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>
1. <span data-ttu-id="58d7c-118">Modifier et régénérer l’assembly runtime.</span><span class="sxs-lookup"><span data-stu-id="58d7c-118">Modify and rebuild the runtime assembly.</span></span>
1. <span data-ttu-id="58d7c-119">Exécutez le programme client pour voir qu’il utilise la nouvelle version de l’assembly du runtime sans devoir être recompilé.</span><span class="sxs-lookup"><span data-stu-id="58d7c-119">Run the client program to see that it uses the new version of the runtime assembly without having to be recompiled.</span></span>

[!INCLUDE[note_settings_general](../../../includes/note-settings-general-md.md)]

## <a name="conditions-and-limitations"></a><span data-ttu-id="58d7c-120">Conditions et limitations</span><span class="sxs-lookup"><span data-stu-id="58d7c-120">Conditions and limitations</span></span>

<span data-ttu-id="58d7c-121">Vous pouvez incorporer des informations de type à partir d’un assembly dans les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="58d7c-121">You can embed type information from an assembly under the following conditions:</span></span> 

- <span data-ttu-id="58d7c-122">L’assembly expose au moins une interface publique.</span><span class="sxs-lookup"><span data-stu-id="58d7c-122">The assembly exposes at least one public interface.</span></span>
- <span data-ttu-id="58d7c-123">Les interfaces incorporées sont annotées avec des attributs `ComImport` et des attributs `Guid` avec des GUID uniques.</span><span class="sxs-lookup"><span data-stu-id="58d7c-123">The embedded interfaces are annotated with `ComImport` attributes and `Guid` attributes with unique GUIDs.</span></span>
- <span data-ttu-id="58d7c-124">L’assembly est annoté avec l’attribut `ImportedFromTypeLib` ou l’attribut `PrimaryInteropAssembly` et un attribut `Guid` au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="58d7c-124">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="58d7c-125">Les modèles C# de projet Visual et Visual Basic incluent par défaut un attribut `Guid` au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="58d7c-125">The Visual C# and Visual Basic project templates include an assembly-level `Guid` attribute by default.</span></span>

<span data-ttu-id="58d7c-126">Étant donné que la fonction principale de l’incorporation de type consiste à prendre en charge les assemblys COM Interop, les limitations suivantes s’appliquent quand vous incorporez des informations de type dans une solution entièrement managée :</span><span class="sxs-lookup"><span data-stu-id="58d7c-126">Because the primary function of type embedding is to support COM interop assemblies, the following limitations apply when you embed type information in a fully-managed solution:</span></span>

- <span data-ttu-id="58d7c-127">Seuls les attributs spécifiques aux COM Interop sont incorporés.</span><span class="sxs-lookup"><span data-stu-id="58d7c-127">Only attributes specific to COM interop are embedded.</span></span> <span data-ttu-id="58d7c-128">Les autres attributs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="58d7c-128">Other attributes are ignored.</span></span>
- <span data-ttu-id="58d7c-129">Si un type utilise des paramètres génériques et que le type du paramètre générique est un type incorporé, ce type ne peut pas être utilisé dans les limites d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="58d7c-129">If a type uses generic parameters, and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="58d7c-130">Les exemples de franchissement d’une limite d’assembly incluent l’appel d’une méthode à partir d’un autre assembly ou la dérivation d’un type d’un type défini dans un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="58d7c-130">Examples of crossing an assembly boundary include calling a method from another assembly or deriving a type from a type defined in another assembly.</span></span>
- <span data-ttu-id="58d7c-131">Les constantes ne sont pas incorporées.</span><span class="sxs-lookup"><span data-stu-id="58d7c-131">Constants are not embedded.</span></span>
- <span data-ttu-id="58d7c-132">La classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ne prend pas en charge un type incorporé comme clé.</span><span class="sxs-lookup"><span data-stu-id="58d7c-132">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="58d7c-133">Vous pouvez implémenter votre propre type de dictionnaire pour prendre en charge un type incorporé comme clé.</span><span class="sxs-lookup"><span data-stu-id="58d7c-133">You can implement your own dictionary type to support an embedded type as a key.</span></span>

## <a name="create-an-interface"></a><span data-ttu-id="58d7c-134">Créer une interface</span><span class="sxs-lookup"><span data-stu-id="58d7c-134">Create an interface</span></span>

<span data-ttu-id="58d7c-135">La première étape consiste à créer l’assembly de l’interface d’équivalence de type.</span><span class="sxs-lookup"><span data-stu-id="58d7c-135">The first step is to create the type equivalence interface assembly.</span></span> 

1. <span data-ttu-id="58d7c-136">Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-136">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="58d7c-137">Dans la boîte de dialogue **créer un nouveau projet** , tapez *bibliothèque de classes* dans la zone **Rechercher des modèles** .</span><span class="sxs-lookup"><span data-stu-id="58d7c-137">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="58d7c-138">Sélectionnez le C# modèle Bibliothèque de **classes VB ou (.NET Framework)** dans la liste, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-138">Select either the C# or VB **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="58d7c-139">Dans la boîte de dialogue **configurer votre nouveau projet** , sous **nom du projet**, tapez *TypeEquivalenceInterface*, puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-139">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceInterface*, and then select **Create**.</span></span> <span data-ttu-id="58d7c-140">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="58d7c-140">The new project is created.</span></span>
   
1. <span data-ttu-id="58d7c-141">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Class1.cs* ou *Class1. vb* , sélectionnez **Renommer**, puis renommez le fichier de *Class1* en *ISampleInterface*.</span><span class="sxs-lookup"><span data-stu-id="58d7c-141">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *ISampleInterface*.</span></span> <span data-ttu-id="58d7c-142">Répondez **Oui** à l’invite pour renommer la classe en `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="58d7c-142">Respond **Yes** to the prompt to also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="58d7c-143">Cette classe représente l’interface publique de la classe.</span><span class="sxs-lookup"><span data-stu-id="58d7c-143">This class represents the public interface for the class.</span></span>
   
1. <span data-ttu-id="58d7c-144">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** , puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-144">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project, and then select **Properties**.</span></span> 
   
1. <span data-ttu-id="58d7c-145">Sélectionnez **Build** dans le volet gauche de l’écran **Propriétés** , puis définissez le **chemin de sortie** sur un emplacement sur votre ordinateur, par exemple *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="58d7c-145">Select **Build** on the left pane of the **Properties** screen, and set the **Output path** to a location on your computer, such as *C:\TypeEquivalenceSample*.</span></span> <span data-ttu-id="58d7c-146">Vous utilisez le même emplacement dans cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="58d7c-146">You use the same location throughout this walkthrough.</span></span> 
   
1. <span data-ttu-id="58d7c-147">Sélectionnez **signature** dans le volet gauche de l’écran **Propriétés** , puis activez la case à cocher **signer l’assembly** .</span><span class="sxs-lookup"><span data-stu-id="58d7c-147">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="58d7c-148">Dans la liste déroulante **choisir un fichier de clé de nom fort**, sélectionnez **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-148">In the dropdown for **Choose a strong name key file**, select **New**.</span></span> 
   
1. <span data-ttu-id="58d7c-149">Dans la boîte de dialogue **créer une clé de nom fort** , sous **nom du fichier de clé**, tapez *Key. snk*.</span><span class="sxs-lookup"><span data-stu-id="58d7c-149">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="58d7c-150">Désactivez la case à cocher **protéger le fichier de clé avec un mot de passe** , puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-150">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58d7c-151">Ouvrez le fichier de la classe *ISampleInterface* dans l’éditeur de code, puis remplacez son contenu par le code suivant pour créer l’interface `ISampleInterface` :</span><span class="sxs-lookup"><span data-stu-id="58d7c-151">Open the *ISampleInterface* class file in the code editor, and replace its contents with the following code to create the `ISampleInterface` interface:</span></span>
   
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
   
1. <span data-ttu-id="58d7c-152">Dans le menu **Outils** , sélectionnez **créer un GUID**, puis dans la boîte de dialogue créer un **GUID** , sélectionnez **format du Registre**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-152">On the **Tools** menu, select **Create Guid**, and in the **Create GUID** dialog box, select **Registry Format**.</span></span> <span data-ttu-id="58d7c-153">Sélectionnez **copier**, puis **quitter**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-153">Select **Copy**, and then select **Exit**.</span></span>
   
1. <span data-ttu-id="58d7c-154">Dans l’attribut `Guid` de votre code, remplacez l’exemple de GUID par le GUID que vous avez copié, et supprimez les accolades ( **{}** ).</span><span class="sxs-lookup"><span data-stu-id="58d7c-154">In the `Guid` attribute of your code, replace the sample GUID with the GUID you copied, and remove the braces (**{ }**).</span></span>
   
1. <span data-ttu-id="58d7c-155">Dans **Explorateur de solutions**, développez le dossier **Propriétés** et sélectionnez le fichier *AssemblyInfo.cs* ou *AssemblyInfo. vb* .</span><span class="sxs-lookup"><span data-stu-id="58d7c-155">In **Solution Explorer**, expand the **Properties** folder and select the *AssemblyInfo.cs* or *AssemblyInfo.vb* file.</span></span> <span data-ttu-id="58d7c-156">Dans l’éditeur de code, ajoutez l’attribut suivant au fichier :</span><span class="sxs-lookup"><span data-stu-id="58d7c-156">In the code editor, add the following attribute to the file:</span></span>
   
   ```csharp
   [assembly: ImportedFromTypeLib("")]
   ```
   
   ```vb
   <Assembly: ImportedFromTypeLib("")>
   ```
   
1. <span data-ttu-id="58d7c-157">Sélectionnez **fichier**  > **enregistrer tout** ou appuyez sur **CTRL** +**MAJ** +**S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="58d7c-157">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58d7c-158">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** , puis sélectionnez **générer**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-158">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="58d7c-159">Le fichier DLL de la bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié, par exemple *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="58d7c-159">The class library DLL file is compiled and saved to the specified build output path, for example *C:\TypeEquivalenceSample*.</span></span>

## <a name="create-a-runtime-class"></a><span data-ttu-id="58d7c-160">Créer une classe d’exécution</span><span class="sxs-lookup"><span data-stu-id="58d7c-160">Create a runtime class</span></span>

<span data-ttu-id="58d7c-161">Ensuite, créez la classe d’exécution d’équivalence de type.</span><span class="sxs-lookup"><span data-stu-id="58d7c-161">Next, create the type equivalence runtime class.</span></span>

1. <span data-ttu-id="58d7c-162">Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-162">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="58d7c-163">Dans la boîte de dialogue **créer un nouveau projet** , tapez *bibliothèque de classes* dans la zone **Rechercher des modèles** .</span><span class="sxs-lookup"><span data-stu-id="58d7c-163">In the **Create a new project** dialog box, type *class library* in the **Search for templates** box.</span></span> <span data-ttu-id="58d7c-164">Sélectionnez le C# modèle Bibliothèque de **classes VB ou (.NET Framework)** dans la liste, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-164">Select either the C# or VB **Class Library (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="58d7c-165">Dans la boîte de dialogue **configurer votre nouveau projet** , sous **nom du projet**, tapez *TypeEquivalenceRuntime*, puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-165">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceRuntime*, and then select **Create**.</span></span> <span data-ttu-id="58d7c-166">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="58d7c-166">The new project is created.</span></span>
   
1. <span data-ttu-id="58d7c-167">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *Class1.cs* ou *Class1. vb* , sélectionnez **Renommer**, puis renommez le fichier de *Class1* en *SampleClass*.</span><span class="sxs-lookup"><span data-stu-id="58d7c-167">In **Solution Explorer**, right-click the *Class1.cs* or *Class1.vb* file, select **Rename**, and rename the file from *Class1* to *SampleClass*.</span></span> <span data-ttu-id="58d7c-168">Répondez **Oui** à l’invite pour renommer la classe en `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="58d7c-168">Respond **Yes** to the prompt to also rename the class to `SampleClass`.</span></span> <span data-ttu-id="58d7c-169">Cette classe implémente l'interface `ISampleInterface` .</span><span class="sxs-lookup"><span data-stu-id="58d7c-169">This class implements the `ISampleInterface` interface.</span></span>
   
1. <span data-ttu-id="58d7c-170">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-170">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58d7c-171">Sélectionnez **Build** dans le volet gauche de l’écran **Propriétés** , puis définissez le **chemin de sortie** sur le même emplacement que celui que vous avez utilisé pour le projet TypeEquivalenceInterface, par exemple *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="58d7c-171">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>
   
1. <span data-ttu-id="58d7c-172">Sélectionnez **signature** dans le volet gauche de l’écran **Propriétés** , puis activez la case à cocher **signer l’assembly** .</span><span class="sxs-lookup"><span data-stu-id="58d7c-172">Select **Signing** on the left pane of the **Properties** screen, and then select the **Sign the assembly** check box.</span></span> <span data-ttu-id="58d7c-173">Dans la liste déroulante **choisir un fichier de clé de nom fort**, sélectionnez **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-173">In the dropdown for **Choose a strong name key file**, select **New**.</span></span> 
   
1. <span data-ttu-id="58d7c-174">Dans la boîte de dialogue **créer une clé de nom fort** , sous **nom du fichier de clé**, tapez *Key. snk*.</span><span class="sxs-lookup"><span data-stu-id="58d7c-174">In the **Create Strong Name Key** dialog, under **Key file name**, type *key.snk*.</span></span> <span data-ttu-id="58d7c-175">Désactivez la case à cocher **protéger le fichier de clé avec un mot de passe** , puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-175">Deselect the **Protect my key file with a password** check box, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58d7c-176">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** , puis sélectionnez **Ajouter** une**référence**de  > .</span><span class="sxs-lookup"><span data-stu-id="58d7c-176">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Add** > **Reference**.</span></span> 
   
1. <span data-ttu-id="58d7c-177">Dans la boîte de dialogue **Gestionnaire de références** , sélectionnez **Parcourir** et accédez au dossier du chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="58d7c-177">In the **Reference Manager** dialog, select **Browse** and browse to the output path folder.</span></span> <span data-ttu-id="58d7c-178">Sélectionnez le fichier *TypeEquivalenceInterface. dll* , sélectionnez **Ajouter**, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-178">Select the *TypeEquivalenceInterface.dll* file, select **Add**, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58d7c-179">Dans **Explorateur de solutions**, développez le dossier **références** et sélectionnez la référence **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="58d7c-179">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="58d7c-180">Dans le volet **Propriétés** , affectez à **version spécifique** la **valeur false** si ce n’est pas déjà fait.</span><span class="sxs-lookup"><span data-stu-id="58d7c-180">In the **Properties** pane, set **Specific Version** to **False** if it is not already.</span></span>
   
1. <span data-ttu-id="58d7c-181">Ouvrez le fichier de classe *SampleClass* dans l’éditeur de code, puis remplacez son contenu par le code suivant pour créer la classe `SampleClass` :</span><span class="sxs-lookup"><span data-stu-id="58d7c-181">Open the *SampleClass* class file in the code editor, and replace its contents with the following code to create the `SampleClass` class:</span></span>
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
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
   
1. <span data-ttu-id="58d7c-182">Sélectionnez **fichier**  > **enregistrer tout** ou appuyez sur **CTRL** +**MAJ** +**S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="58d7c-182">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58d7c-183">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** et sélectionnez **générer**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-183">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="58d7c-184">Le fichier DLL de la bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié.</span><span class="sxs-lookup"><span data-stu-id="58d7c-184">The class library DLL file is compiled and saved to the specified build output path.</span></span>

## <a name="create-a-client-project"></a><span data-ttu-id="58d7c-185">Créer un projet client</span><span class="sxs-lookup"><span data-stu-id="58d7c-185">Create a client project</span></span>

<span data-ttu-id="58d7c-186">Enfin, créez un programme client d’équivalence de type qui référence l’assembly d’interface.</span><span class="sxs-lookup"><span data-stu-id="58d7c-186">Finally, create a type equivalence client program that references the interface assembly.</span></span>

1. <span data-ttu-id="58d7c-187">Dans Visual Studio, sélectionnez **Fichier** > **Nouveau** > **Projet**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-187">In Visual Studio, select **File** > **New** > **Project**.</span></span>
   
1. <span data-ttu-id="58d7c-188">Dans la boîte de dialogue **créer un nouveau projet** , tapez *console* dans la zone **Rechercher des modèles** .</span><span class="sxs-lookup"><span data-stu-id="58d7c-188">In the **Create a new project** dialog box, type *console* in the **Search for templates** box.</span></span> <span data-ttu-id="58d7c-189">Sélectionnez le C# modèle application de **console ou vb (.NET Framework)** dans la liste, puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-189">Select either the C# or VB **Console App (.NET Framework)** template from the list, and then select **Next**.</span></span> 
   
1. <span data-ttu-id="58d7c-190">Dans la boîte de dialogue **configurer votre nouveau projet** , sous **nom du projet**, tapez *TypeEquivalenceClient,* , puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-190">In the **Configure your new project** dialog box, under **Project name**, type *TypeEquivalenceClient*, and then select **Create**.</span></span> <span data-ttu-id="58d7c-191">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="58d7c-191">The new project is created.</span></span>
   
1. <span data-ttu-id="58d7c-192">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceClient,** , puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-192">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58d7c-193">Sélectionnez **Build** dans le volet gauche de l’écran **Propriétés** , puis définissez le **chemin de sortie** sur le même emplacement que celui que vous avez utilisé pour le projet TypeEquivalenceInterface, par exemple *C:\TypeEquivalenceSample*.</span><span class="sxs-lookup"><span data-stu-id="58d7c-193">Select **Build** on the left pane of the **Properties** screen, and then set the **Output path** to the same location you used for the TypeEquivalenceInterface project, for example, *C:\TypeEquivalenceSample*.</span></span>
   
1. <span data-ttu-id="58d7c-194">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceClient,** et sélectionnez **Ajouter** une**référence**de  > .</span><span class="sxs-lookup"><span data-stu-id="58d7c-194">In **Solution Explorer**, right-click the **TypeEquivalenceClient** project and select **Add** > **Reference**.</span></span> 
   
1. <span data-ttu-id="58d7c-195">Dans la boîte de dialogue **Gestionnaire de références** , si le fichier **TypeEquivalenceInterface. dll** est déjà listé, sélectionnez-le.</span><span class="sxs-lookup"><span data-stu-id="58d7c-195">In the **Reference Manager** dialog, if the **TypeEquivalenceInterface.dll** file is already listed, select it.</span></span> <span data-ttu-id="58d7c-196">Si ce n’est pas le cas, sélectionnez **Parcourir**, accédez au dossier du chemin de sortie, sélectionnez le fichier *TypeEquivalenceInterface. dll* (pas le fichier *TypeEquivalenceRuntime. dll*), puis sélectionnez **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-196">If not, select **Browse**, browse to the output path folder, select the *TypeEquivalenceInterface.dll* file (not the *TypeEquivalenceRuntime.dll*), and select **Add**.</span></span> <span data-ttu-id="58d7c-197">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-197">Select **OK**.</span></span>
   
1. <span data-ttu-id="58d7c-198">Dans **Explorateur de solutions**, développez le dossier **références** et sélectionnez la référence **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="58d7c-198">In **Solution Explorer**, expand the **References** folder and select the **TypeEquivalenceInterface** reference.</span></span> <span data-ttu-id="58d7c-199">Dans le volet **Propriétés** , affectez à **incorporer les types d’interopérabilité** la **valeur true**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-199">In the **Properties** pane, set **Embed Interop Types** to **True**.</span></span>
   
1. <span data-ttu-id="58d7c-200">Ouvrez le fichier *Program.cs* ou *Module1. vb* dans l’éditeur de code, puis remplacez son contenu par le code suivant pour créer le programme client :</span><span class="sxs-lookup"><span data-stu-id="58d7c-200">Open the *Program.cs* or *Module1.vb* file in the code editor, and replace its contents with the following code to create the client program:</span></span>
   
   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;
   using TypeEquivalenceInterface;
   using System.Reflection;
   
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
   Imports TypeEquivalenceInterface
   Imports System.Reflection
   
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
   
1. <span data-ttu-id="58d7c-201">Sélectionnez **fichier**  > **enregistrer tout** ou appuyez sur **CTRL** +**MAJ** +**S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="58d7c-201">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58d7c-202">Appuyez sur **Ctrl** +**F5** pour générer et exécuter le programme.</span><span class="sxs-lookup"><span data-stu-id="58d7c-202">Press **Ctrl**+**F5** to build and run the program.</span></span> <span data-ttu-id="58d7c-203">Notez que la sortie de la console retourne la version de l’assembly **1.0.0.0**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-203">Note that the console output returns the assembly version **1.0.0.0**.</span></span> 
   
## <a name="modify-the-interface"></a><span data-ttu-id="58d7c-204">Modifier l’interface</span><span class="sxs-lookup"><span data-stu-id="58d7c-204">Modify the interface</span></span>

<span data-ttu-id="58d7c-205">À présent, modifiez l’assembly d’interface et modifiez sa version.</span><span class="sxs-lookup"><span data-stu-id="58d7c-205">Now, modify the interface assembly, and change its version.</span></span> 

1. <span data-ttu-id="58d7c-206">Dans Visual Studio, sélectionnez **fichier**  > **ouvrir**  > **projet/solution**, puis ouvrez le projet **TypeEquivalenceInterface** .</span><span class="sxs-lookup"><span data-stu-id="58d7c-206">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceInterface** project.</span></span>
   
1. <span data-ttu-id="58d7c-207">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-207">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58d7c-208">Sélectionnez **application** dans le volet gauche de l’écran **Propriétés** , puis sélectionnez informations de l' **assembly**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-208">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span> 
   
1. <span data-ttu-id="58d7c-209">Dans la boîte de dialogue informations de l' **assembly** , modifiez les valeurs version de l' **assembly** et **version du fichier** sur *2.0.0.0*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-209">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58d7c-210">Ouvrez le fichier *SampleInterface.cs* ou *SampleInterface. vb* et ajoutez la ligne de code suivante à l’interface `ISampleInterface` :</span><span class="sxs-lookup"><span data-stu-id="58d7c-210">Open the *SampleInterface.cs* or *SampleInterface.vb* file, and add the following line of code to the `ISampleInterface` interface:</span></span>
   
   ```csharp
   DateTime GetDate();
   ```
   
   ```vb
   Function GetDate() As Date
   ```
   
1. <span data-ttu-id="58d7c-211">Sélectionnez **fichier**  > **enregistrer tout** ou appuyez sur **CTRL** +**MAJ** +**S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="58d7c-211">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58d7c-212">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceInterface** , puis sélectionnez **générer**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-212">In **Solution Explorer**, right-click the **TypeEquivalenceInterface** project and select **Build**.</span></span> <span data-ttu-id="58d7c-213">Une nouvelle version du fichier DLL de la bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération.</span><span class="sxs-lookup"><span data-stu-id="58d7c-213">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="modify-the-runtime-class"></a><span data-ttu-id="58d7c-214">Modifier la classe d’exécution</span><span class="sxs-lookup"><span data-stu-id="58d7c-214">Modify the runtime class</span></span>

<span data-ttu-id="58d7c-215">Modifiez également la classe Runtime et mettez à jour sa version.</span><span class="sxs-lookup"><span data-stu-id="58d7c-215">Also modify the runtime class and update its version.</span></span> 

1. <span data-ttu-id="58d7c-216">Dans Visual Studio, sélectionnez **fichier**  > **ouvrir**  > **projet/solution**, puis ouvrez le projet **TypeEquivalenceRuntime** .</span><span class="sxs-lookup"><span data-stu-id="58d7c-216">In Visual Studio, select **File** > **Open** > **Project/Solution**, and open the **TypeEquivalenceRuntime** project.</span></span>
   
1. <span data-ttu-id="58d7c-217">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-217">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Properties**.</span></span> 
   
1. <span data-ttu-id="58d7c-218">Sélectionnez **application** dans le volet gauche de l’écran **Propriétés** , puis sélectionnez informations de l' **assembly**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-218">Select **Application** on the left pane of the **Properties** screen, and then select **Assembly Information**.</span></span> 
   
1. <span data-ttu-id="58d7c-219">Dans la boîte de dialogue informations de l' **assembly** , modifiez les valeurs version de l' **assembly** et **version du fichier** sur *2.0.0.0*, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-219">In the **Assembly Information** dialog box, change the **Assembly version** and **File version** values to *2.0.0.0*, and then select **OK**.</span></span>
   
1. <span data-ttu-id="58d7c-220">Ouvrez le fichier *SampleClass.cs* ou *SampleClass. vb* , puis ajoutez le code suivant à la classe `SampleClass` :</span><span class="sxs-lookup"><span data-stu-id="58d7c-220">Open the *SampleClass.cs* or *SampleClass.vb* file, and add the following code to the `SampleClass` class:</span></span>
   
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
   
1. <span data-ttu-id="58d7c-221">Sélectionnez **fichier**  > **enregistrer tout** ou appuyez sur **CTRL** +**MAJ** +**S** pour enregistrer les fichiers et le projet.</span><span class="sxs-lookup"><span data-stu-id="58d7c-221">Select **File** > **Save All** or press **Ctrl**+**Shift**+**S** to save the files and project.</span></span>
   
1. <span data-ttu-id="58d7c-222">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TypeEquivalenceRuntime** et sélectionnez **générer**.</span><span class="sxs-lookup"><span data-stu-id="58d7c-222">In **Solution Explorer**, right-click the **TypeEquivalenceRuntime** project and select **Build**.</span></span> <span data-ttu-id="58d7c-223">Une nouvelle version du fichier DLL de la bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération.</span><span class="sxs-lookup"><span data-stu-id="58d7c-223">A new version of the class library DLL file is compiled and saved to the build output path.</span></span>

## <a name="run-the-updated-client-program"></a><span data-ttu-id="58d7c-224">Exécuter le programme client mis à jour</span><span class="sxs-lookup"><span data-stu-id="58d7c-224">Run the updated client program</span></span> 

<span data-ttu-id="58d7c-225">Accédez à l’emplacement du dossier de sortie de la génération et exécutez *TypeEquivalenceClient,. exe*.</span><span class="sxs-lookup"><span data-stu-id="58d7c-225">Go to the build output folder location and run *TypeEquivalenceClient.exe*.</span></span> <span data-ttu-id="58d7c-226">Notez que la sortie de la console reflète désormais la nouvelle version de l’assembly `TypeEquivalenceRuntime`, *2.0.0.0*, sans le programme en cours de recompilation.</span><span class="sxs-lookup"><span data-stu-id="58d7c-226">Note that the console output now reflects the new version of the `TypeEquivalenceRuntime` assembly, *2.0.0.0*, without the program being recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="58d7c-227">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58d7c-227">See also</span></span>

- [<span data-ttu-id="58d7c-228">-link (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="58d7c-228">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="58d7c-229">-Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58d7c-229">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="58d7c-230">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="58d7c-230">C# programming guide</span></span>](../../csharp/programming-guide/index.md)
- [<span data-ttu-id="58d7c-231">Concepts de programmation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58d7c-231">Programming concepts (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="58d7c-232">Programmer avec des assemblys</span><span class="sxs-lookup"><span data-stu-id="58d7c-232">Program with assemblies</span></span>](program.md)
- [<span data-ttu-id="58d7c-233">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="58d7c-233">Assemblies in .NET</span></span>](index.md)
