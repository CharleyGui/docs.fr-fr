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
# <a name="dotnet-nuget-update-source"></a>source de mise à jour de nuget dotnet

**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet nuget update source`- Mettre à jour une source NuGet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget update source <NAME> [--source] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget update source [-h|--help]
```

## <a name="description"></a>Description

La `dotnet nuget update source` commande met à jour une source existante dans vos fichiers de configuration NuGet.

## <a name="arguments"></a>Arguments

- **`NAME`**

  Nom de la source.

## <a name="options"></a>Options

- **`--configfile`**

  Le fichier de configuration NuGet. Si spécifié, seuls les paramètres de ce fichier seront utilisés. S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée. Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`-p|--password`**

  Mot de passe à utiliser lors de la connexion à une source authentifiée.

- **`-s|--source`**

  Chemin vers la source du paquet.

- **`--store-password-in-clear-text`**

  Permet de stocker des informations d’identification portables de source de paquets en désactivant le chiffrement de mot de passe.

- **`-u|--username`**

  Nom d’utilisateur à utiliser lors de la connexion à une source authentifiée.

- **`--valid-authentication-types`**

  Liste séparée par comma de types d’authentification valides pour cette source. Définissez `basic` ceci à si le serveur annonce NTLM ou Négocier et vos informations d’identification doivent être envoyées à l’aide du mécanisme de base, par exemple lors de l’utilisation d’un PAT avec sur place Azure DevOps Server. D’autres `negotiate`valeurs `kerberos` `ntlm`valides `digest`incluent, , , et , mais ces valeurs sont peu susceptibles d’être utiles.

## <a name="examples"></a>Exemples

- Mettre à jour `mySource`une source avec le nom de :

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>Voir aussi

- [Sections source de paquet dans les fichiers NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [commande de sources (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
