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
# <a name="dotnet-nuget-add-source"></a>dotnet nuget ajouter source

**Cet article s’applique à:** ✔️ .NET Core 3.1.200 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet nuget add source`- Ajouter une source NuGet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget add source [-h|--help]
```

## <a name="description"></a>Description

La `dotnet nuget add source` commande ajoute une nouvelle source de paquet à vos fichiers de configuration NuGet.

## <a name="arguments"></a>Arguments

- **`PACKAGE_SOURCE_PATH`**

  Chemin vers la source du paquet.

## <a name="options"></a>Options

- **`--configfile`**

  Le fichier de configuration NuGet. Si spécifié, seuls les paramètres de ce fichier seront utilisés. S’il n’est pas précisé, la hiérarchie des fichiers de configuration de l’annuaire actuel sera utilisée. Pour plus d’informations, voir [Configurations NuGet communes](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`-n|--name`**

  Nom de la source.

- **`-p|--password`**

  Mot de passe à utiliser lors de la connexion à une source authentifiée.

- **`--store-password-in-clear-text`**

  Permet de stocker des informations d’identification portables de source de paquets en désactivant le chiffrement de mot de passe.

- **`-u|--username`**

  Nom d’utilisateur à utiliser lors de la connexion à une source authentifiée.

- **`--valid-authentication-types`**

  Liste séparée par comma de types d’authentification valides pour cette source. Définissez `basic` ceci à si le serveur annonce NTLM ou Négocier et vos informations d’identification doivent être envoyées à l’aide du mécanisme de base, par exemple lors de l’utilisation d’un PAT avec sur place Azure DevOps Server. D’autres `negotiate`valeurs `kerberos` `ntlm`valides `digest`incluent, , , et , mais ces valeurs sont peu susceptibles d’être utiles.

## <a name="examples"></a>Exemples

- Ajouter `nuget.org` comme source:

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- Ajoutez `c:\packages` comme source locale :

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- Ajoutez une source qui a besoin d’authentification :

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- Ajouter une source qui a besoin d’authentification (puis allez installer le fournisseur d’informations d’identification):

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>Voir aussi

- [Sections source de paquet dans les fichiers NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [commande de sources (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
