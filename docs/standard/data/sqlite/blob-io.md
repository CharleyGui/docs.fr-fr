---
title: E/S d’objet blob
ms.date: 12/13/2019
description: Découvrez comment utiliser la fonctionnalité d’e/s BLOB de SQLite.
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447047"
---
# <a name="blob-io"></a>E/S d’objet blob

Vous pouvez réduire l’utilisation de la mémoire lors de la lecture et de l’écriture d’objets volumineux en diffusant les données dans et hors de la base de données. Cela peut être particulièrement utile lors de l’analyse ou de la transformation des données.

Commencez par insérer une ligne comme d’habitude. Utilisez la `zeroblob()` fonction SQL pour allouer de l’espace dans la base de données afin de conserver l’objet volumineux. La `last_insert_rowid()` fonction offre un moyen pratique d’obtenir son ROWID.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

Après avoir inséré la ligne, ouvrez un flux pour écrire l’objet volumineux <xref:Microsoft.Data.Sqlite.SqliteBlob>à l’aide de.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

Pour diffuser en continu l’objet volumineux à partir de la base de données, vous devez sélectionner ROWID ou l’un de ses alias comme indiqué ici en plus de la colonne de l’objet volumineux. Si vous ne sélectionnez pas le ROWID, l’objet entier est chargé en mémoire. L’objet retourné par `GetStream()` est une `SqliteBlob` lorsqu’il est terminé correctement.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
