---
title: commande dotnet NuGet Add source
description: La commande dotnet NuGet Add source ajoute une nouvelle source de package à vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: b847d987de2d88cb3452d32d1bc84232a1e20b6e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537971"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="e65e7-103">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="e65e7-103">dotnet nuget add source</span></span>

<span data-ttu-id="e65e7-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.200 .net Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="e65e7-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e65e7-105">Name</span><span class="sxs-lookup"><span data-stu-id="e65e7-105">Name</span></span>

<span data-ttu-id="e65e7-106">`dotnet nuget add source` -Ajouter une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="e65e7-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e65e7-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="e65e7-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a><span data-ttu-id="e65e7-108">Description</span><span class="sxs-lookup"><span data-stu-id="e65e7-108">Description</span></span>

<span data-ttu-id="e65e7-109">La `dotnet nuget add source` commande ajoute une nouvelle source de package à vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="e65e7-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="e65e7-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="e65e7-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="e65e7-111">Chemin d’accès à la source du package.</span><span class="sxs-lookup"><span data-stu-id="e65e7-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="e65e7-112">Options</span><span class="sxs-lookup"><span data-stu-id="e65e7-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="e65e7-113">Fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="e65e7-113">The NuGet configuration file.</span></span> <span data-ttu-id="e65e7-114">Si ce paramètre est spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="e65e7-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="e65e7-115">S’il n’est pas spécifié, la hiérarchie des fichiers de configuration du répertoire actif sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="e65e7-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="e65e7-116">Pour plus d’informations, consultez [configurations NuGet courantes](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="e65e7-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name <SOURCE_NAME>`**

  <span data-ttu-id="e65e7-117">Nom de la source.</span><span class="sxs-lookup"><span data-stu-id="e65e7-117">Name of the source.</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="e65e7-118">Mot de passe à utiliser lors de la connexion à une source authentifiée.</span><span class="sxs-lookup"><span data-stu-id="e65e7-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="e65e7-119">Active le stockage des informations d’identification de la source du package portable en désactivant le chiffrement du mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e65e7-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="e65e7-120">Nom d’utilisateur à utiliser lors de la connexion à une source authentifiée.</span><span class="sxs-lookup"><span data-stu-id="e65e7-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="e65e7-121">Liste séparée par des virgules des types d’authentification valides pour cette source.</span><span class="sxs-lookup"><span data-stu-id="e65e7-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="e65e7-122">Définissez cette valeur sur `basic` si le serveur publie NTLM ou Negotiate et que vos informations d’identification doivent être envoyées à l’aide du mécanisme de base, par exemple lors de l’utilisation d’un Pat avec un Azure DevOps Server local.</span><span class="sxs-lookup"><span data-stu-id="e65e7-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="e65e7-123">Les autres valeurs valides incluent `negotiate` , `kerberos` , `ntlm` et `digest` , mais ces valeurs ne sont pas susceptibles d’être utiles.</span><span class="sxs-lookup"><span data-stu-id="e65e7-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="e65e7-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="e65e7-124">Examples</span></span>

- <span data-ttu-id="e65e7-125">Ajouter `nuget.org` en tant que source :</span><span class="sxs-lookup"><span data-stu-id="e65e7-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="e65e7-126">Ajouter `c:\packages` en tant que source locale :</span><span class="sxs-lookup"><span data-stu-id="e65e7-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="e65e7-127">Ajoutez une source qui requiert une authentification :</span><span class="sxs-lookup"><span data-stu-id="e65e7-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="e65e7-128">Ajoutez une source qui nécessite une authentification (puis accédez à installer le fournisseur d’informations d’identification) :</span><span class="sxs-lookup"><span data-stu-id="e65e7-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="e65e7-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e65e7-129">See also</span></span>

- [<span data-ttu-id="e65e7-130">Sections sources du package dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="e65e7-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="e65e7-131">sources, commande (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="e65e7-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
