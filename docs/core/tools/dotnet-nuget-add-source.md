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
# <a name="dotnet-nuget-add-source"></a>dotnet nuget add source

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.200 .net Core et versions ultérieures

## <a name="name"></a>Name

`dotnet nuget add source` -Ajouter une source NuGet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a>Description

La `dotnet nuget add source` commande ajoute une nouvelle source de package à vos fichiers de configuration NuGet.

## <a name="arguments"></a>Arguments

- **`PACKAGE_SOURCE_PATH`**

  Chemin d’accès à la source du package.

## <a name="options"></a>Options

- **`--configfile <FILE>`**

  Fichier de configuration NuGet. Si ce paramètre est spécifié, seuls les paramètres de ce fichier seront utilisés. S’il n’est pas spécifié, la hiérarchie des fichiers de configuration du répertoire actif sera utilisée. Pour plus d’informations, consultez [configurations NuGet courantes](/nuget/consume-packages/configuring-nuget-behavior).

- **`-n|--name <SOURCE_NAME>`**

  Nom de la source.

- **`-p|--password <PASSWORD>`**

  Mot de passe à utiliser lors de la connexion à une source authentifiée.

- **`--store-password-in-clear-text`**

  Active le stockage des informations d’identification de la source du package portable en désactivant le chiffrement du mot de passe.

- **`-u|--username <USER>`**

  Nom d’utilisateur à utiliser lors de la connexion à une source authentifiée.

- **`--valid-authentication-types <TYPES>`**

  Liste séparée par des virgules des types d’authentification valides pour cette source. Définissez cette valeur sur `basic` si le serveur publie NTLM ou Negotiate et que vos informations d’identification doivent être envoyées à l’aide du mécanisme de base, par exemple lors de l’utilisation d’un Pat avec un Azure DevOps Server local. Les autres valeurs valides incluent `negotiate` , `kerberos` , `ntlm` et `digest` , mais ces valeurs ne sont pas susceptibles d’être utiles.

## <a name="examples"></a>Exemples

- Ajouter `nuget.org` en tant que source :

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- Ajouter `c:\packages` en tant que source locale :

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- Ajoutez une source qui requiert une authentification :

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- Ajoutez une source qui nécessite une authentification (puis accédez à installer le fournisseur d’informations d’identification) :

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>Voir aussi

- [Sections sources du package dans les fichiers NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, commande (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
