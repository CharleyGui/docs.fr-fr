---
title: Commande dotnet store
description: La commande « dotnet store » stocke les assemblys spécifiés dans le magasin de packages de runtime.
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503582"
---
# <a name="dotnet-store"></a><span data-ttu-id="6e0d4-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="6e0d4-103">dotnet store</span></span>

<span data-ttu-id="6e0d4-104">**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6e0d4-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6e0d4-105">Nom</span><span class="sxs-lookup"><span data-stu-id="6e0d4-105">Name</span></span>

<span data-ttu-id="6e0d4-106">`dotnet store` : stocke les assemblys spécifiés dans le [magasin de packages de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="6e0d4-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="6e0d4-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="6e0d4-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a><span data-ttu-id="6e0d4-108">Description</span><span class="sxs-lookup"><span data-stu-id="6e0d4-108">Description</span></span>

<span data-ttu-id="6e0d4-109">`dotnet store` stocke les assemblys spécifiés dans le [magasin de packages de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="6e0d4-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="6e0d4-110">Par défaut, les assemblys sont optimisés pour les runtime et framework cibles.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="6e0d4-111">Pour plus d’informations, consultez la rubrique [Magasin de packages de runtime](../deploying/runtime-store.md).</span><span class="sxs-lookup"><span data-stu-id="6e0d4-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="6e0d4-112">Options obligatoires</span><span class="sxs-lookup"><span data-stu-id="6e0d4-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6e0d4-113">Spécifie le [framework cible](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="6e0d4-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="6e0d4-114">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="6e0d4-115">Le *fichier manifeste du magasin de packages* est un fichier XML qui contient la liste des packages à stocker.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="6e0d4-116">Le format du fichier manifeste est compatible avec celui du projet de style SDK.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="6e0d4-117">Ainsi, vous pouvez utiliser un fichier projet qui référence les packages souhaités avec l’option `-m|--manifest` pour stocker des assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="6e0d4-118">Pour spécifier plusieurs fichiers manifeste, répétez l’option et le chemin pour chaque fichier.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="6e0d4-119">Par exemple : `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="6e0d4-120">[L’identifiant de temps d’exécution](../rid-catalog.md) à cibler.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="6e0d4-121">Options facultatives</span><span class="sxs-lookup"><span data-stu-id="6e0d4-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="6e0d4-122">Spécifie la version du SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-122">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="6e0d4-123">Cette option vous permet de sélectionner une version de framework spécifique en plus du framework indiqué par l’option `-f|--framework`.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6e0d4-124">Affiche des informations d’aide.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="6e0d4-125">Spécifie le chemin du magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="6e0d4-126">Si ce chemin n’est pas spécifié, le sous-répertoire *store* du répertoire d’installation de .NET Core du profil de l’utilisateur est choisi par défaut.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="6e0d4-127">Ignore la phase d’optimisation.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="6e0d4-128">Ignore la génération de symboles.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-128">Skips symbol generation.</span></span> <span data-ttu-id="6e0d4-129">Vous pouvez uniquement générer des symboles sur Windows et Linux.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="6e0d4-130">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6e0d4-131">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="6e0d4-132">Répertoire de travail utilisé par la commande.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-132">The working directory used by the command.</span></span> <span data-ttu-id="6e0d4-133">S’il n’est pas spécifié, il utilise le sous-répertoire *obj* du répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="6e0d4-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="6e0d4-134">Exemples</span><span class="sxs-lookup"><span data-stu-id="6e0d4-134">Examples</span></span>

- <span data-ttu-id="6e0d4-135">Stocker les packages spécifiés dans le fichier projet *packages.csproj* pour .NET Core 2.0.0 :</span><span class="sxs-lookup"><span data-stu-id="6e0d4-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="6e0d4-136">Stocker les packages spécifiés dans le fichier projet *packages.csproj* sans optimisation :</span><span class="sxs-lookup"><span data-stu-id="6e0d4-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="6e0d4-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e0d4-137">See also</span></span>

- [<span data-ttu-id="6e0d4-138">Magasin de packages de runtime</span><span class="sxs-lookup"><span data-stu-id="6e0d4-138">Runtime package store</span></span>](../deploying/runtime-store.md)
