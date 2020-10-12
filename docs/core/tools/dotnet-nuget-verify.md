---
title: commande dotnet NuGet Verify
description: La commande dotnet NuGet Verify vérifie un package signé.
author: kartheekp-ms
ms.date: 10/08/2020
ms.openlocfilehash: 6cb368e2b6c203f3774b4450c0831c5d6b2dc0e8
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957150"
---
# <a name="dotnet-nuget-verify"></a><span data-ttu-id="0c727-103">vérification de dotnet NuGet</span><span class="sxs-lookup"><span data-stu-id="0c727-103">dotnet nuget verify</span></span>

<span data-ttu-id="0c727-104">**Cet article s’applique à :** ✔️ le kit de développement logiciel (SDK) .net 5.0.100-RC. 2. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="0c727-104">**This article applies to:** ✔️ .NET 5.0.100-rc.2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0c727-105">Nom</span><span class="sxs-lookup"><span data-stu-id="0c727-105">Name</span></span>

<span data-ttu-id="0c727-106">`dotnet nuget verify` -Vérifie un package NuGet signé.</span><span class="sxs-lookup"><span data-stu-id="0c727-106">`dotnet nuget verify` - Verifies a signed NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0c727-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="0c727-107">Synopsis</span></span>

```dotnetcli
dotnet nuget verify [<package-path(s)>]
    [--all]
    [--certificate-fingerprint <FINGERPRINT>]
    [-v|--verbosity <LEVEL>]

dotnet nuget verify -h|--help
```

## <a name="description"></a><span data-ttu-id="0c727-108">Description</span><span class="sxs-lookup"><span data-stu-id="0c727-108">Description</span></span>

<span data-ttu-id="0c727-109">La `dotnet nuget verify` commande vérifie un package NuGet signé.</span><span class="sxs-lookup"><span data-stu-id="0c727-109">The `dotnet nuget verify` command verifies a signed NuGet package.</span></span>

## <a name="arguments"></a><span data-ttu-id="0c727-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="0c727-110">Arguments</span></span>

- **`package-path(s)`**

  <span data-ttu-id="0c727-111">Spécifie le chemin d’accès au (x) package (s) à vérifier.</span><span class="sxs-lookup"><span data-stu-id="0c727-111">Specifies the file path to the package(s) to be verified.</span></span> <span data-ttu-id="0c727-112">Plusieurs arguments de position peuvent être passés pour vérifier plusieurs packages.</span><span class="sxs-lookup"><span data-stu-id="0c727-112">Multiple position arguments can be passed in to verify multiple packages.</span></span>

## <a name="options"></a><span data-ttu-id="0c727-113">Options</span><span class="sxs-lookup"><span data-stu-id="0c727-113">Options</span></span>

- **`--all`**

  <span data-ttu-id="0c727-114">Spécifie que toutes les vérifications possibles doivent être effectuées sur le ou les packages.</span><span class="sxs-lookup"><span data-stu-id="0c727-114">Specifies that all verifications possible should be performed on the package(s).</span></span> <span data-ttu-id="0c727-115">Par défaut, seuls `signatures` sont vérifiés.</span><span class="sxs-lookup"><span data-stu-id="0c727-115">By default, only `signatures` are verified.</span></span>

> [!NOTE]
> <span data-ttu-id="0c727-116">Cette commande ne prend actuellement en charge que la `signature` vérification.</span><span class="sxs-lookup"><span data-stu-id="0c727-116">This command currently supports only `signature` verification.</span></span>

- **`--certificate-fingerprint <FINGERPRINT>`**

  <span data-ttu-id="0c727-117">Vérifiez que le certificat de signataire correspond à l’une des `SHA256` empreintes spécifiées.</span><span class="sxs-lookup"><span data-stu-id="0c727-117">Verify that the signer certificate matches with one of the specified `SHA256` fingerprints.</span></span> <span data-ttu-id="0c727-118">Cette option peut être fournie plusieurs fois pour fournir plusieurs empreintes digitales.</span><span class="sxs-lookup"><span data-stu-id="0c727-118">This option can be supplied multiple times to provide multiple fingerprints.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0c727-119">Définit le niveau de détail MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0c727-119">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="0c727-120">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0c727-120">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0c727-121">Par défaut, il s’agit de `normal`.</span><span class="sxs-lookup"><span data-stu-id="0c727-121">The default is `normal`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="0c727-122">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="0c727-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="0c727-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="0c727-123">Examples</span></span>

- <span data-ttu-id="0c727-124">Vérifiez *foo. nupkg*:</span><span class="sxs-lookup"><span data-stu-id="0c727-124">Verify *foo.nupkg*:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg
  ```

- <span data-ttu-id="0c727-125">Vérifiez que plusieurs packages NuGet- *foo. nupkg* et *tous les fichiers. nupkg dans le répertoire spécifié*:</span><span class="sxs-lookup"><span data-stu-id="0c727-125">Verify multiple NuGet packages - *foo.nupkg* and *all .nupkg files in the directory specified*:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg c:\mydir\*.nupkg
  ```

- <span data-ttu-id="0c727-126">Vérifiez que la signature de *foo. nupkg* correspond à l’empreinte de certificat spécifiée :</span><span class="sxs-lookup"><span data-stu-id="0c727-126">Verify *foo.nupkg* signature matches with the specified certificate fingerprint:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039
  ```

- <span data-ttu-id="0c727-127">Vérifiez que la signature de *foo. nupkg* correspond à l’une des empreintes de certificat spécifiées :</span><span class="sxs-lookup"><span data-stu-id="0c727-127">Verify *foo.nupkg* signature matches with one of the specified certificate fingerprints:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 --certificate-fingerprint EC10992GG5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E027
  ```
