---
title: Commande dotnet nuget locals
description: La commande dotnet nuget locals efface ou répertorie les ressources NuGet locales telles que le cache de requête http, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: b57c127650555e412af08df6656fb62d75c8ed7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734082"
---
# <a name="dotnet-nuget-locals"></a>dotnet nuget locals

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet nuget locals` - Efface ou liste les ressources NuGet locales.

## <a name="synopsis"></a>Résumé

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet nuget locals` efface ou liste les ressources NuGet locales dans le cache de requête HTTP, le cache temporaire ou le dossier des packages globaux à l’échelle de l’ordinateur.

## <a name="arguments"></a>Arguments

* **`CACHE_LOCATION`**

  Emplacement du cache à répertorier ou effacer. L’une des valeurs suivantes est acceptée :

  * `all` : indique que l’opération spécifiée est appliquée à tous les types de cache : le cache de requête HTTP, le cache des packages globaux et le cache temporaire.
  * `http-cache` : indique que l’opération spécifiée est appliquée uniquement au cache de requête HTTP. Les autres emplacements de cache ne sont pas affectés.
  * `global-packages` : indique que l’opération spécifiée est appliquée uniquement au cache des packages globaux. Les autres emplacements de cache ne sont pas affectés.
  * `temp` : indique que l’opération spécifiée est appliquée uniquement au cache temporaire. Les autres emplacements de cache ne sont pas affectés.

## <a name="options"></a>Options

* **`--force-english-output`**

  Force l’application à s’exécuter avec les paramètres régionaux Anglais (culture indifférente).

* **`-h|--help`**

  Affiche une aide brève pour la commande.

* **`-c|--clear`**

  L’option clear exécute une opération d’effacement sur le type de cache spécifié. Le contenu des répertoires de cache est supprimé de manière récursive. Le groupe ou l’utilisateur qui effectue l’opération doit disposer de droits sur les fichiers des répertoires de cache. Sinon, une erreur s’affiche, indiquant les fichiers ou dossiers qui n’ont pas été effacés.

* **`-l|--list`**

  L’option list est utilisée pour afficher l’emplacement du type de cache spécifié.

## <a name="examples"></a>Exemples

* Afficher les chemins d’accès de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :

  ```dotnetcli
  dotnet nuget locals all –l
  ```

* Affiche le chemin du répertoire du cache http local :

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

* Effacer tous les fichiers de tous les répertoires de cache local (le répertoire du cache HTTP, le répertoire du cache des packages globaux et le répertoire du cache temporaire) :

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

* Effacer tous les fichiers du répertoire du cache des packages globaux local :

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

* Effacer tous les fichiers du répertoire du cache temporaire local :

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a>Résolution des problèmes

Pour plus d’informations sur les problèmes et erreurs courants liés à l’utilisation de la commande `dotnet nuget locals`, consultez la page [Gestion du cache NuGet](/nuget/consume-packages/managing-the-nuget-cache).
