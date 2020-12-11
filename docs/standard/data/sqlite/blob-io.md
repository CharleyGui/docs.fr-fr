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
# <a name="blob-io"></a><span data-ttu-id="0f98d-103">E/S d’objet blob</span><span class="sxs-lookup"><span data-stu-id="0f98d-103">Blob I/O</span></span>

> [!NOTE]
> <span data-ttu-id="0f98d-104">La classe SqliteBlob a été ajoutée dans la version 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f98d-104">The SqliteBlob class was added in version 3.0.</span></span>

<span data-ttu-id="0f98d-105">Vous pouvez réduire l’utilisation de la mémoire lors de la lecture et de l’écriture d’objets volumineux en diffusant les données dans et hors de la base de données.</span><span class="sxs-lookup"><span data-stu-id="0f98d-105">You can reduce memory usage while reading and writing large objects by streaming the data into and out of the database.</span></span> <span data-ttu-id="0f98d-106">Cela peut être particulièrement utile lors de l’analyse ou de la transformation des données.</span><span class="sxs-lookup"><span data-stu-id="0f98d-106">This can be especially useful when parsing or transforming the data.</span></span>

<span data-ttu-id="0f98d-107">Commencez par insérer une ligne comme d’habitude.</span><span class="sxs-lookup"><span data-stu-id="0f98d-107">Start by inserting a row as normal.</span></span> <span data-ttu-id="0f98d-108">Utilisez la `zeroblob()` fonction SQL pour allouer de l’espace dans la base de données afin de conserver l’objet volumineux.</span><span class="sxs-lookup"><span data-stu-id="0f98d-108">Use the `zeroblob()` SQL function to allocate space in the database to hold the large object.</span></span> <span data-ttu-id="0f98d-109">La `last_insert_rowid()` fonction offre un moyen pratique d’obtenir son ROWID.</span><span class="sxs-lookup"><span data-stu-id="0f98d-109">The `last_insert_rowid()` function provides a convenient way to get its rowid.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Insert)]

<span data-ttu-id="0f98d-110">Après avoir inséré la ligne, ouvrez un flux pour écrire l’objet volumineux à l’aide de <xref:Microsoft.Data.Sqlite.SqliteBlob> .</span><span class="sxs-lookup"><span data-stu-id="0f98d-110">After inserting the row, open a stream to write the large object using <xref:Microsoft.Data.Sqlite.SqliteBlob>.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Write)]

<span data-ttu-id="0f98d-111">Pour diffuser en continu l’objet volumineux à partir de la base de données, vous devez sélectionner ROWID ou l’un de ses alias comme indiqué ici en plus de la colonne de l’objet volumineux.</span><span class="sxs-lookup"><span data-stu-id="0f98d-111">To stream the large object out of the database, you must select the rowid or one of its aliases as show here in addition to the large object's column.</span></span> <span data-ttu-id="0f98d-112">Si vous ne sélectionnez pas le ROWID, l’objet entier est chargé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="0f98d-112">If you don't select the rowid, the entire object will be loaded into memory.</span></span> <span data-ttu-id="0f98d-113">L’objet retourné par `GetStream()` est une lorsqu’il est `SqliteBlob` terminé correctement.</span><span class="sxs-lookup"><span data-stu-id="0f98d-113">The object returned by `GetStream()` will be a `SqliteBlob` when done correctly.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/StreamingSample/Program.cs?name=snippet_Read)]
