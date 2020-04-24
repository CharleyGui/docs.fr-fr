---
title: Bases de données en mémoire
ms.date: 12/13/2019
description: Découvrez comment utiliser les bases de données SQLite en mémoire.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391206"
---
# <a name="in-memory-databases"></a>Bases de données en mémoire

Les bases de données en mémoire SQLite sont stockées entièrement en mémoire, et non sur le disque. Utilisez le nom de fichier `:memory:` de la source de données spéciale pour créer une base de données en mémoire. Lorsque la connexion est fermée, la base de données est supprimée. Lors de `:memory:`l’utilisation de, chaque connexion crée sa propre base de données.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Bases de données en mémoire partageables

Les bases de données en mémoire peuvent être partagées entre plusieurs connexions `Mode=Memory` à `Cache=Shared` l’aide de et dans la chaîne de connexion. Le `Data Source` mot clé est utilisé pour attribuer un nom à la base de données en mémoire. Les chaînes de connexion qui utilisent le même nom accèdent à la même base de données en mémoire. La base de données est conservée tant qu’au moins une connexion à celle-ci reste ouverte. Un [exemple](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) illustrant cette fonction est disponible sur GitHub.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
