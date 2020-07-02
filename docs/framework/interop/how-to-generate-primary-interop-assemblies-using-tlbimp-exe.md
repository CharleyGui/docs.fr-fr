---
title: 'Procédure : générer des assemblys PIA à l’aide de Tlbimp.exe'
description: Découvrez comment générer des assemblys PIA à l’aide de l’importateur de bibliothèques de types (Tlbimp.exe) fourni par le SDK Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
ms.openlocfilehash: 779b4863b6f1513f3566d4ab31660d88cda1039b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619128"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a><span data-ttu-id="26a95-103">Procédure : générer des assemblys PIA à l’aide de Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="26a95-103">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>

<span data-ttu-id="26a95-104">Il existe deux manières de générer un assembly PIA :</span><span class="sxs-lookup"><span data-stu-id="26a95-104">There are two ways to generate a primary interop assembly:</span></span>

- <span data-ttu-id="26a95-105">En utilisant l’outil [Tlbimp.exe (Importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md) fourni par le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="26a95-105">Using the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) provided by the Windows SDK.</span></span>

  <span data-ttu-id="26a95-106">La façon la plus simple de générer un assembly PIA est d’utiliser l’outil [Tlbimp.exe (importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="26a95-106">The most straightforward way to produce primary interop assemblies is to use the [Tlbimp.exe (Type Library Importer)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="26a95-107">Tlbimp.exe offre les protections suivantes :</span><span class="sxs-lookup"><span data-stu-id="26a95-107">Tlbimp.exe provides the following safeguards:</span></span>

  - <span data-ttu-id="26a95-108">Il vérifie les autres assemblys PIA inscrits avant de créer de nouveaux assemblys PIA pour les références de bibliothèque de types imbriquées.</span><span class="sxs-lookup"><span data-stu-id="26a95-108">Checks for other registered primary interop assemblies before creating new interop assemblies for any nested type library references.</span></span>

  - <span data-ttu-id="26a95-109">Il n'émet pas d'assembly PIA si vous ne spécifiez pas le conteneur ou le nom de fichier pour attribuer un nom fort à l'assembly PIA.</span><span class="sxs-lookup"><span data-stu-id="26a95-109">Fails to emit the primary interop assembly if you do not specify either the container or file name to give the primary interop assembly a strong name.</span></span>

  - <span data-ttu-id="26a95-110">Il n'émet pas d'assembly PIA si vous omettez les références aux assemblys dépendants.</span><span class="sxs-lookup"><span data-stu-id="26a95-110">Fails to emit a primary interop assembly if you omit references to dependent assemblies.</span></span>

  - <span data-ttu-id="26a95-111">Il n'émet pas d'assembly PIA si vous ajoutez des références à des assemblys dépendants qui ne sont pas des assemblys PIA.</span><span class="sxs-lookup"><span data-stu-id="26a95-111">Fails to emit a primary interop assembly if you add references to dependent assemblies that are not primary interop assemblies.</span></span>

- <span data-ttu-id="26a95-112">Par la création manuelle d'assemblys PIA dans le code source avec un langage conforme à la spécification CLS, tel que le C#.</span><span class="sxs-lookup"><span data-stu-id="26a95-112">Creating primary interop assemblies manually in source code by using a language that is compliant with the Common Language Specification (CLS), such as C#.</span></span> <span data-ttu-id="26a95-113">Cette approche est utile quand aucune bibliothèque de types n'est disponible.</span><span class="sxs-lookup"><span data-stu-id="26a95-113">This approach is useful when a type library is unavailable.</span></span>

<span data-ttu-id="26a95-114">Pour signer un assembly avec un nom fort, vous devez avoir une paire de clés de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="26a95-114">You must have a cryptographic key pair to sign the assembly with a strong name.</span></span> <span data-ttu-id="26a95-115">Pour plus d’informations, consultez [Création d’une paire de clés](../../standard/assembly/create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="26a95-115">For details, see [Creating A Key Pair](../../standard/assembly/create-public-private-key-pair.md).</span></span>

### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a><span data-ttu-id="26a95-116">Pour générer des assemblys PIA à l'aide de Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="26a95-116">To generate a primary interop assembly using Tlbimp.exe</span></span>

1. <span data-ttu-id="26a95-117">À l’invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="26a95-117">At the command prompt, type:</span></span>

    <span data-ttu-id="26a95-118">**tlbimp** *fichiertlb*  **/primary /keyfile:** *nomfichier* **/out:** *nomassembly*</span><span class="sxs-lookup"><span data-stu-id="26a95-118">**tlbimp** *tlbfile*  **/primary /keyfile:** *filename* **/out:** *assemblyname*</span></span>

    <span data-ttu-id="26a95-119">Dans cette commande, *fichiertlb* correspond au fichier contenant la bibliothèque de types COM, *nomfichier* au nom du conteneur ou du fichier qui contient la paire de clés, et *nomassembly* au nom de l’assembly à signer avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="26a95-119">In this command, *tlbfile* is the file containing the COM type library, *filename* is the name of the container or file that contains the key pair, and *assemblyname* is the name of the assembly to sign with a strong name.</span></span>

<span data-ttu-id="26a95-120">Les assemblys PIA peuvent référencer uniquement d'autres assemblys PIA.</span><span class="sxs-lookup"><span data-stu-id="26a95-120">Primary interop assemblies can reference only other primary interop assemblies.</span></span> <span data-ttu-id="26a95-121">Si votre assembly référence des types d'une bibliothèque de types COM tiers, vous devrez obtenir un assembly PIA auprès de l'éditeur avant de pouvoir générer votre assembly PIA.</span><span class="sxs-lookup"><span data-stu-id="26a95-121">If your assembly references types from a third-party COM type library, you must obtain a primary interop assembly from the publisher before you can generate your primary interop assembly.</span></span> <span data-ttu-id="26a95-122">Si vous êtes l'éditeur, vous devrez générer un assembly PIA pour la bibliothèque de types dépendante avant de générer l'assembly PIA de référence.</span><span class="sxs-lookup"><span data-stu-id="26a95-122">If you are the publisher, you must generate a primary interop assembly for the dependent type library before generating the referencing primary interop assembly.</span></span>

<span data-ttu-id="26a95-123">Un assembly PIA avec un numéro de version différent de celui de la bibliothèque de types d'origine ne pourra pas être détecté s'il est installé dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="26a95-123">A dependent primary interop assembly with a version number that differs from that of the original type library is not discoverable when installed in the current directory.</span></span> <span data-ttu-id="26a95-124">Vous devez inscrire l’assembly PIA dépendant dans le Registre Windows ou utiliser l’option **/reference** pour garantir que Tlbimp.exe trouve la DLL dépendante.</span><span class="sxs-lookup"><span data-stu-id="26a95-124">You must either register the dependent primary interop assembly in the Windows registry or use the **/reference** option to be sure that Tlbimp.exe finds the dependent DLL.</span></span>

<span data-ttu-id="26a95-125">Vous pouvez également encapsuler plusieurs versions d'une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="26a95-125">You can also wrap multiple versions of a type library.</span></span> <span data-ttu-id="26a95-126">Pour obtenir des instructions, consultez [Guide pratique pour encapsuler plusieurs versions de bibliothèques de types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="26a95-126">For instructions, see [How to: Wrap Multiple Versions of Type Libraries](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="26a95-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="26a95-127">Example</span></span>

<span data-ttu-id="26a95-128">Dans l'exemple suivant, la bibliothèque de types COM `LibUtil.tlb` est importée et l'assembly `LibUtil.dll` est signé avec un nom fort à l'aide du fichier de clé `CompanyA.snk`.</span><span class="sxs-lookup"><span data-stu-id="26a95-128">The following example imports the COM type library `LibUtil.tlb` and signs the assembly `LibUtil.dll` with a strong name using the key file `CompanyA.snk`.</span></span> <span data-ttu-id="26a95-129">En ne spécifiant pas de nom d'espace de noms, cet exemple génère l'espace de noms par défaut `LibUtil`.</span><span class="sxs-lookup"><span data-stu-id="26a95-129">By omitting a specific namespace name, this example produces the default namespace, `LibUtil`.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll
```

<span data-ttu-id="26a95-130">Pour un nom plus descriptif (qui utilise la règle de nommage *Nom_fournisseur*.*Nom_bibliothèque*), l’exemple suivant remplace le nom de fichier d’assembly et le nom d’espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="26a95-130">For a more descriptive name (using the *VendorName*.*LibraryName* naming guideline), the following example overrides the default assembly file name and namespace name.</span></span>

```console
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll
```

<span data-ttu-id="26a95-131">L'exemple suivant importe `MyLib.tlb`, qui référence `CompanyA.LibUtil.dll`, et signe l'assembly `CompanyB.MyLib.dll` avec un nom fort à l'aide du fichier de clé `CompanyB.snk`.</span><span class="sxs-lookup"><span data-stu-id="26a95-131">The following example imports `MyLib.tlb`, which references `CompanyA.LibUtil.dll`, and signs the assembly `CompanyB.MyLib.dll` with a strong name using the key file `CompanyB.snk`.</span></span> <span data-ttu-id="26a95-132">L'espace de noms `CompanyB.MyLib` remplace le nom d'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="26a95-132">The namespace, `CompanyB.MyLib`, overrides the default namespace name.</span></span>

```console
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll
```

## <a name="see-also"></a><span data-ttu-id="26a95-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26a95-133">See also</span></span>

- [<span data-ttu-id="26a95-134">Procédure : enregistrer des assemblys PIA</span><span class="sxs-lookup"><span data-stu-id="26a95-134">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)
