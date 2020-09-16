---
title: Bases de données en mémoire
ms.date: 12/13/2019
description: Découvrez comment utiliser les bases de données SQLite en mémoire.
ms.openlocfilehash: fbda5787d95a9ce462752b985f847af0b0551fa6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555365"
---
# <a name="in-memory-databases"></a>Bases de données en mémoire

Les bases de données en mémoire SQLite sont stockées entièrement en mémoire, et non sur le disque. Utilisez le nom de fichier de la source de données spéciale `:memory:` pour créer une base de données en mémoire. Lorsque la connexion est fermée, la base de données est supprimée. Lors de l’utilisation `:memory:` de, chaque connexion crée sa propre base de données.

```connectionstring
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Bases de données en mémoire partageables

Les bases de données en mémoire peuvent être partagées entre plusieurs connexions à l’aide de `Mode=Memory` et `Cache=Shared` dans la chaîne de connexion. Le `Data Source` mot clé est utilisé pour attribuer un nom à la base de données en mémoire. Les chaînes de connexion qui utilisent le même nom accèdent à la même base de données en mémoire. La base de données est conservée tant qu’au moins une connexion à celle-ci reste ouverte. Un [exemple](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) illustrant cette fonction est disponible sur GitHub.

```connectionstring
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
