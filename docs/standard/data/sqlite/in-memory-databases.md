---
title: Bases de données en mémoire
ms.date: 12/13/2019
description: Apprenez à utiliser les bases de données SQLite en mémoire.
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391206"
---
# <a name="in-memory-databases"></a>Bases de données en mémoire

Les bases de données en mémoire SQLite sont des bases de données entièrement stockées dans la mémoire, et non sur disque. Utilisez le nom de `:memory:` fichier source de données spéciale pour créer une base de données en mémoire. Lorsque la connexion est fermée, la base de données est supprimée. Lors `:memory:`de l’utilisation, chaque connexion crée sa propre base de données.

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>Bases de données en mémoire partageables

Les bases de données en mémoire peuvent `Mode=Memory` `Cache=Shared` être partagées entre plusieurs connexions en utilisant et dans la chaîne de connexion. Le `Data Source` mot clé est utilisé pour donner un nom à la base de données mémoire. Les chaînes de connexion utilisant le même nom accéderont à la même base de données en mémoire. La base de données persiste tant qu’au moins une connexion reste ouverte. Un [échantillon](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs) démontrant cela est disponible sur GitHub.

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
