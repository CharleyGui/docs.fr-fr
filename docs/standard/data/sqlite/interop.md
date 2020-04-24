---
title: Interopérabilité
ms.date: 12/13/2019
description: Découvrez comment interagir avec d’autres bibliothèques SQLite.
ms.openlocfilehash: 486e2a8e00999b8ebe9c85a5fcc1539c514676d3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447236"
---
# <a name="interoperability"></a>Interopérabilité

Microsoft. Data. sqlite utilise SQLitePCLRaw pour interagir avec la bibliothèque SQLite native. SQLitePCLRaw fournit une API .NET fine sur l’API SQLite native. SqliteConnection et SqliteDataReader fournissent l’accès aux objets SQLitePCLRaw sous-jacents, ce qui vous permet d’appeler ces API directement.

L’exemple suivant montre comment appeler `sqlite3_trace` pour écrire des instructions SQL exécutées sur la console :

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

Et l’exemple suivant illustre l' `sqlite3_stmt_status` appel de pour afficher le nombre d’étapes de machine virtuelle SQLite compilées par une instruction SQL :

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

Les objets SQLitePCLRaw exposent même un pointeur vers les objets natifs pour vous permettre d’appeler P/Invoke des API SQLite natives supplémentaires.
