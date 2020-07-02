---
title: 'Procédure : créer des wrappers COM'
description: Créer des wrappers COM (Component Object Model) à l’aide de Visual Studio ou des outils .NET (Tlbimp.exe et Regasm.exe). Les deux méthodes génèrent deux types de wrappers COM.
ms.date: 03/30/2017
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
ms.openlocfilehash: 286526c710287e6efa3e49a7f7c55e3687076e29
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617390"
---
# <a name="how-to-create-com-wrappers"></a><span data-ttu-id="bfd5c-104">Procédure : créer des wrappers COM</span><span class="sxs-lookup"><span data-stu-id="bfd5c-104">How to: Create COM Wrappers</span></span>

<span data-ttu-id="bfd5c-105">Vous pouvez créer des wrappers COM (Component Object Model) à l’aide des fonctionnalités Visual Studio 2005 ou des outils .NET Framework Tlbimp.exe et Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-105">You can create Component Object Model (COM) wrappers by using Visual Studio 2005 features or the .NET Framework tools Tlbimp.exe and Regasm.exe.</span></span> <span data-ttu-id="bfd5c-106">Ces deux méthodes génèrent deux types de wrappers COM :</span><span class="sxs-lookup"><span data-stu-id="bfd5c-106">Both methods generate two types of COM wrappers:</span></span>

- <span data-ttu-id="bfd5c-107">un [wrapper RCW (Runtime Callable Wrapper)](../../standard/native-interop/runtime-callable-wrapper.md) d’une bibliothèque de types pour exécuter un objet COM en code managé ;</span><span class="sxs-lookup"><span data-stu-id="bfd5c-107">A [Runtime Callable Wrapper](../../standard/native-interop/runtime-callable-wrapper.md) from a type library to run a COM object in managed code.</span></span>

- <span data-ttu-id="bfd5c-108">un [wrapper CCW (COM Callable Wrapper)](../../standard/native-interop/com-callable-wrapper.md) avec les paramètres de Registre requis pour exécuter un objet managé dans une application native.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-108">A [COM Callable Wrapper](../../standard/native-interop/com-callable-wrapper.md) with the required registry settings to run a managed object in a native application.</span></span>

<span data-ttu-id="bfd5c-109">Dans Visual Studio 2005, vous pouvez ajouter le wrapper COM à votre projet en tant que référence.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-109">In Visual Studio 2005, you can add the COM wrapper as a reference to your project.</span></span>

## <a name="wrap-com-objects-in-a-managed-application"></a><span data-ttu-id="bfd5c-110">Encapsuler des objets COM dans une application managée</span><span class="sxs-lookup"><span data-stu-id="bfd5c-110">Wrap COM Objects in a Managed Application</span></span>

### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a><span data-ttu-id="bfd5c-111">Pour créer un wrapper RCW à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bfd5c-111">To create a runtime callable wrapper using Visual Studio</span></span>

1. <span data-ttu-id="bfd5c-112">Ouvrez le projet pour votre application managée.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-112">Open the project for your managed application.</span></span>

2. <span data-ttu-id="bfd5c-113">Dans le menu **Projet**, cliquez sur **Afficher tous les fichiers**.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-113">On the **Project** menu, click **Show All Files**.</span></span>

3. <span data-ttu-id="bfd5c-114">Dans le menu **projet** , cliquez sur **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-114">On the **Project** menu, click **Add Reference**.</span></span>

4. <span data-ttu-id="bfd5c-115">Dans la boîte de dialogue Ajouter une référence, cliquez sur l’onglet **COM**, sélectionnez le composant que vous souhaitez utiliser et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-115">In the Add Reference dialog box, click the **COM** tab, select the component you want to use, and click **OK**.</span></span>

     <span data-ttu-id="bfd5c-116">Dans l’**Explorateur de solutions**, notez que le composant COM est ajouté au dossier Références dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-116">In **Solution Explorer**, note that the COM component is added to the References folder in your project.</span></span>

<span data-ttu-id="bfd5c-117">Vous pouvez maintenant écrire le code pour accéder à l’objet COM.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-117">You can now write code to access the COM object.</span></span> <span data-ttu-id="bfd5c-118">Vous pouvez commencer par déclarer l’objet, par exemple avec une instruction `Imports` pour Visual Basic ou une instruction `Using` pour C#.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-118">You can begin by declaring the object, such as with an `Imports` statement for Visual Basic or a `Using` statement for C#.</span></span>

> [!NOTE]
> <span data-ttu-id="bfd5c-119">Si vous souhaitez programmer des composants Microsoft Office, commencez par installer le [package redistribuable d’assemblys pia Microsoft Office](https://www.microsoft.com/Download/details.aspx?id=3508).</span><span class="sxs-lookup"><span data-stu-id="bfd5c-119">If you want to program Microsoft Office components, first install the [Microsoft Office Primary Interop Assemblies Redistributable](https://www.microsoft.com/Download/details.aspx?id=3508).</span></span>
  
### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="bfd5c-120">Pour créer un wrapper RCW à l’aide des outils .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bfd5c-120">To create a runtime callable wrapper using .NET Framework tools</span></span>  
  
- <span data-ttu-id="bfd5c-121">Exécutez l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="bfd5c-121">Run the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md) tool.</span></span>  
  
 <span data-ttu-id="bfd5c-122">Cet outil crée un assembly qui contient des métadonnées de runtime pour les types définis dans la bibliothèque de types d’origine.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-122">This tool creates an assembly that contains run-time metadata for the types defined in the original type library.</span></span>  
  
## <a name="wrap-managed-objects-in-a-native-application"></a><span data-ttu-id="bfd5c-123">Encapsuler des objets managés dans une application native</span><span class="sxs-lookup"><span data-stu-id="bfd5c-123">Wrap Managed Objects in a Native Application</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a><span data-ttu-id="bfd5c-124">Pour créer un wrapper CCW à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bfd5c-124">To create a COM callable wrapper using Visual Studio</span></span>  
  
1. <span data-ttu-id="bfd5c-125">Créez un projet de bibliothèque de classes pour la classe managée que vous souhaitez exécuter en code natif.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-125">Create a Class Library project for the managed class that you want to run in native code.</span></span> <span data-ttu-id="bfd5c-126">La classe doit avoir un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-126">The class must have a parameterless constructor.</span></span>  
  
     <span data-ttu-id="bfd5c-127">Vérifiez que vous disposez d’un numéro de version à quatre parties complet pour votre assembly dans le fichier AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-127">Verify that you have a complete four-part version number for your assembly in the AssemblyInfo file.</span></span> <span data-ttu-id="bfd5c-128">Ce numéro est requis pour assurer le contrôle de version dans le Registre Windows.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-128">This number is required for maintaining versioning in the Windows registry.</span></span> <span data-ttu-id="bfd5c-129">Pour plus d’informations sur les numéros de version, consultez [Contrôle de version des assemblys](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="bfd5c-129">For more information about version numbers, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span>  
  
2. <span data-ttu-id="bfd5c-130">Dans le menu **Projet** , cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-130">On the **Project** menu, click **Properties**.</span></span>  
  
3. <span data-ttu-id="bfd5c-131">Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-131">Click the **Compile** tab.</span></span>  
  
4. <span data-ttu-id="bfd5c-132">Cochez la case **Inscrire pour COM Interop**.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-132">Select the **Register for COM interop** check box.</span></span>  
  
 <span data-ttu-id="bfd5c-133">Quand vous générez le projet, l’assembly est automatiquement inscrit pour COM Interop.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-133">When you build the project, the assembly is automatically registered for COM interop.</span></span> <span data-ttu-id="bfd5c-134">Si vous générez une application native dans Visual Studio 2005, vous pouvez utiliser l’assembly en cliquant sur **Ajouter une référence** dans le menu **Projet**.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-134">If you are building a native application in Visual Studio 2005, you can use the assembly by clicking **Add Reference** on the **Project** menu.</span></span>  
  
### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a><span data-ttu-id="bfd5c-135">Pour créer un wrapper CCW à l’aide des outils .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bfd5c-135">To create a COM callable wrapper using .NET Framework tools</span></span>  
  
<span data-ttu-id="bfd5c-136">Exécutez l’outil [Regasm.exe (outil d’inscription d’assemblys)](../tools/regasm-exe-assembly-registration-tool.md).</span><span class="sxs-lookup"><span data-stu-id="bfd5c-136">Run the [Regasm.exe (Assembly Registration Tool)](../tools/regasm-exe-assembly-registration-tool.md) tool.</span></span>  
  
<span data-ttu-id="bfd5c-137">Cet outil lit les métadonnées de l’assembly et ajoute les entrées nécessaires au Registre.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-137">This tool reads the assembly metadata and adds the necessary entries to the registry.</span></span> <span data-ttu-id="bfd5c-138">Par conséquent, les clients COM peuvent créer des classes .NET Framework en toute transparence.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-138">As a result, COM clients can create .NET Framework classes transparently.</span></span> <span data-ttu-id="bfd5c-139">Vous pouvez utiliser l’assembly comme s’il s’agissait d’une classe COM native.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-139">You can use the assembly as if it were a native COM class.</span></span>  
  
<span data-ttu-id="bfd5c-140">Vous pouvez exécuter Regasm.exe sur un assembly situé dans n’importe quel répertoire, puis [Gacutil.exe (outil Global Assembly Cache)](../tools/gacutil-exe-gac-tool.md) pour le déplacer dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-140">You can run Regasm.exe on an assembly located in any directory, and then run the [Gacutil.exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) to move it to the global assembly cache.</span></span> <span data-ttu-id="bfd5c-141">Le déplacement de l’assembly n’invalide pas les entrées du Registre d’emplacement, car le Global Assembly Cache est toujours examiné si l’assembly est introuvable ailleurs.</span><span class="sxs-lookup"><span data-stu-id="bfd5c-141">Moving the assembly does not invalidate location registry entries, because the global assembly cache is always examined if the assembly is not found elsewhere.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd5c-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfd5c-142">See also</span></span>

- [<span data-ttu-id="bfd5c-143">Wrapper pouvant être appelé par le runtime</span><span class="sxs-lookup"><span data-stu-id="bfd5c-143">Runtime Callable Wrapper</span></span>](../../standard/native-interop/runtime-callable-wrapper.md)
- [<span data-ttu-id="bfd5c-144">Wrapper CCW (COM Callable Wrapper)</span><span class="sxs-lookup"><span data-stu-id="bfd5c-144">COM Callable Wrapper</span></span>](../../standard/native-interop/com-callable-wrapper.md)
