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
# <a name="dotnet-nuget-update-source"></a>dotnet nuget update source

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) 3.1.200 .net Core et versions ultérieures

## <a name="name"></a>Name

`dotnet nuget update source` -Mettez à jour une source NuGet.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a>Description

La `dotnet nuget update source` commande met à jour une source existante dans vos fichiers de configuration NuGet.

## <a name="arguments"></a>Arguments

- **`NAME`**

  Nom de la source.

## <a name="options"></a>Options

- **`--configfile <FILE>`**

  Fichier de configuration NuGet. Si ce paramètre est spécifié, seuls les paramètres de ce fichier seront utilisés. S’il n’est pas spécifié, la hiérarchie des fichiers de configuration du répertoire actif sera utilisée. Pour plus d’informations, consultez [configurations NuGet courantes](/nuget/consume-packages/configuring-nuget-behavior).

- **`-p|--password <PASSWORD>`**

  Mot de passe à utiliser lors de la connexion à une source authentifiée.

- **`-s|--source <SOURCE>`**

  Chemin d’accès à la source du package.

- **`--store-password-in-clear-text`**

  Active le stockage des informations d’identification de la source du package portable en désactivant le chiffrement du mot de passe.

- **`-u|--username <USER>`**

  Nom d’utilisateur à utiliser lors de la connexion à une source authentifiée.

- **`--valid-authentication-types <TYPES>`**

  Liste séparée par des virgules des types d’authentification valides pour cette source. Définissez cette valeur sur `basic` si le serveur publie NTLM ou Negotiate et que vos informations d’identification doivent être envoyées à l’aide du mécanisme de base, par exemple lors de l’utilisation d’un Pat avec un Azure DevOps Server local. Les autres valeurs valides incluent `negotiate` , `kerberos` , `ntlm` et `digest` , mais ces valeurs ne sont pas susceptibles d’être utiles.

## <a name="examples"></a>Exemples

- Mettez à jour une source avec le nom `mySource` :

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>Voir aussi

- [Sections sources du package dans les fichiers NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, commande (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
