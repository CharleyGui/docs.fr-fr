---
title: Sauvegarde en ligne
ms.date: 12/13/2019
description: Découvrez comment utiliser la fonctionnalité de sauvegarde en ligne de SQLite.
ms.openlocfilehash: 885aa2c5555b58deb2551c0a4e6933742a093457
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447096"
---
# <a name="online-backup"></a>Sauvegarde en ligne

SQLite peut sauvegarder des fichiers de base de données pendant que l’application est en cours d’exécution. Cette fonctionnalité est disponible dans Microsoft. Data. sqlite comme méthode <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> sur `SqliteConnection`.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

Actuellement, `BackupDatabase` sauvegarde la base de données aussi rapidement que possible et empêche les autres connexions d’écrire dans la base de données. Le problème [#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834) fournirait une autre API pour sauvegarder la base de données en arrière-plan et permettre à d’autres connexions d’interrompre la sauvegarde et d’écrire dans la base de données. Si vous êtes intéressé, fournissez vos commentaires sur le problème.
