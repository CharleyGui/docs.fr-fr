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
# <a name="online-backup"></a><span data-ttu-id="c18db-103">Sauvegarde en ligne</span><span class="sxs-lookup"><span data-stu-id="c18db-103">Online backup</span></span>

<span data-ttu-id="c18db-104">SQLite peut sauvegarder des fichiers de base de données pendant que l’application est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c18db-104">SQLite can back up database files while the app is running.</span></span> <span data-ttu-id="c18db-105">Cette fonctionnalité est disponible dans Microsoft. Data. sqlite comme <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> méthode sur. `SqliteConnection`</span><span class="sxs-lookup"><span data-stu-id="c18db-105">This functionality is available in Microsoft.Data.Sqlite as the <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> method on `SqliteConnection`.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

<span data-ttu-id="c18db-106">Actuellement, `BackupDatabase` sauvegarde la base de données aussi rapidement que possible et empêche les autres connexions d’écrire dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="c18db-106">Currently, `BackupDatabase` will back up the database as quickly as possible and blocks other connections from writing to the database.</span></span> <span data-ttu-id="c18db-107">Le problème [#13834](https://github.com/dotnet/efcore/issues/13834) fournirait une autre API pour sauvegarder la base de données en arrière-plan et permettre à d’autres connexions d’interrompre la sauvegarde et d’écrire dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="c18db-107">Issue [#13834](https://github.com/dotnet/efcore/issues/13834) would provide an alternative API to back up the database in the background and allow other connections to interrupt the backup and write to the database.</span></span> <span data-ttu-id="c18db-108">Si vous êtes intéressé, fournissez vos commentaires sur le problème.</span><span class="sxs-lookup"><span data-stu-id="c18db-108">If you're interested, provide feedback on the issue.</span></span>
