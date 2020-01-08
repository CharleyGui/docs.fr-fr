---
title: E/s d’objet BLOB
ms.date: 12/13/2019
description: Découvrez comment utiliser la fonctionnalité d’e/s BLOB de SQLite.
ms.openlocfilehash: 0c133deacdc19684eca3a6724fb398dc01fda558
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447047"
---
# <a name="blob-io"></a><span data-ttu-id="4de84-103">E/s d’objet BLOB</span><span class="sxs-lookup"><span data-stu-id="4de84-103">Blob I/O</span></span>

<span data-ttu-id="4de84-104">Vous pouvez réduire l’utilisation de la mémoire lors de la lecture et de l’écriture d’objets volumineux en diffusant les données dans et hors de la base de données.</span><span class="sxs-lookup"><span data-stu-id="4de84-104">You can reduce memory usage while reading and writing large objects by streaming the data into and out of the database.</span></span> <span data-ttu-id="4de84-105">Cela peut être particulièrement utile lors de l’analyse ou de la transformation des données.</span><span class="sxs-lookup"><span data-stu-id="4de84-105">This can be especially useful when parsing or transforming the data.</span></span>

<span data-ttu-id="4de84-106">Commencez par insérer une ligne comme d’habitude.</span><span class="sxs-lookup"><span data-stu-id="4de84-106">Start by inserting a row as normal.</span></span> <span data-ttu-id="4de84-107">Utilisez la fonction SQL `zeroblob()` pour allouer de l’espace dans la base de données afin de conserver l’objet volumineux.</span><span class="sxs-lookup"><span data-stu-id="4de84-107">Use the `zeroblob()` SQL function to allocate space in the database to hold the large object.</span></span> <span data-ttu-id="4de84-108">La fonction `last_insert_rowid()` offre un moyen pratique d’obtenir son ROWID.</span><span class="sxs-lookup"><span data-stu-id="4de84-108">The `last_insert_rowid()` function provides a convenient way to get its rowid.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

<span data-ttu-id="4de84-109">Après avoir inséré la ligne, ouvrez un flux pour écrire l’objet volumineux à l’aide de <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span><span class="sxs-lookup"><span data-stu-id="4de84-109">After inserting the row, open a stream to write the large object using <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

<span data-ttu-id="4de84-110">Pour diffuser en continu l’objet volumineux à partir de la base de données, vous devez sélectionner ROWID ou l’un de ses alias comme indiqué ici en plus de la colonne de l’objet volumineux.</span><span class="sxs-lookup"><span data-stu-id="4de84-110">To stream the large object out of the database, you must select the rowid or one of its aliases as show here in addition to the large object's column.</span></span> <span data-ttu-id="4de84-111">Si vous ne sélectionnez pas le ROWID, l’objet entier est chargé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="4de84-111">If you don't select the rowid, the entire object will be loaded into memory.</span></span> <span data-ttu-id="4de84-112">L’objet retourné par `GetStream()` est une `SqliteBlob` quand il est terminé correctement.</span><span class="sxs-lookup"><span data-stu-id="4de84-112">The object returned by `GetStream()` will be a `SqliteBlob` when done correctly.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
