---
title: E/S d’objet blob
ms.date: 12/08/2020
description: Découvrez comment utiliser la fonctionnalité d’e/s BLOB de SQLite.
ms.openlocfilehash: 8b305669f3155d2366215e9a05beb5ed51533d81
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110043"
---
# <a name="blob-io"></a>E/S d’objet blob

> [!NOTE]
> La classe SqliteBlob a été ajoutée dans la version 3,0.

Vous pouvez réduire l’utilisation de la mémoire lors de la lecture et de l’écriture d’objets volumineux en diffusant les données dans et hors de la base de données. Cela peut être particulièrement utile lors de l’analyse ou de la transformation des données.

Commencez par insérer une ligne comme d’habitude. Utilisez la `zeroblob()` fonction SQL pour allouer de l’espace dans la base de données afin de conserver l’objet volumineux. La `last_insert_rowid()` fonction offre un moyen pratique d’obtenir son ROWID.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

Après avoir inséré la ligne, ouvrez un flux pour écrire l’objet volumineux à l’aide de <xref:Microsoft.Data.Sqlite.SqliteBlob> .

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

Pour diffuser en continu l’objet volumineux à partir de la base de données, vous devez sélectionner ROWID ou l’un de ses alias comme indiqué ici en plus de la colonne de l’objet volumineux. Si vous ne sélectionnez pas le ROWID, l’objet entier est chargé en mémoire. L’objet retourné par `GetStream()` est une lorsqu’il est `SqliteBlob` terminé correctement.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
