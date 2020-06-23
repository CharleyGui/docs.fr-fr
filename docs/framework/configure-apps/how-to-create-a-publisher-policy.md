---
title: 'Procédure : Créer une stratégie d’éditeur'
description: Découvrez comment les fournisseurs d’assemblys peuvent créer un fichier de stratégie d’éditeur avec un assembly mis à niveau dans .NET, pour stipuler que les applications doivent utiliser la version plus récente.
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 23e9d8144ec5742e0371d566b7af59dc9dd30c9b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105401"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="b00c0-103">Procédure : Créer une stratégie d’éditeur</span><span class="sxs-lookup"><span data-stu-id="b00c0-103">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="b00c0-104">Les fournisseurs d’assemblys peuvent indiquer que les applications doivent utiliser une version plus récente d’un assembly en incluant un fichier de stratégie d’éditeur avec l’assembly mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="b00c0-104">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="b00c0-105">Le fichier de stratégie d’éditeur spécifie la redirection d’assembly et les paramètres de base de code, et utilise le même format qu’un fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="b00c0-105">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="b00c0-106">Le fichier de stratégie d’éditeur est compilé dans un assembly et placé dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="b00c0-106">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="b00c0-107">La création d’une stratégie d’éditeur implique trois étapes :</span><span class="sxs-lookup"><span data-stu-id="b00c0-107">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="b00c0-108">Créez un fichier de stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="b00c0-108">Create a publisher policy file.</span></span>

2. <span data-ttu-id="b00c0-109">Créer un assembly de stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="b00c0-109">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="b00c0-110">Ajoutez l’assembly de stratégie d’éditeur au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="b00c0-110">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="b00c0-111">Le schéma de la stratégie d’éditeur est décrit dans [redirection des versions d’assembly](redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="b00c0-111">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="b00c0-112">L’exemple suivant montre un fichier de stratégie d’éditeur qui redirige une version de `myAssembly` vers une autre.</span><span class="sxs-lookup"><span data-stu-id="b00c0-112">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="b00c0-113">Pour savoir comment spécifier une base de code, consultez [spécification de l’emplacement d’un assembly](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="b00c0-113">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="b00c0-114">Création de l’assembly de stratégie d’éditeur</span><span class="sxs-lookup"><span data-stu-id="b00c0-114">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="b00c0-115">Utilisez [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) pour créer l’assembly de stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="b00c0-115">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="b00c0-116">Pour créer un assembly de stratégie d’éditeur</span><span class="sxs-lookup"><span data-stu-id="b00c0-116">To create a publisher policy assembly</span></span>

<span data-ttu-id="b00c0-117">Entrez la commande suivante à l'invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="b00c0-117">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="b00c0-118">Dans cette commande :</span><span class="sxs-lookup"><span data-stu-id="b00c0-118">In this command:</span></span>

- <span data-ttu-id="b00c0-119">L' `publisherPolicyFile` argument est le nom du fichier de stratégie d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="b00c0-119">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="b00c0-120">L' `publisherPolicyAssemblyFile` argument est le nom de l’assembly de stratégie d’éditeur qui résulte de cette commande.</span><span class="sxs-lookup"><span data-stu-id="b00c0-120">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="b00c0-121">Le nom du fichier de l’assembly doit respecter le format suivant :</span><span class="sxs-lookup"><span data-stu-id="b00c0-121">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="b00c0-122">'policy.majorNumber.minorNumber.mainAssemblyName.dll '</span><span class="sxs-lookup"><span data-stu-id="b00c0-122">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="b00c0-123">L' `keyPairFile` argument est le nom du fichier contenant la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="b00c0-123">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="b00c0-124">Vous devez signer l’assembly et l’assembly de stratégie d’éditeur avec la même paire de clés.</span><span class="sxs-lookup"><span data-stu-id="b00c0-124">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="b00c0-125">L' `processorArchitecture` argument identifie la plateforme ciblée par un assembly spécifique au processeur.</span><span class="sxs-lookup"><span data-stu-id="b00c0-125">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="b00c0-126">La possibilité de cibler une architecture de processeur spécifique est disponible à partir de .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b00c0-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="b00c0-127">La possibilité de cibler une architecture de processeur spécifique est disponible à partir de .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b00c0-127">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="b00c0-128">La commande suivante crée un assembly de stratégie `policy.1.0.myAssembly` d’éditeur appelé à partir d’un fichier de stratégie d’éditeur appelé `pub.config` , attribue un nom fort à l’assembly à l’aide de la paire de clés dans le `sgKey.snk` fichier et spécifie que l’assembly cible l’architecture de processeur x86.</span><span class="sxs-lookup"><span data-stu-id="b00c0-128">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="b00c0-129">L’assembly de stratégie d’éditeur doit correspondre à l’architecture de processeur de l’assembly auquel il s’applique.</span><span class="sxs-lookup"><span data-stu-id="b00c0-129">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="b00c0-130">Ainsi, si votre assembly a la <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> valeur <xref:System.Reflection.ProcessorArchitecture.MSIL> , l’assembly de stratégie d’éditeur de cet assembly doit être créé avec `/platform:anycpu` .</span><span class="sxs-lookup"><span data-stu-id="b00c0-130">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="b00c0-131">Vous devez fournir un assembly de stratégie d’éditeur distinct pour chaque assembly spécifique au processeur.</span><span class="sxs-lookup"><span data-stu-id="b00c0-131">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="b00c0-132">Une conséquence de cette règle est que pour modifier l’architecture de processeur d’un assembly, vous devez modifier le composant principal ou mineur du numéro de version, afin de pouvoir fournir un nouvel assembly de stratégie d’éditeur avec l’architecture de processeur correcte.</span><span class="sxs-lookup"><span data-stu-id="b00c0-132">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="b00c0-133">L’ancien assembly de stratégie d’éditeur ne peut pas traiter votre assembly une fois que votre assembly a une architecture de processeur différente.</span><span class="sxs-lookup"><span data-stu-id="b00c0-133">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="b00c0-134">Une autre conséquence est que l’éditeur de liens version 2,0 ne peut pas être utilisé pour créer un assembly de stratégie d’éditeur pour un assembly compilé à l’aide de versions antérieures du .NET Framework, car il spécifie toujours l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="b00c0-134">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="b00c0-135">Ajout de l’assembly de stratégie d’éditeur au global assembly cache</span><span class="sxs-lookup"><span data-stu-id="b00c0-135">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="b00c0-136">Utilisez l' [outil global assembly cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour ajouter l’assembly de stratégie d’éditeur au global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="b00c0-136">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="b00c0-137">Pour ajouter l’assembly de stratégie d’éditeur au Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="b00c0-137">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="b00c0-138">Entrez la commande suivante à l'invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="b00c0-138">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="b00c0-139">La commande suivante ajoute `policy.1.0.myAssembly.dll` à la global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="b00c0-139">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="b00c0-140">L’assembly de stratégie d’éditeur ne peut pas être ajouté au Global Assembly Cache, sauf si le fichier de stratégie d’éditeur d’origine spécifié dans l' `/link` argument se trouve dans le même répertoire que l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b00c0-140">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="b00c0-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b00c0-141">See also</span></span>

- [<span data-ttu-id="b00c0-142">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="b00c0-142">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="b00c0-143">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="b00c0-143">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="b00c0-144">Configuration des applications à l'aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b00c0-144">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="b00c0-145">Schéma des paramètres d’exécution</span><span class="sxs-lookup"><span data-stu-id="b00c0-145">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="b00c0-146">Schéma des fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="b00c0-146">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="b00c0-147">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="b00c0-147">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
