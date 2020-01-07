---
title: Bases de données en mémoire
ms.date: 12/13/2019
description: Découvrez comment utiliser les bases de données SQLite en mémoire.
ms.openlocfilehash: b125ff5aa4128bd4c3ff558c5573b7d11802090a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447243"
---
# <a name="in-memory-databases"></a>Bases de données en mémoire

Les bases de données en mémoire SQLite sont stockées entièrement en mémoire, et non sur le disque. Utilisez le nom de fichier de la source de données spéciale `:memory:` pour créer une base de données en mémoire. Lorsque la connexion est fermée, la base de données est supprimée. Lors de l’utilisation de `:memory:`, chaque connexion crée sa propre base de données.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Bases de données en mémoire partageables

Les bases de données en mémoire peuvent être partagées entre plusieurs connexions à l’aide de `Mode=Memory` et `Cache=Shared` dans la chaîne de connexion. Le mot clé `Data Source` est utilisé pour attribuer un nom à la base de données en mémoire. Les chaînes de connexion qui utilisent le même nom accèdent à la même base de données en mémoire. La base de données est conservée tant qu’au moins une connexion à celle-ci reste ouverte. Un [exemple](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) illustrant cette fonction est disponible sur GitHub.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
