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
# <a name="dotnet-nuget-verify"></a>vérification de dotnet NuGet

**Cet article s’applique à :** ✔️ le kit de développement logiciel (SDK) .net 5.0.100-RC. 2. x et versions ultérieures

## <a name="name"></a>Nom

`dotnet nuget verify` -Vérifie un package NuGet signé.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet nuget verify [<package-path(s)>]
    [--all]
    [--certificate-fingerprint <FINGERPRINT>]
    [-v|--verbosity <LEVEL>]

dotnet nuget verify -h|--help
```

## <a name="description"></a>Description

La `dotnet nuget verify` commande vérifie un package NuGet signé.

## <a name="arguments"></a>Arguments

- **`package-path(s)`**

  Spécifie le chemin d’accès au (x) package (s) à vérifier. Plusieurs arguments de position peuvent être passés pour vérifier plusieurs packages.

## <a name="options"></a>Options

- **`--all`**

  Spécifie que toutes les vérifications possibles doivent être effectuées sur le ou les packages. Par défaut, seuls `signatures` sont vérifiés.

> [!NOTE]
> Cette commande ne prend actuellement en charge que la `signature` vérification.

- **`--certificate-fingerprint <FINGERPRINT>`**

  Vérifiez que le certificat de signataire correspond à l’une des `SHA256` empreintes spécifiées. Cette option peut être fournie plusieurs fois pour fournir plusieurs empreintes digitales.

* **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail MSBuild. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Par défaut, il s’agit de `normal`.

* **`-h|--help`**

  Affiche une aide brève pour la commande.

## <a name="examples"></a>Exemples

- Vérifiez *foo. nupkg*:

  ```dotnetcli
  dotnet nuget verify foo.nupkg
  ```

- Vérifiez que plusieurs packages NuGet- *foo. nupkg* et *tous les fichiers. nupkg dans le répertoire spécifié*:

  ```dotnetcli
  dotnet nuget verify foo.nupkg c:\mydir\*.nupkg
  ```

- Vérifiez que la signature de *foo. nupkg* correspond à l’empreinte de certificat spécifiée :

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039
  ```

- Vérifiez que la signature de *foo. nupkg* correspond à l’une des empreintes de certificat spécifiées :

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 --certificate-fingerprint EC10992GG5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E027
  ```
