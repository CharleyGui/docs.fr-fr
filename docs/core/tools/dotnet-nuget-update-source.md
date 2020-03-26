---
title: dotnet nuget mise à jour de la commande source
description: La commande source de mise à jour de nuget dotnet met à jour une source existante dans vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 38335e07f91850756c7671413e1193c2578e7e7e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148546"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="44593-103">source de mise à jour de nuget dotnet</span><span class="sxs-lookup"><span data-stu-id="44593-103">dotnet nuget update source</span></span>

<span data-ttu-id="44593-104">**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="44593-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="44593-105">Nom</span><span class="sxs-lookup"><span data-stu-id="44593-105">Name</span></span>

<span data-ttu-id="44593-106">`dotnet nuget update source`- Mettre à jour une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="44593-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="44593-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="44593-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget update source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="44593-108">Description</span><span class="sxs-lookup"><span data-stu-id="44593-108">Description</span></span>

<span data-ttu-id="44593-109">La `dotnet nuget update source` commande met à jour une source existante dans vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="44593-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="44593-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="44593-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="44593-111">Nom de la source.</span><span class="sxs-lookup"><span data-stu-id="44593-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="44593-112">Options</span><span class="sxs-lookup"><span data-stu-id="44593-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="44593-113">Le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="44593-113">The NuGet configuration file.</span></span> <span data-ttu-id="44593-114">Si spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="44593-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="44593-115">S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="44593-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="44593-116">Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="44593-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password`**

  <span data-ttu-id="44593-117">Mot de passe à utiliser lors de la connexion à une source authentifiée.</span><span class="sxs-lookup"><span data-stu-id="44593-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source`**

  <span data-ttu-id="44593-118">Chemin vers la source du paquet.</span><span class="sxs-lookup"><span data-stu-id="44593-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="44593-119">Permet de stocker des informations d’identification portables de source de paquets en désactivant le chiffrement de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="44593-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username`**

  <span data-ttu-id="44593-120">Nom d’utilisateur à utiliser lors de la connexion à une source authentifiée.</span><span class="sxs-lookup"><span data-stu-id="44593-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types`**

  <span data-ttu-id="44593-121">Liste séparée par comma de types d’authentification valides pour cette source.</span><span class="sxs-lookup"><span data-stu-id="44593-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="44593-122">Définissez `basic` ceci à si le serveur annonce NTLM ou Négocier et vos informations d’identification doivent être envoyées à l’aide du mécanisme de base, par exemple lors de l’utilisation d’un PAT avec sur place Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="44593-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="44593-123">D’autres `negotiate`valeurs `kerberos` `ntlm`valides `digest`incluent, , , et , mais ces valeurs sont peu susceptibles d’être utiles.</span><span class="sxs-lookup"><span data-stu-id="44593-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="44593-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="44593-124">Examples</span></span>

- <span data-ttu-id="44593-125">Mettre à jour `mySource`une source avec le nom de :</span><span class="sxs-lookup"><span data-stu-id="44593-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="44593-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44593-126">See also</span></span>

- [<span data-ttu-id="44593-127">Sections source de paquet dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="44593-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="44593-128">commande de sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="44593-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
