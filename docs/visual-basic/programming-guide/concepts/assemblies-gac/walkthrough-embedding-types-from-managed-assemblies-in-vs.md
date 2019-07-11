---
title: 'Procédure pas à pas : Incorporer des types provenant d’assemblys managés dans Visual Studio (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
ms.openlocfilehash: 0c0de529a0005c9dbaf1f8d0f25957b217280e31
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753025"
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a><span data-ttu-id="8727c-102">Procédure pas à pas : Incorporer des types provenant d’assemblys managés dans Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8727c-102">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="8727c-103">Si vous incorporez des informations de type d’un assembly managé avec nom fort, vous pouvez coupler faiblement des types dans une application pour obtenir une indépendance de version.</span><span class="sxs-lookup"><span data-stu-id="8727c-103">If you embed type information from a strong-named managed assembly, you can loosely couple types in an application to achieve version independence.</span></span> <span data-ttu-id="8727c-104">Autrement dit, votre programme peut être écrit de façon à ce qu’il utilise des types de plusieurs versions d’une bibliothèque managée sans que vous n’ayez à effectuer de recompilation pour chaque version.</span><span class="sxs-lookup"><span data-stu-id="8727c-104">That is, your program can be written to use types from multiple versions of a managed library without having to be recompiled for each version.</span></span>

<span data-ttu-id="8727c-105">L’incorporation de type est fréquemment utilisée avec COM Interop, par exemple pour une application qui utilise des objets Automation de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="8727c-105">Type embedding is frequently used with COM interop, such as an application that uses automation objects from Microsoft Office.</span></span> <span data-ttu-id="8727c-106">L’incorporation des informations de type permet à la même build d’un programme de fonctionner avec différentes versions de Microsoft Office sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="8727c-106">Embedding type information enables the same build of a program to work with different versions of Microsoft Office on different computers.</span></span> <span data-ttu-id="8727c-107">Toutefois, vous pouvez également utiliser l’incorporation de type avec une solution totalement managée.</span><span class="sxs-lookup"><span data-stu-id="8727c-107">However, you can also use type embedding with a fully managed solution.</span></span>

<span data-ttu-id="8727c-108">Les informations de type peuvent être incorporées à partir d’un assembly doté des caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="8727c-108">Type information can be embedded from an assembly that has the following characteristics:</span></span>

- <span data-ttu-id="8727c-109">L’assembly expose au moins une interface publique.</span><span class="sxs-lookup"><span data-stu-id="8727c-109">The assembly exposes at least one public interface.</span></span>

- <span data-ttu-id="8727c-110">Les interfaces incorporées sont annotées avec un attribut `ComImport` et un attribut `Guid` (et un GUID unique).</span><span class="sxs-lookup"><span data-stu-id="8727c-110">The embedded interfaces are annotated with a `ComImport` attribute and a `Guid` attribute (and a unique GUID).</span></span>

- <span data-ttu-id="8727c-111">L’assembly est annoté avec l’attribut `ImportedFromTypeLib` ou l’attribut `PrimaryInteropAssembly` et un attribut `Guid` au niveau de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8727c-111">The assembly is annotated with the `ImportedFromTypeLib` attribute or the `PrimaryInteropAssembly` attribute, and an assembly-level `Guid` attribute.</span></span> <span data-ttu-id="8727c-112">(Par défaut, les modèles de projet Visual Basic incluent un niveau de l’assembly `Guid` attribut.)</span><span class="sxs-lookup"><span data-stu-id="8727c-112">(By default, Visual Basic project templates include an assembly-level `Guid` attribute.)</span></span>

<span data-ttu-id="8727c-113">Après avoir spécifié les interfaces publiques qui peuvent être incorporées, vous pouvez créer des classes runtime qui implémentent ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="8727c-113">After you have specified the public interfaces that can be embedded, you can create runtime classes that implement those interfaces.</span></span> <span data-ttu-id="8727c-114">Un programme client peut ensuite incorporer les informations de type pour ces interfaces au moment de la conception en référençant l’assembly qui contient les interfaces publiques et en affectant à la propriété `Embed Interop Types` de la référence la valeur `True`.</span><span class="sxs-lookup"><span data-stu-id="8727c-114">A client program can then embed the type information for those interfaces at design time by referencing the assembly that contains the public interfaces and setting the `Embed Interop Types` property of the reference to `True`.</span></span> <span data-ttu-id="8727c-115">Cela revient à utiliser le compilateur de ligne de commande et à référencer l’assembly à l’aide de l’option de compilateur `/link`.</span><span class="sxs-lookup"><span data-stu-id="8727c-115">This is equivalent to using the command line compiler and referencing the assembly by using the `/link` compiler option.</span></span> <span data-ttu-id="8727c-116">Le programme client peut ensuite charger des instances de vos objets d’exécution possédant le même type que ces interfaces.</span><span class="sxs-lookup"><span data-stu-id="8727c-116">The client program can then load instances of your runtime objects typed as those interfaces.</span></span> <span data-ttu-id="8727c-117">Si vous créez une version de votre assembly runtime avec nom fort, le programme client n’a pas besoin d’être recompilé avec l’assembly runtime mis à jour.</span><span class="sxs-lookup"><span data-stu-id="8727c-117">If you create a new version of your strong-named runtime assembly, the client program does not have to be recompiled with the updated runtime assembly.</span></span> <span data-ttu-id="8727c-118">En revanche, le programme client continue d’utiliser la version de l’assembly runtime disponible avec les informations de type incorporées pour les interfaces publiques.</span><span class="sxs-lookup"><span data-stu-id="8727c-118">Instead, the client program continues to use whichever version of the runtime assembly is available to it, using the embedded type information for the public interfaces.</span></span>

<span data-ttu-id="8727c-119">Étant donné que la fonction principale de l’incorporation de type est de prendre en charge l’incorporation d’informations de type à partir d’assemblys COM Interop, les limitations suivantes s’appliquent quand vous incorporez des informations de type dans une solution totalement managée :</span><span class="sxs-lookup"><span data-stu-id="8727c-119">Because the primary function of type embedding is to support embedding of type information from COM interop assemblies, the following limitations apply when you embed type information in a fully managed solution:</span></span>

- <span data-ttu-id="8727c-120">Seuls les attributs spécifiques à COM Interop sont incorporés ; les autres attributs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="8727c-120">Only attributes specific to COM interop are embedded; other attributes are ignored.</span></span>

- <span data-ttu-id="8727c-121">Si un type utilise des paramètres génériques et que le type du paramètre générique est un type incorporé, ce type ne peut pas être utilisé au-delà de la limite de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="8727c-121">If a type uses generic parameters and the type of the generic parameter is an embedded type, that type cannot be used across an assembly boundary.</span></span> <span data-ttu-id="8727c-122">Les exemples de passage de la limite de l’assembly incluent l’appel d’une méthode à partir d’un autre assembly ou la dérivation d’un type à partir d’un type défini dans un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="8727c-122">Examples of crossing an assembly boundary include calling a method from another assembly or a deriving a type from a type defined in another assembly.</span></span>

- <span data-ttu-id="8727c-123">Les constantes ne sont pas incorporées.</span><span class="sxs-lookup"><span data-stu-id="8727c-123">Constants are not embedded.</span></span>

- <span data-ttu-id="8727c-124">La classe <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ne prend pas en charge un type incorporé comme clé.</span><span class="sxs-lookup"><span data-stu-id="8727c-124">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class does not support an embedded type as a key.</span></span> <span data-ttu-id="8727c-125">Vous pouvez implémenter votre propre type de dictionnaire pour prendre en charge un type incorporé comme clé.</span><span class="sxs-lookup"><span data-stu-id="8727c-125">You can implement your own dictionary type to support an embedded type as a key.</span></span>

 <span data-ttu-id="8727c-126">Dans cette procédure pas à pas, vous exécuterez les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8727c-126">In this walkthrough, you will do the following:</span></span>

- <span data-ttu-id="8727c-127">Créer un assembly avec nom fort doté d’une interface publique contenant des informations de type qui peuvent être incorporées.</span><span class="sxs-lookup"><span data-stu-id="8727c-127">Create a strong-named assembly that has a public interface that contains type information that can be embedded.</span></span>

- <span data-ttu-id="8727c-128">Créer un assembly runtime avec nom fort qui implémente cette interface publique.</span><span class="sxs-lookup"><span data-stu-id="8727c-128">Create a strong-named runtime assembly that implements that public interface.</span></span>

- <span data-ttu-id="8727c-129">Créer un programme client qui incorpore les informations de type de l’interface publique et crée une instance de la classe à partir de l’assembly runtime.</span><span class="sxs-lookup"><span data-stu-id="8727c-129">Create a client program that embeds the type information from the public interface and creates an instance of the class from the runtime assembly.</span></span>

- <span data-ttu-id="8727c-130">Modifier et régénérer l’assembly runtime.</span><span class="sxs-lookup"><span data-stu-id="8727c-130">Modify and rebuild the runtime assembly.</span></span>

- <span data-ttu-id="8727c-131">Exécuter le programme client pour constater que la nouvelle version de l’assembly runtime est utilisée sans devoir recompiler le programme client.</span><span class="sxs-lookup"><span data-stu-id="8727c-131">Run the client program to see that the new version of the runtime assembly is being used without having to recompile the client program.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="creating-an-interface"></a><span data-ttu-id="8727c-132">Création d’une interface</span><span class="sxs-lookup"><span data-stu-id="8727c-132">Creating an Interface</span></span>

### <a name="to-create-the-type-equivalence-interface-project"></a><span data-ttu-id="8727c-133">Pour créer le projet d’interface d’équivalence des types</span><span class="sxs-lookup"><span data-stu-id="8727c-133">To create the type equivalence interface project</span></span>

1. <span data-ttu-id="8727c-134">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="8727c-134">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="8727c-135">Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8727c-135">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="8727c-136">Sélectionnez **Bibliothèque de classes** dans le volet **Modèles**.</span><span class="sxs-lookup"><span data-stu-id="8727c-136">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="8727c-137">Dans la zone **Nom**, tapez `TypeEquivalenceInterface`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8727c-137">In the **Name** box, type `TypeEquivalenceInterface`, and then click **OK**.</span></span> <span data-ttu-id="8727c-138">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="8727c-138">The new project is created.</span></span>

3. <span data-ttu-id="8727c-139">Dans **l’Explorateur de solutions**, cliquez sur le fichier Class1.vb et cliquez sur **renommer**.</span><span class="sxs-lookup"><span data-stu-id="8727c-139">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="8727c-140">Renommez le fichier `ISampleInterface.vb` et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="8727c-140">Rename the file to `ISampleInterface.vb` and press ENTER.</span></span> <span data-ttu-id="8727c-141">Quand vous renommez le fichier, la classe est également renommée `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="8727c-141">Renaming the file will also rename the class to `ISampleInterface`.</span></span> <span data-ttu-id="8727c-142">Cette classe représente l’interface publique pour la classe.</span><span class="sxs-lookup"><span data-stu-id="8727c-142">This class will represent the public interface for the class.</span></span>

4. <span data-ttu-id="8727c-143">Cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8727c-143">Right-click the TypeEquivalenceInterface project and click **Properties**.</span></span> <span data-ttu-id="8727c-144">Cliquez sur l’onglet **Compiler**. Affectez au chemin de sortie un emplacement valide sur votre ordinateur de développement, tel que `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="8727c-144">Click the **Compile** tab. Set the output path to a valid location on your development computer, such as `C:\TypeEquivalenceSample`.</span></span> <span data-ttu-id="8727c-145">Cet emplacement sera également utilisé dans une étape ultérieure de cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="8727c-145">This location will also be used in a later step in this walkthrough.</span></span>

5. <span data-ttu-id="8727c-146">Tout en modifiant les propriétés de projet, cliquez sur l’onglet **Signature**. Sélectionnez l’option **Signer l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="8727c-146">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="8727c-147">Dans la liste **Choisir un fichier de clé de nom fort**, cliquez sur **<Nouveau...>** .</span><span class="sxs-lookup"><span data-stu-id="8727c-147">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="8727c-148">Dans la zone **Nom du fichier de clé**, tapez `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="8727c-148">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="8727c-149">Décochez la case **Protéger mon fichier de clé par un mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="8727c-149">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="8727c-150">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8727c-150">Click **OK**.</span></span>

6. <span data-ttu-id="8727c-151">Ouvrez le fichier ISampleInterface.vb.</span><span class="sxs-lookup"><span data-stu-id="8727c-151">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="8727c-152">Ajoutez le code suivant au fichier de classe ISampleInterface pour créer l’interface ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="8727c-152">Add the following code to the ISampleInterface class file to create the ISampleInterface interface.</span></span>

    ```vb
    Imports System.Runtime.InteropServices

    <ComImport()>
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>
    Public Interface ISampleInterface
        Sub GetUserInput()
        ReadOnly Property UserInput As String
    End Interface
    ```

7. <span data-ttu-id="8727c-153">Dans le menu **Outils**, cliquez sur **Créer un Guid**.</span><span class="sxs-lookup"><span data-stu-id="8727c-153">On the **Tools** menu, click **Create Guid**.</span></span> <span data-ttu-id="8727c-154">Dans la boîte de dialogue **Créer un Guid**, cliquez sur **Format du Registre**, puis sur **Copier**.</span><span class="sxs-lookup"><span data-stu-id="8727c-154">In the **Create GUID** dialog box, click **Registry Format** and then click **Copy**.</span></span> <span data-ttu-id="8727c-155">Cliquez sur **Quitter**.</span><span class="sxs-lookup"><span data-stu-id="8727c-155">Click **Exit**.</span></span>

8. <span data-ttu-id="8727c-156">Dans l’attribut `Guid`, supprimez l’exemple de GUID et collez le GUID que vous avez copié à partir de la boîte de dialogue **Créer un Guid**.</span><span class="sxs-lookup"><span data-stu-id="8727c-156">In the `Guid` attribute, delete the sample GUID and paste in the GUID that you copied from the **Create GUID** dialog box.</span></span> <span data-ttu-id="8727c-157">Supprimez les accolades ({}) du GUID copié.</span><span class="sxs-lookup"><span data-stu-id="8727c-157">Remove the braces ({}) from the copied GUID.</span></span>

9. <span data-ttu-id="8727c-158">Dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="8727c-158">On the **Project** menu, click **Show All Files**.</span></span>

10. <span data-ttu-id="8727c-159">Dans **l’Explorateur de solutions**, développez le **mon projet** dossier.</span><span class="sxs-lookup"><span data-stu-id="8727c-159">In **Solution Explorer**, expand the **My Project** folder.</span></span> <span data-ttu-id="8727c-160">Double-cliquez sur le AssemblyInfo.vb.</span><span class="sxs-lookup"><span data-stu-id="8727c-160">Double-click the AssemblyInfo.vb.</span></span> <span data-ttu-id="8727c-161">Ajoutez l’attribut suivant au fichier.</span><span class="sxs-lookup"><span data-stu-id="8727c-161">Add the following attribute to the file.</span></span>

    ```vb
    <Assembly: ImportedFromTypeLib("")>
    ```

    <span data-ttu-id="8727c-162">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="8727c-162">Save the file.</span></span>

11. <span data-ttu-id="8727c-163">Enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="8727c-163">Save the project.</span></span>

12. <span data-ttu-id="8727c-164">Cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="8727c-164">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="8727c-165">Le fichier .dll de bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié (par exemple, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="8727c-165">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-runtime-class"></a><span data-ttu-id="8727c-166">Création d’une classe runtime</span><span class="sxs-lookup"><span data-stu-id="8727c-166">Creating a Runtime Class</span></span>

### <a name="to-create-the-type-equivalence-runtime-project"></a><span data-ttu-id="8727c-167">Pour créer le projet d’exécution d’équivalence des types</span><span class="sxs-lookup"><span data-stu-id="8727c-167">To create the type equivalence runtime project</span></span>

1. <span data-ttu-id="8727c-168">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="8727c-168">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="8727c-169">Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8727c-169">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="8727c-170">Sélectionnez **Bibliothèque de classes** dans le volet **Modèles**.</span><span class="sxs-lookup"><span data-stu-id="8727c-170">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="8727c-171">Dans la zone **Nom**, tapez `TypeEquivalenceRuntime`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8727c-171">In the **Name** box, type `TypeEquivalenceRuntime`, and then click **OK**.</span></span> <span data-ttu-id="8727c-172">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="8727c-172">The new project is created.</span></span>

3. <span data-ttu-id="8727c-173">Dans **l’Explorateur de solutions**, cliquez sur le fichier Class1.vb et cliquez sur **renommer**.</span><span class="sxs-lookup"><span data-stu-id="8727c-173">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="8727c-174">Renommez le fichier `SampleClass.vb` et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="8727c-174">Rename the file to `SampleClass.vb` and press ENTER.</span></span> <span data-ttu-id="8727c-175">Quand vous renommez le fichier, la classe est également renommée `SampleClass`.</span><span class="sxs-lookup"><span data-stu-id="8727c-175">Renaming the file also renames the class to `SampleClass`.</span></span> <span data-ttu-id="8727c-176">Cette classe va implémenter l’interface `ISampleInterface`.</span><span class="sxs-lookup"><span data-stu-id="8727c-176">This class will implement the `ISampleInterface` interface.</span></span>

4. <span data-ttu-id="8727c-177">Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8727c-177">Right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="8727c-178">Cliquez sur l’onglet **Compiler**. Affectez au chemin de sortie le même emplacement que celui que vous avez utilisé dans le projet TypeEquivalenceInterface, par exemple `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="8727c-178">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

5. <span data-ttu-id="8727c-179">Tout en modifiant les propriétés de projet, cliquez sur l’onglet **Signature**. Sélectionnez l’option **Signer l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="8727c-179">While still editing the project properties, click the **Signing** tab. Select the **Sign the assembly** option.</span></span> <span data-ttu-id="8727c-180">Dans la liste **Choisir un fichier de clé de nom fort**, cliquez sur **<Nouveau...>** .</span><span class="sxs-lookup"><span data-stu-id="8727c-180">In the **Choose a strong name key file** list, click **<New...>**.</span></span> <span data-ttu-id="8727c-181">Dans la zone **Nom du fichier de clé**, tapez `key.snk`.</span><span class="sxs-lookup"><span data-stu-id="8727c-181">In the **Key file name** box, type `key.snk`.</span></span> <span data-ttu-id="8727c-182">Décochez la case **Protéger mon fichier de clé par un mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="8727c-182">Clear the **Protect my key file with a password** check box.</span></span> <span data-ttu-id="8727c-183">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8727c-183">Click **OK**.</span></span>

6. <span data-ttu-id="8727c-184">Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="8727c-184">Right-click the TypeEquivalenceRuntime project and click **Add Reference**.</span></span> <span data-ttu-id="8727c-185">Cliquez sur l’onglet **Parcourir** et recherchez le dossier du chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="8727c-185">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="8727c-186">Sélectionnez le fichier TypeEquivalenceInterface.dll et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8727c-186">Select the TypeEquivalenceInterface.dll file and click **OK**.</span></span>

7. <span data-ttu-id="8727c-187">Dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="8727c-187">On the **Project** menu, click **Show All Files**.</span></span>

8. <span data-ttu-id="8727c-188">Dans l’**Explorateur de solutions**, développez le dossier **Références**.</span><span class="sxs-lookup"><span data-stu-id="8727c-188">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="8727c-189">Sélectionnez la référence TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="8727c-189">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="8727c-190">Dans la fenêtre Propriétés de la référence TypeEquivalenceInterface, affectez à la propriété **Version spécifique** la valeur **False**.</span><span class="sxs-lookup"><span data-stu-id="8727c-190">In the Properties window for the TypeEquivalenceInterface reference, set the **Specific Version** property to **False**.</span></span>

9. <span data-ttu-id="8727c-191">Ajoutez le code suivant au fichier de classe SampleClass pour créer la classe SampleClass.</span><span class="sxs-lookup"><span data-stu-id="8727c-191">Add the following code to the SampleClass class file to create the SampleClass class.</span></span>

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

10. <span data-ttu-id="8727c-192">Enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="8727c-192">Save the project.</span></span>

11. <span data-ttu-id="8727c-193">Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="8727c-193">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="8727c-194">Le fichier .dll de bibliothèque de classes est compilé et enregistré dans le chemin de sortie de la génération spécifié (par exemple, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="8727c-194">The class library .dll file is compiled and saved to the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="creating-a-client-project"></a><span data-ttu-id="8727c-195">Création d’un projet client</span><span class="sxs-lookup"><span data-stu-id="8727c-195">Creating a Client Project</span></span>

### <a name="to-create-the-type-equivalence-client-project"></a><span data-ttu-id="8727c-196">Pour créer le projet client d’équivalence des types</span><span class="sxs-lookup"><span data-stu-id="8727c-196">To create the type equivalence client project</span></span>

1. <span data-ttu-id="8727c-197">Dans Visual Studio, dans le menu **Fichier**,pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="8727c-197">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>

2. <span data-ttu-id="8727c-198">Dans la boîte de dialogue **Nouveau projet**, dans le volet **Types de projets**, vérifiez que **Windows** est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8727c-198">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="8727c-199">Sélectionnez **Application console** dans le volet **Modèles**.</span><span class="sxs-lookup"><span data-stu-id="8727c-199">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="8727c-200">Dans la zone **Nom**, tapez `TypeEquivalenceClient`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8727c-200">In the **Name** box, type `TypeEquivalenceClient`, and then click **OK**.</span></span> <span data-ttu-id="8727c-201">Le nouveau projet est créé.</span><span class="sxs-lookup"><span data-stu-id="8727c-201">The new project is created.</span></span>

3. <span data-ttu-id="8727c-202">Cliquez avec le bouton droit sur le projet TypeEquivalenceClient, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8727c-202">Right-click the TypeEquivalenceClient project and click **Properties**.</span></span> <span data-ttu-id="8727c-203">Cliquez sur l’onglet **Compiler**. Affectez au chemin de sortie le même emplacement que celui que vous avez utilisé dans le projet TypeEquivalenceInterface, par exemple `C:\TypeEquivalenceSample`.</span><span class="sxs-lookup"><span data-stu-id="8727c-203">Click the **Compile** tab. Set the output path to the same location you used in the TypeEquivalenceInterface project, for example, `C:\TypeEquivalenceSample`.</span></span>

4. <span data-ttu-id="8727c-204">Cliquez avec le bouton droit sur le projet TypeEquivalenceClient, puis cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="8727c-204">Right-click the TypeEquivalenceClient project and click **Add Reference**.</span></span> <span data-ttu-id="8727c-205">Cliquez sur l’onglet **Parcourir** et recherchez le dossier du chemin de sortie.</span><span class="sxs-lookup"><span data-stu-id="8727c-205">Click the **Browse** tab and browse to the output path folder.</span></span> <span data-ttu-id="8727c-206">Sélectionnez le fichier TypeEquivalenceInterface.dll (pas le fichier TypeEquivalenceRuntime.dll) et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8727c-206">Select the TypeEquivalenceInterface.dll file (not the TypeEquivalenceRuntime.dll) and click **OK**.</span></span>

5. <span data-ttu-id="8727c-207">Dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="8727c-207">On the **Project** menu, click **Show All Files**.</span></span>

6. <span data-ttu-id="8727c-208">Dans l’**Explorateur de solutions**, développez le dossier **Références**.</span><span class="sxs-lookup"><span data-stu-id="8727c-208">In **Solution Explorer**, expand the **References** folder.</span></span> <span data-ttu-id="8727c-209">Sélectionnez la référence TypeEquivalenceInterface.</span><span class="sxs-lookup"><span data-stu-id="8727c-209">Select the TypeEquivalenceInterface reference.</span></span> <span data-ttu-id="8727c-210">Dans la fenêtre Propriétés de la référence TypeEquivalenceInterface, affectez à la propriété **Incorporer les types d’interopérabilité** la valeur **True**.</span><span class="sxs-lookup"><span data-stu-id="8727c-210">In the Properties window for the TypeEquivalenceInterface reference, set the **Embed Interop Types** property to **True**.</span></span>

7. <span data-ttu-id="8727c-211">Ajoutez le code suivant au fichier Module1.vb pour créer le programme client.</span><span class="sxs-lookup"><span data-stu-id="8727c-211">Add the following code to the Module1.vb file to create the client program.</span></span>

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

8. <span data-ttu-id="8727c-212">Appuyez sur CTRL+F5 pour générer et exécuter le programme.</span><span class="sxs-lookup"><span data-stu-id="8727c-212">Press CTRL+F5 to build and run the program.</span></span>

## <a name="modifying-the-interface"></a><span data-ttu-id="8727c-213">Modification de l’interface</span><span class="sxs-lookup"><span data-stu-id="8727c-213">Modifying the Interface</span></span>

### <a name="to-modify-the-interface"></a><span data-ttu-id="8727c-214">Pour modifier l’interface</span><span class="sxs-lookup"><span data-stu-id="8727c-214">To modify the interface</span></span>

1. <span data-ttu-id="8727c-215">Dans Visual Studio, dans le menu **Fichier**, pointez sur **Ouvrir**, puis cliquez sur **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="8727c-215">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="8727c-216">Dans la boîte de dialogue **Ouvrir un projet**, cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8727c-216">In the **Open Project** dialog box, right-click the TypeEquivalenceInterface project, and then click **Properties**.</span></span> <span data-ttu-id="8727c-217">Cliquez sur l’onglet **Application** . Cliquez sur le bouton **Informations de l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="8727c-217">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="8727c-218">Remplacez les valeurs de **Version de l’assembly** et **Version de fichier** par `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="8727c-218">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="8727c-219">Ouvrez le fichier ISampleInterface.vb.</span><span class="sxs-lookup"><span data-stu-id="8727c-219">Open the ISampleInterface.vb file.</span></span> <span data-ttu-id="8727c-220">Ajoutez la ligne de code suivante à l’interface ISampleInterface.</span><span class="sxs-lookup"><span data-stu-id="8727c-220">Add the following line of code to the ISampleInterface interface.</span></span>

    ```vb
    Function GetDate() As Date
    ```

    <span data-ttu-id="8727c-221">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="8727c-221">Save the file.</span></span>

4. <span data-ttu-id="8727c-222">Enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="8727c-222">Save the project.</span></span>

5. <span data-ttu-id="8727c-223">Cliquez avec le bouton droit sur le projet TypeEquivalenceInterface, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="8727c-223">Right-click the TypeEquivalenceInterface project and click **Build**.</span></span> <span data-ttu-id="8727c-224">Une nouvelle version du fichier .dll de bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération spécifié (par exemple, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="8727c-224">A new version of the class library .dll file is compiled and saved in the specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

## <a name="modifying-the-runtime-class"></a><span data-ttu-id="8727c-225">Modification de la classe runtime</span><span class="sxs-lookup"><span data-stu-id="8727c-225">Modifying the Runtime Class</span></span>

### <a name="to-modify-the-runtime-class"></a><span data-ttu-id="8727c-226">Pour modifier la classe runtime</span><span class="sxs-lookup"><span data-stu-id="8727c-226">To modify the runtime class</span></span>

1. <span data-ttu-id="8727c-227">Dans Visual Studio, dans le menu **Fichier**, pointez sur **Ouvrir**, puis cliquez sur **Projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="8727c-227">In Visual Studio, on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>

2. <span data-ttu-id="8727c-228">Dans la boîte de dialogue **Ouvrir un projet**, cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8727c-228">In the **Open Project** dialog box, right-click the TypeEquivalenceRuntime project and click **Properties**.</span></span> <span data-ttu-id="8727c-229">Cliquez sur l’onglet **Application** . Cliquez sur le bouton **Informations de l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="8727c-229">Click the **Application** tab. Click the **Assembly Information** button.</span></span> <span data-ttu-id="8727c-230">Remplacez les valeurs de **Version de l’assembly** et **Version de fichier** par `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="8727c-230">Change the **Assembly Version** and **File Version** values to `2.0.0.0`.</span></span>

3. <span data-ttu-id="8727c-231">Ouvrez le fichier SampleClass.vb.</span><span class="sxs-lookup"><span data-stu-id="8727c-231">Open the SampleClass.vb file.</span></span> <span data-ttu-id="8727c-232">Ajoutez les lignes de code suivantes à la classe SampleClass.</span><span class="sxs-lookup"><span data-stu-id="8727c-232">Add the following lines of code to the SampleClass class.</span></span>

    ```vb
    Public Function GetDate() As DateTime Implements ISampleInterface.GetDate
        Return Now
    End Function
    ```

    <span data-ttu-id="8727c-233">Enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="8727c-233">Save the file.</span></span>

4. <span data-ttu-id="8727c-234">Enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="8727c-234">Save the project.</span></span>

5. <span data-ttu-id="8727c-235">Cliquez avec le bouton droit sur le projet TypeEquivalenceRuntime, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="8727c-235">Right-click the TypeEquivalenceRuntime project and click **Build**.</span></span> <span data-ttu-id="8727c-236">Une version mise à jour du fichier .dll de bibliothèque de classes est compilée et enregistrée dans le chemin de sortie de la génération précédemment spécifié (par exemple, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="8727c-236">An updated version of the class library .dll file is compiled and saved in the previously specified build output path (for example, C:\TypeEquivalenceSample).</span></span>

6. <span data-ttu-id="8727c-237">Dans l’Explorateur de fichiers, ouvrez le dossier du chemin de sortie (par exemple, C:\TypeEquivalenceSample).</span><span class="sxs-lookup"><span data-stu-id="8727c-237">In File Explorer, open the output path folder (for example, C:\TypeEquivalenceSample).</span></span> <span data-ttu-id="8727c-238">Double-cliquez sur le fichier TypeEquivalenceClient.exe pour exécuter le programme.</span><span class="sxs-lookup"><span data-stu-id="8727c-238">Double-click the TypeEquivalenceClient.exe to run the program.</span></span> <span data-ttu-id="8727c-239">Le programme reflète la nouvelle version de l’assembly TypeEquivalenceRuntime sans aucune recompilation.</span><span class="sxs-lookup"><span data-stu-id="8727c-239">The program will reflect the new version of the TypeEquivalenceRuntime assembly without having been recompiled.</span></span>

## <a name="see-also"></a><span data-ttu-id="8727c-240">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8727c-240">See also</span></span>

- [<span data-ttu-id="8727c-241">/link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8727c-241">/link (Visual Basic)</span></span>](../../../../visual-basic/reference/command-line-compiler/link.md)
- [<span data-ttu-id="8727c-242">Concepts de programmation</span><span class="sxs-lookup"><span data-stu-id="8727c-242">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
- [<span data-ttu-id="8727c-243">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="8727c-243">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="8727c-244">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="8727c-244">Assemblies in .NET</span></span>](../../../../standard/assembly/index.md)
