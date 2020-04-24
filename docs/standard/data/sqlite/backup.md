---
title: Sauvegarde en ligne
ms.date: 12/13/2019
description: Découvrez comment utiliser la fonctionnalité de sauvegarde en ligne de SQLite.
ms.openlocfilehash: d857dcb69f2b2d10b034a0abf222b30c2e20bb41
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901281"
---
# <a name="online-backup"></a>Sauvegarde en ligne

SQLite peut sauvegarder des fichiers de base de données pendant que l’application est en cours d’exécution. Cette fonctionnalité est disponible dans Microsoft. Data. sqlite comme <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> méthode sur. `SqliteConnection`

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

Actuellement, `BackupDatabase` sauvegarde la base de données aussi rapidement que possible et empêche les autres connexions d’écrire dans la base de données. Le problème [#13834](https://github.com/dotnet/efcore/issues/13834) fournirait une autre API pour sauvegarder la base de données en arrière-plan et permettre à d’autres connexions d’interrompre la sauvegarde et d’écrire dans la base de données. Si vous êtes intéressé, fournissez vos commentaires sur le problème.
