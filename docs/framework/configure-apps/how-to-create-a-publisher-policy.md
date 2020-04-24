---
title: "Comment : créer une stratégie d'éditeur"
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646053"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="1446e-102">Comment : créer une stratégie d'éditeur</span><span class="sxs-lookup"><span data-stu-id="1446e-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="1446e-103">Les fournisseurs d’assemblages peuvent indiquer que les applications doivent utiliser une version plus récente d’un assemblage en incluant un fichier de politique d’éditeur avec l’assemblage mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="1446e-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="1446e-104">Le fichier de politique de l’éditeur spécifie les paramètres de réorientation d’assemblage et de base de code, et utilise le même format qu’un fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="1446e-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="1446e-105">Le fichier de politique de l’éditeur est compilé dans une assemblée et placé dans le cache d’assemblage global.</span><span class="sxs-lookup"><span data-stu-id="1446e-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="1446e-106">La création d’une politique d’éditeur comporte trois étapes :</span><span class="sxs-lookup"><span data-stu-id="1446e-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="1446e-107">Créez un fichier de politique d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="1446e-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="1446e-108">Créer une assemblée des politiques de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="1446e-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="1446e-109">Ajoutez l’assemblage de la politique de l’éditeur au cache d’assemblage global.</span><span class="sxs-lookup"><span data-stu-id="1446e-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="1446e-110">Le schéma de la politique de l’éditeur est décrit dans [Redirecting Assembly Versions](redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="1446e-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="1446e-111">L’exemple suivant montre un fichier de `myAssembly` politique d’éditeur qui redirige une version d’une autre.</span><span class="sxs-lookup"><span data-stu-id="1446e-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

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

<span data-ttu-id="1446e-112">Pour savoir comment spécifier une base de code, voir [spécifier l’emplacement d’une Assemblée](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="1446e-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="1446e-113">Création de l’Assemblée des politiques des éditeurs</span><span class="sxs-lookup"><span data-stu-id="1446e-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="1446e-114">Utilisez le [Linker de l’Assemblée (Al.exe)](../tools/al-exe-assembly-linker.md) pour créer l’assemblée des politiques de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="1446e-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="1446e-115">Créer une assemblée des politiques de l’éditeur</span><span class="sxs-lookup"><span data-stu-id="1446e-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="1446e-116">Entrez la commande suivante à l'invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="1446e-116">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="1446e-117">Dans cette commande :</span><span class="sxs-lookup"><span data-stu-id="1446e-117">In this command:</span></span>

- <span data-ttu-id="1446e-118">L’argument `publisherPolicyFile` est le nom du dossier de politique de l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="1446e-118">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="1446e-119">L’argument `publisherPolicyAssemblyFile` est le nom de l’assemblée des politiques de l’éditeur qui résulte de cette commande.</span><span class="sxs-lookup"><span data-stu-id="1446e-119">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="1446e-120">Le nom du fichier d’assemblage doit suivre le format :</span><span class="sxs-lookup"><span data-stu-id="1446e-120">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="1446e-121">'policy.majorNumber.minorNumber.mainAssemblyName.dll'</span><span class="sxs-lookup"><span data-stu-id="1446e-121">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="1446e-122">L’argument `keyPairFile` est le nom du fichier contenant la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="1446e-122">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="1446e-123">Vous devez signer l’assemblage et l’assemblage des politiques de l’éditeur avec la même paire clé.</span><span class="sxs-lookup"><span data-stu-id="1446e-123">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="1446e-124">L’argument `processorArchitecture` identifie la plate-forme ciblée par un assemblage spécifique au processeur.</span><span class="sxs-lookup"><span data-stu-id="1446e-124">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="1446e-125">La possibilité de cibler une architecture de processeur spécifique est disponible à partir de .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="1446e-125">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="1446e-126">La possibilité de cibler une architecture de processeur spécifique est disponible à partir de .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="1446e-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="1446e-127">La commande suivante crée un `policy.1.0.myAssembly` assemblage de politique `pub.config`d’éditeur appelé à partir d’un `sgKey.snk` fichier de politique d’éditeur appelé , attribue un nom fort à l’assemblage en utilisant la paire de clés dans le fichier, et précise que l’assemblage cible l’architecture du processeur x86.</span><span class="sxs-lookup"><span data-stu-id="1446e-127">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="1446e-128">L’assemblage de la politique de l’éditeur doit correspondre à l’architecture de processeur de l’assemblage à laquelle il s’applique.</span><span class="sxs-lookup"><span data-stu-id="1446e-128">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="1446e-129">Ainsi, si votre <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> assemblée <xref:System.Reflection.ProcessorArchitecture.MSIL>a une valeur de , l’assemblage de la politique de l’éditeur pour cette assemblée doit être créé avec `/platform:anycpu`.</span><span class="sxs-lookup"><span data-stu-id="1446e-129">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="1446e-130">Vous devez fournir un assemblage distinct de la politique de l’éditeur pour chaque assemblage spécifique au processeur.</span><span class="sxs-lookup"><span data-stu-id="1446e-130">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="1446e-131">Une conséquence de cette règle est que pour changer l’architecture du processeur pour un assemblage, vous devez modifier la composante majeure ou mineure du numéro de version, de sorte que vous pouvez fournir un nouvel assemblage de politique d’éditeur avec l’architecture de processeur correcte.</span><span class="sxs-lookup"><span data-stu-id="1446e-131">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="1446e-132">L’ancien assemblage de la politique de l’éditeur ne peut pas servir votre assemblage une fois que votre assemblage a une architecture de processeur différente.</span><span class="sxs-lookup"><span data-stu-id="1446e-132">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="1446e-133">Une autre conséquence est que la version 2.0 linker ne peut pas être utilisé pour créer un assemblage de politique d’éditeur pour une assemblée compilée en utilisant des versions antérieures du cadre .NET, car il spécifie toujours l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="1446e-133">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="1446e-134">Ajout de l’Assemblée des politiques des éditeurs au Cache de l’Assemblée mondiale</span><span class="sxs-lookup"><span data-stu-id="1446e-134">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="1446e-135">Utilisez [l’outil Global Assembly Cache (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) pour ajouter l’assemblage des politiques de l’éditeur au cache d’assemblage mondial.</span><span class="sxs-lookup"><span data-stu-id="1446e-135">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="1446e-136">Pour ajouter l’assemblage de la politique de l’éditeur au cache d’assemblage mondial</span><span class="sxs-lookup"><span data-stu-id="1446e-136">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="1446e-137">Entrez la commande suivante à l'invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="1446e-137">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="1446e-138">La commande `policy.1.0.myAssembly.dll` suivante s’ajoute à la cache d’assemblage global.</span><span class="sxs-lookup"><span data-stu-id="1446e-138">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="1446e-139">L’assemblée des politiques de l’éditeur ne peut être ajoutée `/link` au cache d’assemblage global à moins que le dossier de politique originale de l’éditeur spécifié dans l’argumentation ne soit situé dans le même répertoire que l’assemblée.</span><span class="sxs-lookup"><span data-stu-id="1446e-139">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="1446e-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1446e-140">See also</span></span>

- [<span data-ttu-id="1446e-141">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="1446e-141">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="1446e-142">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="1446e-142">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1446e-143">Configuration des applications à l'aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="1446e-143">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="1446e-144">Paramètres de durée d’exécution Schema</span><span class="sxs-lookup"><span data-stu-id="1446e-144">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="1446e-145">Configuration Fichier Schema</span><span class="sxs-lookup"><span data-stu-id="1446e-145">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="1446e-146">Redirection des versions d'assemblys</span><span class="sxs-lookup"><span data-stu-id="1446e-146">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
