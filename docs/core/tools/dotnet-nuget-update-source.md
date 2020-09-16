---
title: commande de source de mise à jour NuGet de dotnet
description: La commande dotnet NuGet Update source met à jour une source existante dans vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: a8658c78c095ad4b9272d97200e1d6466cbe658b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537852"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="a5504-103">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="a5504-103">dotnet nuget update source</span></span>

<span data-ttu-id="a5504-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.200 .net Core et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="a5504-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a5504-105">Name</span><span class="sxs-lookup"><span data-stu-id="a5504-105">Name</span></span>

<span data-ttu-id="a5504-106">`dotnet nuget update source` -Mettez à jour une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5504-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a5504-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="a5504-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a><span data-ttu-id="a5504-108">Description</span><span class="sxs-lookup"><span data-stu-id="a5504-108">Description</span></span>

<span data-ttu-id="a5504-109">La `dotnet nuget update source` commande met à jour une source existante dans vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5504-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="a5504-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="a5504-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="a5504-111">Nom de la source.</span><span class="sxs-lookup"><span data-stu-id="a5504-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="a5504-112">Options</span><span class="sxs-lookup"><span data-stu-id="a5504-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="a5504-113">Fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="a5504-113">The NuGet configuration file.</span></span> <span data-ttu-id="a5504-114">Si ce paramètre est spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="a5504-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="a5504-115">S’il n’est pas spécifié, la hiérarchie des fichiers de configuration du répertoire actif sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="a5504-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="a5504-116">Pour plus d’informations, consultez [configurations NuGet courantes](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="a5504-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="a5504-117">Mot de passe à utiliser lors de la connexion à une source authentifiée.</span><span class="sxs-lookup"><span data-stu-id="a5504-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="a5504-118">Chemin d’accès à la source du package.</span><span class="sxs-lookup"><span data-stu-id="a5504-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="a5504-119">Active le stockage des informations d’identification de la source du package portable en désactivant le chiffrement du mot de passe.</span><span class="sxs-lookup"><span data-stu-id="a5504-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="a5504-120">Nom d’utilisateur à utiliser lors de la connexion à une source authentifiée.</span><span class="sxs-lookup"><span data-stu-id="a5504-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="a5504-121">Liste séparée par des virgules des types d’authentification valides pour cette source.</span><span class="sxs-lookup"><span data-stu-id="a5504-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="a5504-122">Définissez cette valeur sur `basic` si le serveur publie NTLM ou Negotiate et que vos informations d’identification doivent être envoyées à l’aide du mécanisme de base, par exemple lors de l’utilisation d’un Pat avec un Azure DevOps Server local.</span><span class="sxs-lookup"><span data-stu-id="a5504-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="a5504-123">Les autres valeurs valides incluent `negotiate` , `kerberos` , `ntlm` et `digest` , mais ces valeurs ne sont pas susceptibles d’être utiles.</span><span class="sxs-lookup"><span data-stu-id="a5504-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="a5504-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="a5504-124">Examples</span></span>

- <span data-ttu-id="a5504-125">Mettez à jour une source avec le nom `mySource` :</span><span class="sxs-lookup"><span data-stu-id="a5504-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="a5504-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5504-126">See also</span></span>

- [<span data-ttu-id="a5504-127">Sections sources du package dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="a5504-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="a5504-128">sources, commande (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="a5504-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
