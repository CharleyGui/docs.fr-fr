---
title: Limitations de dapper
ms.date: 12/13/2019
description: Décrit certaines des limitations que vous pouvez rencontrer lors de l’utilisation de dapper.
ms.openlocfilehash: 90c7fb24f068d663081390bdba9b1b222b4be56e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447278"
---
# <a name="dapper-limitations"></a><span data-ttu-id="c18fe-103">Limitations de dapper</span><span class="sxs-lookup"><span data-stu-id="c18fe-103">Dapper limitations</span></span>

<span data-ttu-id="c18fe-104">Il existe quelques limitations que vous devez connaître lors de l’utilisation de Microsoft. Data. sqlite avec [dapper](https://stackexchange.github.io/Dapper/).</span><span class="sxs-lookup"><span data-stu-id="c18fe-104">There are a few limitations you should be aware of when using Microsoft.Data.Sqlite with [Dapper](https://stackexchange.github.io/Dapper/).</span></span>

## <a name="parameters"></a><span data-ttu-id="c18fe-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="c18fe-105">Parameters</span></span>

<span data-ttu-id="c18fe-106">Les noms de paramètres SQLite sont sensibles à la casse.</span><span class="sxs-lookup"><span data-stu-id="c18fe-106">SQLite parameter names are case-sensitive.</span></span> <span data-ttu-id="c18fe-107">Assurez-vous que les noms de paramètres utilisés dans SQL correspondent à la casse des propriétés de l’objet anonyme.</span><span class="sxs-lookup"><span data-stu-id="c18fe-107">Ensure that the parameter names used in SQL match the case of the anonymous object's properties.</span></span> <span data-ttu-id="c18fe-108">Le problème [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) améliorer cette expérience.</span><span class="sxs-lookup"><span data-stu-id="c18fe-108">Issue [#18861](https://github.com/aspnet/EntityFrameworkCore/issues/18861) would improve this experience.</span></span>

<span data-ttu-id="c18fe-109">Dapper s’attend également à ce que les paramètres utilisent le préfixe `@`.</span><span class="sxs-lookup"><span data-stu-id="c18fe-109">Dapper also expects parameters to use the `@` prefix.</span></span> <span data-ttu-id="c18fe-110">Les autres préfixes ne fonctionneront pas.</span><span class="sxs-lookup"><span data-stu-id="c18fe-110">Other prefixes won't work.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_Parameter)]

## <a name="data-types"></a><span data-ttu-id="c18fe-111">Types de données</span><span class="sxs-lookup"><span data-stu-id="c18fe-111">Data types</span></span>

<span data-ttu-id="c18fe-112">Dapper lit les valeurs à l’aide de l’indexeur SqliteDataReader.</span><span class="sxs-lookup"><span data-stu-id="c18fe-112">Dapper reads values using the SqliteDataReader indexer.</span></span> <span data-ttu-id="c18fe-113">Le type de retour de cet indexeur est Object, ce qui signifie qu’il ne renverra jamais de valeurs de type long, double, String ou Byte [].</span><span class="sxs-lookup"><span data-stu-id="c18fe-113">The return type of this indexer is object, which means it will only ever return long, double, string, or byte[] values.</span></span> <span data-ttu-id="c18fe-114">Pour plus d’informations, consultez [types de données](types.md).</span><span class="sxs-lookup"><span data-stu-id="c18fe-114">For more information, see [Data types](types.md).</span></span> <span data-ttu-id="c18fe-115">Dapper gère la plupart des conversions entre ces types primitifs et les autres.</span><span class="sxs-lookup"><span data-stu-id="c18fe-115">Dapper handles most conversions between these and other primitive types.</span></span> <span data-ttu-id="c18fe-116">Malheureusement, il ne gère pas `DateTimeOffset`, `Guid`ou `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="c18fe-116">Unfortunately, it doesn't handle `DateTimeOffset`, `Guid`, or `TimeSpan`.</span></span> <span data-ttu-id="c18fe-117">Créez des gestionnaires de types si vous souhaitez utiliser ces types dans vos résultats.</span><span class="sxs-lookup"><span data-stu-id="c18fe-117">Create type handlers if you want to use these types in your results.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_TypeHandlers)]

<span data-ttu-id="c18fe-118">N’oubliez pas d’ajouter les gestionnaires de types avant d’interroger.</span><span class="sxs-lookup"><span data-stu-id="c18fe-118">Don't forget to add the type handlers before querying.</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DapperSample/Program.cs?name=snippet_AddTypeHandlers)]

## <a name="see-also"></a><span data-ttu-id="c18fe-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c18fe-119">See also</span></span>

* [<span data-ttu-id="c18fe-120">Types de données</span><span class="sxs-lookup"><span data-stu-id="c18fe-120">Data types</span></span>](types.md)
* [<span data-ttu-id="c18fe-121">Limitations Async</span><span class="sxs-lookup"><span data-stu-id="c18fe-121">Async limitations</span></span>](async.md)
