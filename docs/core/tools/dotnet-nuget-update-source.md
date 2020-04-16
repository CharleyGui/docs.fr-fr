---
title: dotnet nuget mise à jour de la commande source
description: La commande source de mise à jour de nuget dotnet met à jour une source existante dans vos fichiers de configuration NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 42b1aec95cdd57e53f966400f6692a3d0150c16c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463479"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="dfe5d-103">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="dfe5d-103">dotnet nuget update source</span></span>

<span data-ttu-id="dfe5d-104">**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="dfe5d-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="dfe5d-105">Nom</span><span class="sxs-lookup"><span data-stu-id="dfe5d-105">Name</span></span>

<span data-ttu-id="dfe5d-106">`dotnet nuget update source`- Mettre à jour une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dfe5d-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="dfe5d-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a><span data-ttu-id="dfe5d-108">Description</span><span class="sxs-lookup"><span data-stu-id="dfe5d-108">Description</span></span>

<span data-ttu-id="dfe5d-109">La `dotnet nuget update source` commande met à jour une source existante dans vos fichiers de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="dfe5d-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="dfe5d-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="dfe5d-111">Nom de la source.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="dfe5d-112">Options</span><span class="sxs-lookup"><span data-stu-id="dfe5d-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="dfe5d-113">Le fichier de configuration NuGet.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-113">The NuGet configuration file.</span></span> <span data-ttu-id="dfe5d-114">Si spécifié, seuls les paramètres de ce fichier seront utilisés.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="dfe5d-115">S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="dfe5d-116">Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="dfe5d-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="dfe5d-117">Mot de passe à utiliser lors de la connexion à une source authentifiée.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="dfe5d-118">Chemin vers la source du paquet.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="dfe5d-119">Permet de stocker des informations d’identification portables de source de paquets en désactivant le chiffrement de mot de passe.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="dfe5d-120">Nom d’utilisateur à utiliser lors de la connexion à une source authentifiée.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="dfe5d-121">Liste séparée par comma de types d’authentification valides pour cette source.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="dfe5d-122">Définissez `basic` ceci à si le serveur annonce NTLM ou Négocier et vos informations d’identification doivent être envoyées à l’aide du mécanisme de base, par exemple lors de l’utilisation d’un PAT avec sur place Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="dfe5d-123">D’autres `negotiate`valeurs `kerberos` `ntlm`valides `digest`incluent, , , et , mais ces valeurs sont peu susceptibles d’être utiles.</span><span class="sxs-lookup"><span data-stu-id="dfe5d-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="dfe5d-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="dfe5d-124">Examples</span></span>

- <span data-ttu-id="dfe5d-125">Mettre à jour `mySource`une source avec le nom de :</span><span class="sxs-lookup"><span data-stu-id="dfe5d-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="dfe5d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfe5d-126">See also</span></span>

- [<span data-ttu-id="dfe5d-127">Sections source de paquet dans les fichiers NuGet.config</span><span class="sxs-lookup"><span data-stu-id="dfe5d-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="dfe5d-128">commande de sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="dfe5d-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
