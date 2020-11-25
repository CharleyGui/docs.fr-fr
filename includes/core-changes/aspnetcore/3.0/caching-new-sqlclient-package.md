---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032484"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="efe7d-101">Mise en cache : Microsoft. extensions. Caching. SqlServer utilise le nouveau package SqlClient</span><span class="sxs-lookup"><span data-stu-id="efe7d-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="efe7d-102">Le `Microsoft.Extensions.Caching.SqlServer` package utilise le nouveau package à la `Microsoft.Data.SqlClient` place du `System.Data.SqlClient` Package.</span><span class="sxs-lookup"><span data-stu-id="efe7d-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="efe7d-103">Cette modification peut entraîner de légères modifications avec rupture de comportement.</span><span class="sxs-lookup"><span data-stu-id="efe7d-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="efe7d-104">Pour plus d’informations, consultez [Présentation du nouveau Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="efe7d-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="efe7d-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="efe7d-105">Version introduced</span></span>

<span data-ttu-id="efe7d-106">3.0</span><span class="sxs-lookup"><span data-stu-id="efe7d-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="efe7d-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="efe7d-107">Old behavior</span></span>

<span data-ttu-id="efe7d-108">Le `Microsoft.Extensions.Caching.SqlServer` package a utilisé le `System.Data.SqlClient` Package.</span><span class="sxs-lookup"><span data-stu-id="efe7d-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="efe7d-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="efe7d-109">New behavior</span></span>

<span data-ttu-id="efe7d-110">`Microsoft.Extensions.Caching.SqlServer` utilise maintenant le `Microsoft.Data.SqlClient` Package.</span><span class="sxs-lookup"><span data-stu-id="efe7d-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="efe7d-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="efe7d-111">Reason for change</span></span>

<span data-ttu-id="efe7d-112">`Microsoft.Data.SqlClient` est un nouveau package qui est créé à partir de `System.Data.SqlClient` .</span><span class="sxs-lookup"><span data-stu-id="efe7d-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="efe7d-113">C’est là que tous les nouveaux travaux de fonctionnalités seront effectués à partir de maintenant.</span><span class="sxs-lookup"><span data-stu-id="efe7d-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="efe7d-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="efe7d-114">Recommended action</span></span>

<span data-ttu-id="efe7d-115">Les clients ne doivent pas avoir à se soucier de cette modification avec rupture, sauf s’ils utilisaient des types retournés par le `Microsoft.Extensions.Caching.SqlServer` package et les castant en `System.Data.SqlClient` types.</span><span class="sxs-lookup"><span data-stu-id="efe7d-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="efe7d-116">Par exemple, si quelqu’un effectuait un cast de `DbConnection` en l' [ancien type SqlConnection](xref:System.Data.SqlClient.SqlConnection), il aurait besoin de remplacer le cast par le nouveau `Microsoft.Data.SqlClient.SqlConnection` type.</span><span class="sxs-lookup"><span data-stu-id="efe7d-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="efe7d-117">Category</span><span class="sxs-lookup"><span data-stu-id="efe7d-117">Category</span></span>

<span data-ttu-id="efe7d-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="efe7d-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="efe7d-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="efe7d-119">Affected APIs</span></span>

<span data-ttu-id="efe7d-120">None</span><span class="sxs-lookup"><span data-stu-id="efe7d-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
