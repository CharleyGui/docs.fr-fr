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
# <a name="interoperability"></a><span data-ttu-id="34121-103">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="34121-103">Interoperability</span></span>

<span data-ttu-id="34121-104">Microsoft. Data. sqlite utilise SQLitePCLRaw pour interagir avec la bibliothèque SQLite native.</span><span class="sxs-lookup"><span data-stu-id="34121-104">Microsoft.Data.Sqlite uses SQLitePCLRaw to interact with the native SQLite library.</span></span> <span data-ttu-id="34121-105">SQLitePCLRaw fournit une API .NET fine sur l’API SQLite native.</span><span class="sxs-lookup"><span data-stu-id="34121-105">SQLitePCLRaw provides a thin .NET API over the native SQLite API.</span></span> <span data-ttu-id="34121-106">SqliteConnection et SqliteDataReader fournissent l’accès aux objets SQLitePCLRaw sous-jacents, ce qui vous permet d’appeler ces API directement.</span><span class="sxs-lookup"><span data-stu-id="34121-106">SqliteConnection and SqliteDataReader provide access to the underlying SQLitePCLRaw objects letting you call these APIs directly.</span></span>

<span data-ttu-id="34121-107">L’exemple suivant montre comment appeler `sqlite3_trace` pour écrire des instructions SQL exécutées sur la console :</span><span class="sxs-lookup"><span data-stu-id="34121-107">The following example shows how to call `sqlite3_trace` to write executed SQL statements to the console:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_Trace)]

<span data-ttu-id="34121-108">Et l’exemple suivant illustre l' `sqlite3_stmt_status` appel de pour afficher le nombre d’étapes de machine virtuelle SQLite compilées par une instruction SQL :</span><span class="sxs-lookup"><span data-stu-id="34121-108">And the following example shows calling `sqlite3_stmt_status` to see how many SQLite virtual machine steps a SQL statement compiled into:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/InteropSample/Program.cs?name=snippet_StatementStatus)]

<span data-ttu-id="34121-109">Les objets SQLitePCLRaw exposent même un pointeur vers les objets natifs pour vous permettre d’appeler P/Invoke des API SQLite natives supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="34121-109">The SQLitePCLRaw objects even expose a pointer to the native objects letting you P/Invoke additional native SQLite APIs.</span></span>
