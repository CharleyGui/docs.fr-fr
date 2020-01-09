---
title: Comparaison avec System. Data. SQLite
ms.date: 12/13/2019
description: Décrit quelques-unes des différences entre les bibliothèques Microsoft. Data. sqlite et System. Data. SQLite.
ms.openlocfilehash: dee90c132b108f2c876c0d8becc1b02035a47b61
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447019"
---
# <a name="comparison-to-systemdatasqlite"></a><span data-ttu-id="b0a70-103">Comparaison avec System. Data. SQLite</span><span class="sxs-lookup"><span data-stu-id="b0a70-103">Comparison to System.Data.SQLite</span></span>

<span data-ttu-id="b0a70-104">Dans 2005, Robert Simpson a créé System. Data. SQLite, un fournisseur SQLite pour ADO.NET 2,0.</span><span class="sxs-lookup"><span data-stu-id="b0a70-104">In 2005, Robert Simpson created System.Data.SQLite, a SQLite provider for ADO.NET 2.0.</span></span> <span data-ttu-id="b0a70-105">Dans 2010, l’équipe SQLite a pris en charge la maintenance et le développement du projet.</span><span class="sxs-lookup"><span data-stu-id="b0a70-105">In 2010, the SQLite team took over maintenance and development of the project.</span></span> <span data-ttu-id="b0a70-106">Il est également intéressant de noter que l’équipe mono a fait la duplication du code dans 2007 en tant que mono. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="b0a70-106">It's also worth noting that the Mono team forked the code in 2007 as Mono.Data.Sqlite.</span></span> <span data-ttu-id="b0a70-107">System. Data. SQLite a un long historique et a évolué vers un fournisseur ADO.NET entièrement stable et complet avec les outils Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0a70-107">System.Data.SQLite has a long history and has evolved into a stable and full-featured ADO.NET provider complete with Visual Studio tooling.</span></span> <span data-ttu-id="b0a70-108">Les nouvelles versions continuent à expédier les assemblys compatibles avec chaque version de .NET Framework à la version 2,0 et même .NET Compact Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="b0a70-108">New releases continue to ship assemblies compatible with every version of .NET Framework back to version 2.0 and even .NET Compact Framework 3.5.</span></span>

<span data-ttu-id="b0a70-109">La première version de .NET Core (publiée dans 2016) était une implémentation unique, légère, moderne et multiplateforme de .NET.</span><span class="sxs-lookup"><span data-stu-id="b0a70-109">The first version of .NET Core (released in 2016) was a single, lightweight, modern, and cross-platform implementation of .NET.</span></span> <span data-ttu-id="b0a70-110">Les API obsolètes et les API avec d’autres alternatives modernes ont été supprimées intentionnellement.</span><span class="sxs-lookup"><span data-stu-id="b0a70-110">Obsolete APIs and APIs with more modern alternatives were intentionally removed.</span></span> <span data-ttu-id="b0a70-111">ADO.NET n’incluait aucune API de DataSet (y compris DataTable et DataAdapter).</span><span class="sxs-lookup"><span data-stu-id="b0a70-111">ADO.NET didn't include any of the DataSet APIs (including DataTable and DataAdapter).</span></span>

<span data-ttu-id="b0a70-112">L’équipe Entity Framework a été très familiarisé avec le code base System. Data. SQLite.</span><span class="sxs-lookup"><span data-stu-id="b0a70-112">The Entity Framework team was somewhat familiar with the System.Data.SQLite codebase.</span></span> <span data-ttu-id="b0a70-113">Brice Lambson, membre de l’équipe EF, avait auparavant aidé l’équipe SQLite à ajouter la prise en charge des versions 5 et 6 de Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b0a70-113">Brice Lambson, a member of the EF team, had previously helped the SQLite team add support for Entity Framework versions 5 and 6.</span></span> <span data-ttu-id="b0a70-114">Brice a également fait l’expérience de sa propre implémentation d’un fournisseur SQLite ADO.NET en même temps que .NET Core était planifié.</span><span class="sxs-lookup"><span data-stu-id="b0a70-114">Brice was also experimenting with his own implementation of a SQLite ADO.NET provider around the same time that .NET Core was being planned.</span></span> <span data-ttu-id="b0a70-115">Après une longue discussion, l’équipe Entity Framework a décidé de créer Microsoft. Data. sqlite en fonction du prototype de brice.</span><span class="sxs-lookup"><span data-stu-id="b0a70-115">After a long discussion, the Entity Framework team decided to create Microsoft.Data.Sqlite based on Brice's prototype.</span></span> <span data-ttu-id="b0a70-116">Cela leur permettrait de créer une nouvelle implémentation légère et moderne qui s’alignerait sur les objectifs de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b0a70-116">This would allow them to create a new lightweight and modern implementation that would align with the goals of .NET Core.</span></span>

<span data-ttu-id="b0a70-117">À titre d’exemple de ce que nous entendons par plus moderne, voici le code permettant de créer une [fonction définie](user-defined-functions.md) par l’utilisateur dans System. Data. sqlite et Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="b0a70-117">As an example of what we mean by more modern, here is code to create a [user-defined function](user-defined-functions.md) in both System.Data.SQLite and Microsoft.Data.Sqlite.</span></span>

```csharp
// System.Data.SQLite
connection.BindFunction(
    new SQLiteFunctionAttribute("ceiling", 1, FunctionType.Scalar),
    (Func<object[], object>)((object[] args) => Math.Ceiling((double)((object[])args[1])[0])),
    null);

// Microsoft.Data.Sqlite
connection.CreateFunction(
    "ceiling",
    (double arg) => Math.Ceiling(arg));
```

<span data-ttu-id="b0a70-118">Dans 2017, .NET Core 2,0 a subi un changement de stratégie.</span><span class="sxs-lookup"><span data-stu-id="b0a70-118">In 2017, .NET Core 2.0 experienced a change in strategy.</span></span> <span data-ttu-id="b0a70-119">Il a été décidé que la compatibilité avec .NET Framework était vitale pour la réussite de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b0a70-119">It was decided that compatibility with .NET Framework was vital to the success of .NET Core.</span></span> <span data-ttu-id="b0a70-120">La plupart des API supprimées, y compris les API de jeu de données, ont été rajoutées.</span><span class="sxs-lookup"><span data-stu-id="b0a70-120">Many of the removed APIs, including the DataSet APIs, were added back.</span></span> <span data-ttu-id="b0a70-121">Comme c’était le cas pour de nombreux autres, cette valeur de System. Data. SQLite débloquée, ce qui lui permet de porter également sur .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b0a70-121">Like it did for many others, this unblocked System.Data.SQLite allowing it to also be ported to .NET Core.</span></span> <span data-ttu-id="b0a70-122">L’objectif initial de Microsoft. Data. sqlite à être léger et moderne, toutefois, reste toujours.</span><span class="sxs-lookup"><span data-stu-id="b0a70-122">The original goal of Microsoft.Data.Sqlite to be lightweight and modern, however, still remains.</span></span> <span data-ttu-id="b0a70-123">Pour plus d’informations sur les API ADO.NET non implémentées par Microsoft. Data. sqlite, consultez [limitations de ADO.net](adonet-limitations.md) .</span><span class="sxs-lookup"><span data-stu-id="b0a70-123">See [ADO.NET limitations](adonet-limitations.md) for details about ADO.NET APIs not implemented by Microsoft.Data.Sqlite.</span></span>

<span data-ttu-id="b0a70-124">Lorsque de nouvelles fonctionnalités sont ajoutées à Microsoft. Data. sqlite, la conception de System. Data. SQLite est prise en compte.</span><span class="sxs-lookup"><span data-stu-id="b0a70-124">When new features are added to Microsoft.Data.Sqlite, the design of System.Data.SQLite is taken into account.</span></span> <span data-ttu-id="b0a70-125">Nous essayons, dans la mesure du possible, de réduire les modifications entre les deux pour faciliter la transition entre eux.</span><span class="sxs-lookup"><span data-stu-id="b0a70-125">We try, when possible, to minimize changes between the two to ease transitioning between them.</span></span>

## <a name="data-types"></a><span data-ttu-id="b0a70-126">Types de données</span><span class="sxs-lookup"><span data-stu-id="b0a70-126">Data types</span></span>

<span data-ttu-id="b0a70-127">La plus grande différence entre Microsoft. Data. sqlite et System. Data. SQLite est la manière dont les types de données sont gérés.</span><span class="sxs-lookup"><span data-stu-id="b0a70-127">The biggest difference between Microsoft.Data.Sqlite and System.Data.SQLite is how data types are handled.</span></span> <span data-ttu-id="b0a70-128">Comme décrit dans [types de données](types.md), Microsoft. Data. sqlite ne tente pas de masquer le quirkiness sous-jacent de SQLite, ce qui permet de spécifier n’importe quelle chaîne arbitraire comme type de colonne et possède uniquement quatre types primitifs : entier, réel, texte et objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="b0a70-128">As described in [Data types](types.md), Microsoft.Data.Sqlite doesn't try to hide the underlying quirkiness of SQLite, which allows any arbitrary string to be specified as the column type, and only has four primitive types: INTEGER, REAL, TEXT, and BLOB.</span></span>

<span data-ttu-id="b0a70-129">System. Data. SQLite applique une sémantique supplémentaire aux types de colonne qui les mappent directement aux types .NET.</span><span class="sxs-lookup"><span data-stu-id="b0a70-129">System.Data.SQLite applies additional semantics to column types mapping them directly to .NET types.</span></span> <span data-ttu-id="b0a70-130">Cela donne au fournisseur une sensation plus fortement typée, mais il a des bords approximatifs.</span><span class="sxs-lookup"><span data-stu-id="b0a70-130">This gives the provider a more strongly typed feel, but it has some rough edges.</span></span> <span data-ttu-id="b0a70-131">Par exemple, ils devaient introduire une nouvelle instruction SQL (TYPES) pour spécifier les types de colonne des expressions dans les instructions SELECT.</span><span class="sxs-lookup"><span data-stu-id="b0a70-131">For example, they had to introduce a new SQL statement (TYPES) to specify the column types of expressions in SELECT statements.</span></span>

## <a name="connection-strings"></a><span data-ttu-id="b0a70-132">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="b0a70-132">Connection strings</span></span>

<span data-ttu-id="b0a70-133">Microsoft. Data. sqlite a beaucoup moins de mots clés de [chaîne de connexion](connection-strings.md) .</span><span class="sxs-lookup"><span data-stu-id="b0a70-133">Microsoft.Data.Sqlite has a lot fewer [connection string](connection-strings.md) keywords.</span></span> <span data-ttu-id="b0a70-134">Le tableau suivant présente des alternatives qui peuvent être utilisées à la place.</span><span class="sxs-lookup"><span data-stu-id="b0a70-134">The following table shows alternatives that can be used instead.</span></span>

| <span data-ttu-id="b0a70-135">Mot clé</span><span class="sxs-lookup"><span data-stu-id="b0a70-135">Keyword</span></span>          | <span data-ttu-id="b0a70-136">Alternative</span><span class="sxs-lookup"><span data-stu-id="b0a70-136">Alternative</span></span>                                         |
| ---------------- | --------------------------------------------------- |
| <span data-ttu-id="b0a70-137">Taille du cache</span><span class="sxs-lookup"><span data-stu-id="b0a70-137">Cache Size</span></span>       | <span data-ttu-id="b0a70-138">`PRAGMA cache_size = <pages>` d’envoi</span><span class="sxs-lookup"><span data-stu-id="b0a70-138">Send `PRAGMA cache_size = <pages>`</span></span>                  |
| <span data-ttu-id="b0a70-139">Délai d’expiration par défaut</span><span class="sxs-lookup"><span data-stu-id="b0a70-139">Default Timeout</span></span>  | <span data-ttu-id="b0a70-140">Utiliser la propriété DefaultTimeout sur SqliteConnection</span><span class="sxs-lookup"><span data-stu-id="b0a70-140">Use the DefaultTimeout property on SqliteConnection</span></span> |
| <span data-ttu-id="b0a70-141">FailIfMissing</span><span class="sxs-lookup"><span data-stu-id="b0a70-141">FailIfMissing</span></span>    | <span data-ttu-id="b0a70-142">Utiliser `Mode=ReadWrite`.</span><span class="sxs-lookup"><span data-stu-id="b0a70-142">Use `Mode=ReadWrite`</span></span>                                |
| <span data-ttu-id="b0a70-143">FullUri</span><span class="sxs-lookup"><span data-stu-id="b0a70-143">FullUri</span></span>          | <span data-ttu-id="b0a70-144">Utiliser le mot clé de source de données</span><span class="sxs-lookup"><span data-stu-id="b0a70-144">Use the Data Source keyword</span></span>                         |
| <span data-ttu-id="b0a70-145">Mode Journal</span><span class="sxs-lookup"><span data-stu-id="b0a70-145">Journal Mode</span></span>     | <span data-ttu-id="b0a70-146">`PRAGMA journal_mode = <mode>` d’envoi</span><span class="sxs-lookup"><span data-stu-id="b0a70-146">Send `PRAGMA journal_mode = <mode>`</span></span>                 |
| <span data-ttu-id="b0a70-147">Format hérité</span><span class="sxs-lookup"><span data-stu-id="b0a70-147">Legacy Format</span></span>    | <span data-ttu-id="b0a70-148">`PRAGMA legacy_file_format = 1` d’envoi</span><span class="sxs-lookup"><span data-stu-id="b0a70-148">Send `PRAGMA legacy_file_format = 1`</span></span>                |
| <span data-ttu-id="b0a70-149">Nombre maximal de pages</span><span class="sxs-lookup"><span data-stu-id="b0a70-149">Max Page Count</span></span>   | <span data-ttu-id="b0a70-150">`PRAGMA max_page_count = <pages>` d’envoi</span><span class="sxs-lookup"><span data-stu-id="b0a70-150">Send `PRAGMA max_page_count = <pages>`</span></span>              |
| <span data-ttu-id="b0a70-151">Taille de la page</span><span class="sxs-lookup"><span data-stu-id="b0a70-151">Page Size</span></span>        | <span data-ttu-id="b0a70-152">`PRAGMA page_size = <bytes>` d’envoi</span><span class="sxs-lookup"><span data-stu-id="b0a70-152">Send `PRAGMA page_size = <bytes>`</span></span>                   |
| <span data-ttu-id="b0a70-153">Lecture seule</span><span class="sxs-lookup"><span data-stu-id="b0a70-153">Read Only</span></span>        | <span data-ttu-id="b0a70-154">Utiliser `Mode=ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="b0a70-154">Use `Mode=ReadOnly`</span></span>                                 |
| <span data-ttu-id="b0a70-155">Synchronous</span><span class="sxs-lookup"><span data-stu-id="b0a70-155">Synchronous</span></span>      | <span data-ttu-id="b0a70-156">`PRAGMA synchronous = <mode>` d’envoi</span><span class="sxs-lookup"><span data-stu-id="b0a70-156">Send `PRAGMA synchronous = <mode>`</span></span>                  |
| <span data-ttu-id="b0a70-157">URI</span><span class="sxs-lookup"><span data-stu-id="b0a70-157">Uri</span></span>              | <span data-ttu-id="b0a70-158">Utiliser le mot clé de source de données</span><span class="sxs-lookup"><span data-stu-id="b0a70-158">Use the Data Source keyword</span></span>                         |
| <span data-ttu-id="b0a70-159">UseUTF16Encoding</span><span class="sxs-lookup"><span data-stu-id="b0a70-159">UseUTF16Encoding</span></span> | <span data-ttu-id="b0a70-160">`PRAGMA encoding = 'UTF-16'` d’envoi</span><span class="sxs-lookup"><span data-stu-id="b0a70-160">Send `PRAGMA encoding = 'UTF-16'`</span></span>                   |

## <a name="authorization"></a><span data-ttu-id="b0a70-161">Autorisation</span><span class="sxs-lookup"><span data-stu-id="b0a70-161">Authorization</span></span>

<span data-ttu-id="b0a70-162">Microsoft. Data. sqlite ne dispose d’aucune API exposant le rappel d’autorisation de SQLite.</span><span class="sxs-lookup"><span data-stu-id="b0a70-162">Microsoft.Data.Sqlite doesn't have any API exposing SQLite's authorization callback.</span></span> <span data-ttu-id="b0a70-163">Utilisez [#13835](https://github.com/aspnet/EntityFrameworkCore/issues/13835) de problème pour fournir des commentaires sur cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="b0a70-163">Use issue [#13835](https://github.com/aspnet/EntityFrameworkCore/issues/13835) to provide feedback about this feature.</span></span>

## <a name="data-change-notifications"></a><span data-ttu-id="b0a70-164">Notifications de modification de données</span><span class="sxs-lookup"><span data-stu-id="b0a70-164">Data change notifications</span></span>

<span data-ttu-id="b0a70-165">Microsoft. Data. sqlite ne dispose d’aucune API exposant les notifications de modification de données de SQLite.</span><span class="sxs-lookup"><span data-stu-id="b0a70-165">Microsoft.Data.Sqlite doesn't have any API exposing SQLite's data change notifications.</span></span> <span data-ttu-id="b0a70-166">Utilisez [#13827](https://github.com/aspnet/EntityFrameworkCore/issues/13827) de problème pour fournir des commentaires sur cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="b0a70-166">Use issue [#13827](https://github.com/aspnet/EntityFrameworkCore/issues/13827) to provide feedback about this feature.</span></span>

## <a name="virtual-table-modules"></a><span data-ttu-id="b0a70-167">Modules de table virtuelle</span><span class="sxs-lookup"><span data-stu-id="b0a70-167">Virtual table modules</span></span>

<span data-ttu-id="b0a70-168">Microsoft. Data. sqlite ne dispose d’aucune API pour la création de modules de table virtuelle.</span><span class="sxs-lookup"><span data-stu-id="b0a70-168">Microsoft.Data.Sqlite doesn't have any API for creating virtual table modules.</span></span> <span data-ttu-id="b0a70-169">Utilisez [#13823](https://github.com/aspnet/EntityFrameworkCore/issues/13823) de problème pour fournir des commentaires sur cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="b0a70-169">Use issue [#13823](https://github.com/aspnet/EntityFrameworkCore/issues/13823) to provide feedback about this feature.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0a70-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0a70-170">See also</span></span>

* [<span data-ttu-id="b0a70-171">Types de données</span><span class="sxs-lookup"><span data-stu-id="b0a70-171">Data types</span></span>](types.md)
* [<span data-ttu-id="b0a70-172">Chaînes de connexion</span><span class="sxs-lookup"><span data-stu-id="b0a70-172">Connection strings</span></span>](connection-strings.md)
* [<span data-ttu-id="b0a70-173">Chiffrement</span><span class="sxs-lookup"><span data-stu-id="b0a70-173">Encryption</span></span>](encryption.md)
* [<span data-ttu-id="b0a70-174">Limitations de ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b0a70-174">ADO.NET limitations</span></span>](adonet-limitations.md)
* [<span data-ttu-id="b0a70-175">Limitations de dapper</span><span class="sxs-lookup"><span data-stu-id="b0a70-175">Dapper limitations</span></span>](dapper-limitations.md)