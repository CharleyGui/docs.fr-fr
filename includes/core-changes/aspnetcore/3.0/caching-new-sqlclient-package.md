---
ms.openlocfilehash: 32c7f4e9e4736145f9275b74f34c04404e7c770a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394110"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="817e3-101">Mise en cache : Microsoft. extensions. Caching. SqlServer utilise le nouveau package SqlClient</span><span class="sxs-lookup"><span data-stu-id="817e3-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="817e3-102">Le package `Microsoft.Extensions.Caching.SqlServer` utilise le nouveau package `Microsoft.Data.SqlClient` au lieu du package `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="817e3-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="817e3-103">Cette modification peut entraîner de légères modifications avec rupture de comportement.</span><span class="sxs-lookup"><span data-stu-id="817e3-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="817e3-104">Pour plus d’informations, consultez [Présentation du nouveau Microsoft. Data. SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="817e3-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="817e3-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="817e3-105">Version introduced</span></span>

<span data-ttu-id="817e3-106">3,0</span><span class="sxs-lookup"><span data-stu-id="817e3-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="817e3-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="817e3-107">Old behavior</span></span>

<span data-ttu-id="817e3-108">Le package `Microsoft.Extensions.Caching.SqlServer` utilisait le package `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="817e3-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="817e3-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="817e3-109">New behavior</span></span>

<span data-ttu-id="817e3-110">`Microsoft.Extensions.Caching.SqlServer` utilise maintenant le package `Microsoft.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="817e3-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="817e3-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="817e3-111">Reason for change</span></span>

<span data-ttu-id="817e3-112">`Microsoft.Data.SqlClient` est un nouveau package qui est créé à partir de `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="817e3-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="817e3-113">C’est là que tous les nouveaux travaux de fonctionnalités seront effectués à partir de maintenant.</span><span class="sxs-lookup"><span data-stu-id="817e3-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="817e3-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="817e3-114">Recommended action</span></span>

<span data-ttu-id="817e3-115">Les clients ne doivent pas avoir à se soucier de cette modification avec rupture, sauf s’ils utilisaient des types retournés par le package `Microsoft.Extensions.Caching.SqlServer` et les castant en types `System.Data.SqlClient`.</span><span class="sxs-lookup"><span data-stu-id="817e3-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="817e3-116">Par exemple, si quelqu’un effectuait un cast d’un `DbConnection` vers l' [ancien type SqlConnection](xref:System.Data.SqlClient.SqlConnection), il aurait besoin de remplacer le cast par le nouveau type `Microsoft.Data.SqlClient.SqlConnection`.</span><span class="sxs-lookup"><span data-stu-id="817e3-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span> 

#### <a name="category"></a><span data-ttu-id="817e3-117">Category</span><span class="sxs-lookup"><span data-stu-id="817e3-117">Category</span></span>

<span data-ttu-id="817e3-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="817e3-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="817e3-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="817e3-119">Affected APIs</span></span>

<span data-ttu-id="817e3-120">aucune.</span><span class="sxs-lookup"><span data-stu-id="817e3-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
