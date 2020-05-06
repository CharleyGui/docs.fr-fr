---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198425"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="41689-101">Mise en cache : Microsoft. extensions. Caching. SqlServer utilise le nouveau package SqlClient</span><span class="sxs-lookup"><span data-stu-id="41689-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="41689-102">Le `Microsoft.Extensions.Caching.SqlServer` package utilise le nouveau `Microsoft.Data.SqlClient` package à la place `System.Data.SqlClient` du package.</span><span class="sxs-lookup"><span data-stu-id="41689-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="41689-103">Cette modification peut entraîner de légères modifications avec rupture de comportement.</span><span class="sxs-lookup"><span data-stu-id="41689-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="41689-104">Pour plus d’informations, consultez [Présentation du nouveau Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="41689-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="41689-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="41689-105">Version introduced</span></span>

<span data-ttu-id="41689-106">3.0</span><span class="sxs-lookup"><span data-stu-id="41689-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="41689-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="41689-107">Old behavior</span></span>

<span data-ttu-id="41689-108">Le `Microsoft.Extensions.Caching.SqlServer` package a utilisé `System.Data.SqlClient` le package.</span><span class="sxs-lookup"><span data-stu-id="41689-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="41689-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="41689-109">New behavior</span></span>

<span data-ttu-id="41689-110">`Microsoft.Extensions.Caching.SqlServer`utilise maintenant le `Microsoft.Data.SqlClient` package.</span><span class="sxs-lookup"><span data-stu-id="41689-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="41689-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="41689-111">Reason for change</span></span>

<span data-ttu-id="41689-112">`Microsoft.Data.SqlClient`est un nouveau package qui est créé à partir `System.Data.SqlClient`de.</span><span class="sxs-lookup"><span data-stu-id="41689-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="41689-113">C’est là que tous les nouveaux travaux de fonctionnalités seront effectués à partir de maintenant.</span><span class="sxs-lookup"><span data-stu-id="41689-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="41689-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="41689-114">Recommended action</span></span>

<span data-ttu-id="41689-115">Les clients ne doivent pas avoir à se soucier de cette modification avec rupture, sauf `Microsoft.Extensions.Caching.SqlServer` s’ils utilisaient des `System.Data.SqlClient` types retournés par le package et les castant en types.</span><span class="sxs-lookup"><span data-stu-id="41689-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="41689-116">Par exemple, si quelqu’un effectuait un `DbConnection` cast de en l' [ancien type SqlConnection](xref:System.Data.SqlClient.SqlConnection), il aurait besoin de remplacer le cast par `Microsoft.Data.SqlClient.SqlConnection` le nouveau type.</span><span class="sxs-lookup"><span data-stu-id="41689-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="41689-117">Category</span><span class="sxs-lookup"><span data-stu-id="41689-117">Category</span></span>

<span data-ttu-id="41689-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="41689-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="41689-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="41689-119">Affected APIs</span></span>

<span data-ttu-id="41689-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="41689-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
