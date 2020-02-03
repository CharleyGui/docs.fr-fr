---
title: Commande dotnet nuget delete
description: La commande nuget-dotnet-delete supprime ou retire un package du serveur.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733124"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nom

`dotnet nuget delete` -Supprime ou retire un package du serveur.

## <a name="synopsis"></a>Résumé

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet nuget delete` supprime ou retire un package du serveur. Pour [nuget.org](https://www.nuget.org/), l’action consiste à supprimer le package de la liste.

## <a name="arguments"></a>Arguments

* **`PACKAGE_NAME`**

  Nom/ID du package à supprimer.

* **`PACKAGE_VERSION`**

  Version du package à supprimer.

## <a name="options"></a>Options

* **`--force-english-output`**

  Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).

* **`-h|--help`**

  Affiche une aide brève pour la commande.

* **`--interactive`**

  Autorise la commande pour bloquer et exige une action manuelle pour des opérations comme l'authentification. Option disponible à partir du SDK .NET Core 2.2.

* **`-k|--api-key <API_KEY>`**

  Clé d’API pour le serveur.

* **`--no-service-endpoint`**

  N’ajoute pas « api/v2/package » à l’URL source. Option disponible à partir du kit SDK .NET Core 2.1.

* **`--non-interactive`**

  Ne demande pas de saisie ou de confirmation de la part de l’utilisateur.

* **`-s|--source <SOURCE>`**

  Spécifie l’URL du serveur. Les URL prises en charge pour nuget.org incluent `https://www.nuget.org`, `https://www.nuget.org/api/v3` et `https://www.nuget.org/api/v2/package`. Pour les flux privés, remplacez le nom d’hôte (par exemple, `%hostname%/api/v3`).

## <a name="examples"></a>Exemples

* Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` :

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Supprime la version 1.0 du package `Microsoft.AspNetCore.Mvc` sans inviter l’utilisateur à fournir ses informations d’identification ou d’autres données :

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
