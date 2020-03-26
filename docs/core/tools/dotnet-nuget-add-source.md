---
title: dotnet nuget ajouter la commande source
description: La commande source d’ajout de nuget dotnet ajoute une nouvelle source de paquet à vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: c1e398699c7482a69b750cde718e6f9178b5c4bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148567"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="fc435-103">dotnet nuget ajouter source</span><span class="sxs-lookup"><span data-stu-id="fc435-103">dotnet nuget add source</span></span>

<span data-ttu-id="fc435-104">**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="fc435-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fc435-105">Nom</span><span class="sxs-lookup"><span data-stu-id="fc435-105">Name</span></span>

<span data-ttu-id="fc435-106">`dotnet nuget add source`- Ajouter une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="fc435-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fc435-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="fc435-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget add source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="fc435-108">Description</span><span class="sxs-lookup"><span data-stu-id="fc435-108">Description</span></span>

<span data-ttu-id="fc435-109">La `dotnet nuget add source` commande ajoute une nouvelle source de paquet à vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="fc435-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="fc435-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="fc435-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="fc435-111">Chemin vers la source du paquet.</span><span class="sxs-lookup"><span data-stu-id="fc435-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="fc435-112">Options</span><span class="sxs-lookup"><span data-stu-id="fc435-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="fc435-113">Le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="fc435-113">The NuGet configuration file.</span></span> <span data-ttu-id="fc435-114">Si spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="fc435-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="fc435-115">S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="fc435-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="fc435-116">Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="fc435-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name`**

  <span data-ttu-id="fc435-117">Nom de la source.</span><span class="sxs-lookup"><span data-stu-id="fc435-117">Name of the source.</span></span>

- **`-p|--password`**

  <span data-ttu-id="fc435-118">Mot de passe à utiliser lors de la connexion à une source authentifiée.</span><span class="sxs-lookup"><span data-stu-id="fc435-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="fc435-119">Permet de stocker des informations d’identification portables de source de paquets en désactivant le chiffrement de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="fc435-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username`**

  <span data-ttu-id="fc435-120">Nom d’utilisateur à utiliser lors de la connexion à une source authentifiée.</span><span class="sxs-lookup"><span data-stu-id="fc435-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types`**

  <span data-ttu-id="fc435-121">Liste séparée par comma de types d’authentification valides pour cette source.</span><span class="sxs-lookup"><span data-stu-id="fc435-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="fc435-122">Définissez `basic` ceci à si le serveur annonce NTLM ou Négocier et vos informations d’identification doivent être envoyées à l’aide du mécanisme de base, par exemple lors de l’utilisation d’un PAT avec sur place Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="fc435-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="fc435-123">D’autres `negotiate`valeurs `kerberos` `ntlm`valides `digest`incluent, , , et , mais ces valeurs sont peu susceptibles d’être utiles.</span><span class="sxs-lookup"><span data-stu-id="fc435-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="fc435-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="fc435-124">Examples</span></span>

- <span data-ttu-id="fc435-125">Ajouter `nuget.org` comme source:</span><span class="sxs-lookup"><span data-stu-id="fc435-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="fc435-126">Ajoutez `c:\packages` comme source locale :</span><span class="sxs-lookup"><span data-stu-id="fc435-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="fc435-127">Ajoutez une source qui a besoin d’authentification :</span><span class="sxs-lookup"><span data-stu-id="fc435-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="fc435-128">Ajouter une source qui a besoin d’authentification (puis allez installer le fournisseur d’informations d’identification):</span><span class="sxs-lookup"><span data-stu-id="fc435-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="fc435-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc435-129">See also</span></span>

- [<span data-ttu-id="fc435-130">Sections source de paquet dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="fc435-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="fc435-131">commande de sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="fc435-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
