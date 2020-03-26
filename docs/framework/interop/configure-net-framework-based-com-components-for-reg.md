---
title: "Comment : configurer les composants COM .NET Framework pour l'activation sans inscription"
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: 9e273bd3e4bf2bb6945fe48c850783a54fa9a869
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291753"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="94a26-102">Comment : configurer les composants COM .NET Framework pour l'activation sans inscription</span><span class="sxs-lookup"><span data-stu-id="94a26-102">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>
<span data-ttu-id="94a26-103">L’activation sans inscription des composants .NET Framework n’est que légèrement plus compliquée que pour les composants COM.</span><span class="sxs-lookup"><span data-stu-id="94a26-103">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="94a26-104">L’installation requiert deux manifestes :</span><span class="sxs-lookup"><span data-stu-id="94a26-104">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="94a26-105">Les applications COM doivent avoir un manifeste d’application de style Win32 pour identifier le composant managé.</span><span class="sxs-lookup"><span data-stu-id="94a26-105">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="94a26-106">Les composants .NET Framework doivent avoir un manifeste de composant pour les informations d’activation nécessaires au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="94a26-106">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="94a26-107">Cette rubrique explique comment associer un manifeste d’application à une application, comment associer un manifeste de composant à un composant et comment incorporer un manifeste de composant dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="94a26-107">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
## <a name="create-an-application-manifest"></a><span data-ttu-id="94a26-108">Créer un manifeste d’application</span><span class="sxs-lookup"><span data-stu-id="94a26-108">Create an application manifest</span></span>  
  
1. <span data-ttu-id="94a26-109">À l’aide d’un éditeur XML, créez (ou modifiez) le manifeste d’application de l’application COM qui interagit avec un ou plusieurs composants managés.</span><span class="sxs-lookup"><span data-stu-id="94a26-109">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="94a26-110">Insérez l’en-tête standard suivant au début du fichier :</span><span class="sxs-lookup"><span data-stu-id="94a26-110">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     <span data-ttu-id="94a26-111">Pour plus d’informations sur les éléments de manifeste et leurs attributs, consultez [Manifestes d’application](/windows/desktop/SbsCs/application-manifests).</span><span class="sxs-lookup"><span data-stu-id="94a26-111">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="94a26-112">Identifiez le propriétaire du manifeste.</span><span class="sxs-lookup"><span data-stu-id="94a26-112">Identify the owner of the manifest.</span></span> <span data-ttu-id="94a26-113">Dans l’exemple suivant, le fichier manifeste appartient à `myComApp` version 1.</span><span class="sxs-lookup"><span data-stu-id="94a26-113">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />
    </assembly>  
    ```  
  
4. <span data-ttu-id="94a26-114">Identifiez les assemblys dépendants.</span><span class="sxs-lookup"><span data-stu-id="94a26-114">Identify dependent assemblies.</span></span> <span data-ttu-id="94a26-115">Dans l’exemple suivant, `myComApp` dépend de `myManagedComp`.</span><span class="sxs-lookup"><span data-stu-id="94a26-115">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="x86"
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myManagedComp"
                        version="6.0.0.0"
                        processorArchitecture="X86"
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="94a26-116">Nommez et enregistrez le fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="94a26-116">Save and name the manifest file.</span></span> <span data-ttu-id="94a26-117">Le nom d’un manifeste d’application est le nom de l’exécutable d’assembly suivi de l’extension .manifest.</span><span class="sxs-lookup"><span data-stu-id="94a26-117">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="94a26-118">Par exemple, le nom du fichier manifeste d’application de myComApp.exe est myComApp.exe.manifest.</span><span class="sxs-lookup"><span data-stu-id="94a26-118">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
<span data-ttu-id="94a26-119">Vous pouvez installer un manifeste d’application dans le même répertoire que l’application COM.</span><span class="sxs-lookup"><span data-stu-id="94a26-119">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="94a26-120">Vous pouvez également l’ajouter en tant que ressource au fichier .exe de l’application.</span><span class="sxs-lookup"><span data-stu-id="94a26-120">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="94a26-121">Pour plus d’informations, voir [à propos des assemblées côte à côte](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span><span class="sxs-lookup"><span data-stu-id="94a26-121">For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
## <a name="create-a-component-manifest"></a><span data-ttu-id="94a26-122">Créer un manifeste de composant</span><span class="sxs-lookup"><span data-stu-id="94a26-122">Create a component manifest</span></span>  
  
1. <span data-ttu-id="94a26-123">À l’aide d’un éditeur XML, créez un manifeste de composant pour décrire l’assembly managé.</span><span class="sxs-lookup"><span data-stu-id="94a26-123">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="94a26-124">Insérez l’en-tête standard suivant au début du fichier :</span><span class="sxs-lookup"><span data-stu-id="94a26-124">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. <span data-ttu-id="94a26-125">Identifiez le propriétaire du fichier.</span><span class="sxs-lookup"><span data-stu-id="94a26-125">Identify the owner of the file.</span></span> <span data-ttu-id="94a26-126">L’élément `<assemblyIdentity>` de l’élément `<dependentAssembly>` dans le fichier manifeste d’application doit correspondre à celui figurant dans le manifeste de composant.</span><span class="sxs-lookup"><span data-stu-id="94a26-126">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="94a26-127">Dans l’exemple suivant, le fichier manifeste appartient à `myManagedComp` version 1.2.3.4.</span><span class="sxs-lookup"><span data-stu-id="94a26-127">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />
    </assembly>
    ```  
  
4. <span data-ttu-id="94a26-128">Identifiez chaque classe dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="94a26-128">Identify each class in the assembly.</span></span> <span data-ttu-id="94a26-129">Utilisez l’élément `<clrClass>` pour identifier de manière unique chaque classe dans l’assembly managé.</span><span class="sxs-lookup"><span data-stu-id="94a26-129">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="94a26-130">L’élément, qui est un sous-élément de l’élément `<assembly>`, a les attributs décrits dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="94a26-130">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="94a26-131">Attribut</span><span class="sxs-lookup"><span data-stu-id="94a26-131">Attribute</span></span>|<span data-ttu-id="94a26-132">Description</span><span class="sxs-lookup"><span data-stu-id="94a26-132">Description</span></span>|<span data-ttu-id="94a26-133">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="94a26-133">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="94a26-134">Identificateur qui spécifie la classe à activer.</span><span class="sxs-lookup"><span data-stu-id="94a26-134">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="94a26-135">Oui</span><span class="sxs-lookup"><span data-stu-id="94a26-135">Yes</span></span>|  
    |`description`|<span data-ttu-id="94a26-136">Chaîne qui informe l’utilisateur sur le composant.</span><span class="sxs-lookup"><span data-stu-id="94a26-136">A string that informs the user about the component.</span></span> <span data-ttu-id="94a26-137">L’attribut par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="94a26-137">An empty string is the default.</span></span>|<span data-ttu-id="94a26-138">Non </span><span class="sxs-lookup"><span data-stu-id="94a26-138">No</span></span>|  
    |`name`|<span data-ttu-id="94a26-139">Chaîne représentant la classe managée.</span><span class="sxs-lookup"><span data-stu-id="94a26-139">A string that represents the managed class.</span></span>|<span data-ttu-id="94a26-140">Oui</span><span class="sxs-lookup"><span data-stu-id="94a26-140">Yes</span></span>|  
    |`progid`|<span data-ttu-id="94a26-141">Identificateur à utiliser pour une activation à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="94a26-141">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="94a26-142">Non </span><span class="sxs-lookup"><span data-stu-id="94a26-142">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="94a26-143">Modèle de thread COM.</span><span class="sxs-lookup"><span data-stu-id="94a26-143">The COM threading model.</span></span> <span data-ttu-id="94a26-144">"Both" est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="94a26-144">"Both" is the default value.</span></span>|<span data-ttu-id="94a26-145">Non </span><span class="sxs-lookup"><span data-stu-id="94a26-145">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="94a26-146">Spécifie la version du CLR (Common Language Runtime) à utiliser.</span><span class="sxs-lookup"><span data-stu-id="94a26-146">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="94a26-147">Si vous ne spécifiez pas cet attribut et que le CLR n’est pas déjà chargé, le composant est chargé avec la version du CLR la plus récente, antérieure à la version CLR 4.</span><span class="sxs-lookup"><span data-stu-id="94a26-147">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="94a26-148">Si vous spécifiez v1.0.3705, v1.1.4322 ou v2.0.50727, la version passe automatiquement à la version du CLR installée la plus récente antérieure à la version CLR 4 (habituellement v2.0.50727).</span><span class="sxs-lookup"><span data-stu-id="94a26-148">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="94a26-149">Si une autre version du CLR est déjà chargée et que la version spécifiée peut être chargée in-process côte à côte, la version spécifiée est chargée ; sinon, le CLR chargé est utilisé.</span><span class="sxs-lookup"><span data-stu-id="94a26-149">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="94a26-150">Cela peut provoquer un échec de chargement.</span><span class="sxs-lookup"><span data-stu-id="94a26-150">This might cause a load failure.</span></span>|<span data-ttu-id="94a26-151">Non </span><span class="sxs-lookup"><span data-stu-id="94a26-151">No</span></span>|  
    |`tlbid`|<span data-ttu-id="94a26-152">Identificateur de la bibliothèque de types qui contient les informations de type sur la classe.</span><span class="sxs-lookup"><span data-stu-id="94a26-152">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="94a26-153">Non </span><span class="sxs-lookup"><span data-stu-id="94a26-153">No</span></span>|  
  
     <span data-ttu-id="94a26-154">Toutes les balises d’attribut respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="94a26-154">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="94a26-155">Vous pouvez obtenir des CLSID, des ProgID, des modèles de thread et la version du runtime en affichant la bibliothèque de types exportée de l’assembly à l’aide de l’explorateur d’objets OLE/COM (Oleview.exe).</span><span class="sxs-lookup"><span data-stu-id="94a26-155">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="94a26-156">Le manifeste de composant suivant identifie deux classes, `testClass1` et `testClass2`.</span><span class="sxs-lookup"><span data-stu-id="94a26-156">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="94a26-157">Nommez et enregistrez le fichier manifeste.</span><span class="sxs-lookup"><span data-stu-id="94a26-157">Save and name the manifest file.</span></span> <span data-ttu-id="94a26-158">Le nom d’un manifeste de composant est le nom de la bibliothèque d’assemblys suivi de l’extension .manifest.</span><span class="sxs-lookup"><span data-stu-id="94a26-158">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="94a26-159">Par exemple, le nom de myManagedComp.dll est myManagedComp.manifest.</span><span class="sxs-lookup"><span data-stu-id="94a26-159">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="94a26-160">Vous devez incorporer le manifeste de composant en tant que ressource dans l’assembly.</span><span class="sxs-lookup"><span data-stu-id="94a26-160">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="94a26-161">Pour incorporer un manifeste de composant dans un assembly managé</span><span class="sxs-lookup"><span data-stu-id="94a26-161">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="94a26-162">Créez un script de ressources qui contient l’instruction suivante :</span><span class="sxs-lookup"><span data-stu-id="94a26-162">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="94a26-163">Dans cette instruction, `myManagedComp.manifest` est le nom du manifeste de composant incorporé.</span><span class="sxs-lookup"><span data-stu-id="94a26-163">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="94a26-164">Pour cet exemple, le nom du fichier de script est `myresource.rc`.</span><span class="sxs-lookup"><span data-stu-id="94a26-164">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="94a26-165">Compilez le script à l’aide de l’outil Compilateur de ressources Microsoft Windows (Rc.exe).</span><span class="sxs-lookup"><span data-stu-id="94a26-165">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="94a26-166">Saisissez ensuite la commande suivante dans l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="94a26-166">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="94a26-167">Rc.exe génère le fichier de ressources `myresource.res`.</span><span class="sxs-lookup"><span data-stu-id="94a26-167">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="94a26-168">Compilez de nouveau le fichier source de l’assembly et spécifiez le fichier de ressources à l’aide de l’option **/win32res** :</span><span class="sxs-lookup"><span data-stu-id="94a26-168">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="94a26-169">Encore `myresource.res` une fois, est le nom du fichier de ressources contenant des ressources intégrées.</span><span class="sxs-lookup"><span data-stu-id="94a26-169">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94a26-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94a26-170">See also</span></span>

- [<span data-ttu-id="94a26-171">COM Interop sans inscription</span><span class="sxs-lookup"><span data-stu-id="94a26-171">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="94a26-172">[Configuration requise pour COM Interop sans inscription](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="94a26-172">[Requirements for Registration-Free COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="94a26-173">[Configurer les composants COM pour l’activation sans inscription](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="94a26-173">[Configuring COM Components for Registration-Free Activation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="94a26-174">[Activation sans inscription de composants .NET : une procédure pas à pas](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="94a26-174">[Registration-Free Activation of .NET-Based Components: A Walkthrough](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
