---
title: Insertion en bloc
ms.date: 12/13/2019
description: Conseils sur les performances que vous pouvez utiliser lorsque vous apportez de nombreuses modifications à la base de données.
ms.openlocfilehash: 9d87d5c8d70f8e70479f9aa02b7802f73b88de9e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447040"
---
# <a name="bulk-insert"></a><span data-ttu-id="0bd83-103">Insertion en bloc</span><span class="sxs-lookup"><span data-stu-id="0bd83-103">Bulk insert</span></span>

<span data-ttu-id="0bd83-104">SQLite n’a pas de méthode spéciale pour insérer des données en bloc.</span><span class="sxs-lookup"><span data-stu-id="0bd83-104">SQLite doesn't have any special way to bulk insert data.</span></span> <span data-ttu-id="0bd83-105">Pour obtenir des performances optimales lors de l’insertion ou de la mise à jour de données, assurez-vous d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0bd83-105">To get optimal performance when inserting or updating data, ensure that you do the following:</span></span>

- <span data-ttu-id="0bd83-106">Utilisez une transaction.</span><span class="sxs-lookup"><span data-stu-id="0bd83-106">Use a transaction.</span></span>
- <span data-ttu-id="0bd83-107">Réutilisez la même commande paramétrable.</span><span class="sxs-lookup"><span data-stu-id="0bd83-107">Reuse the same parameterized command.</span></span> <span data-ttu-id="0bd83-108">Les exécutions suivantes réutiliseront la compilation du premier.</span><span class="sxs-lookup"><span data-stu-id="0bd83-108">Subsequent executions will reuse the compilation of the first one.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
