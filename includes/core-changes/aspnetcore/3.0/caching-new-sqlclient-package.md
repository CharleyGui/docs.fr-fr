---
ms.openlocfilehash: 771238c53dc97f4cf4068968f3c68500ba9f87da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73198425"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a><span data-ttu-id="b00d3-101">Caching: Microsoft.Extensions.Caching.SqlServer utilise le nouveau paquet SqlClient</span><span class="sxs-lookup"><span data-stu-id="b00d3-101">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>

<span data-ttu-id="b00d3-102">Le `Microsoft.Extensions.Caching.SqlServer` paquet utilisera `Microsoft.Data.SqlClient` le `System.Data.SqlClient` nouveau paquet au lieu du paquet.</span><span class="sxs-lookup"><span data-stu-id="b00d3-102">The `Microsoft.Extensions.Caching.SqlServer` package will use the new `Microsoft.Data.SqlClient` package instead of `System.Data.SqlClient` package.</span></span> <span data-ttu-id="b00d3-103">Ce changement pourrait provoquer de légers changements de rupture comportementale.</span><span class="sxs-lookup"><span data-stu-id="b00d3-103">This change could cause slight behavioral breaking changes.</span></span> <span data-ttu-id="b00d3-104">Pour plus d’informations, voir [Présentation du nouveau Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span><span class="sxs-lookup"><span data-stu-id="b00d3-104">For more information, see [Introducing the new Microsoft.Data.SqlClient](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b00d3-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="b00d3-105">Version introduced</span></span>

<span data-ttu-id="b00d3-106">3.0</span><span class="sxs-lookup"><span data-stu-id="b00d3-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b00d3-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="b00d3-107">Old behavior</span></span>

<span data-ttu-id="b00d3-108">Le `Microsoft.Extensions.Caching.SqlServer` paquet `System.Data.SqlClient` a utilisé le paquet.</span><span class="sxs-lookup"><span data-stu-id="b00d3-108">The `Microsoft.Extensions.Caching.SqlServer` package used the `System.Data.SqlClient` package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b00d3-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="b00d3-109">New behavior</span></span>

<span data-ttu-id="b00d3-110">`Microsoft.Extensions.Caching.SqlServer`utilise maintenant `Microsoft.Data.SqlClient` le paquet.</span><span class="sxs-lookup"><span data-stu-id="b00d3-110">`Microsoft.Extensions.Caching.SqlServer` is now using the `Microsoft.Data.SqlClient` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b00d3-111">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="b00d3-111">Reason for change</span></span>

<span data-ttu-id="b00d3-112">`Microsoft.Data.SqlClient`est un nouveau paquet qui `System.Data.SqlClient`est construit hors de .</span><span class="sxs-lookup"><span data-stu-id="b00d3-112">`Microsoft.Data.SqlClient` is a new package that is built off of `System.Data.SqlClient`.</span></span> <span data-ttu-id="b00d3-113">C’est là que tout nouveau travail de fonctionnalité sera fait à partir de maintenant.</span><span class="sxs-lookup"><span data-stu-id="b00d3-113">It's where all new feature work will be done from now on.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b00d3-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="b00d3-114">Recommended action</span></span>

<span data-ttu-id="b00d3-115">Les clients ne devraient pas avoir à s’inquiéter de `Microsoft.Extensions.Caching.SqlServer` ce changement `System.Data.SqlClient` de rupture à moins qu’ils ont été en utilisant des types retournés par le paquet et de les jeter à des types.</span><span class="sxs-lookup"><span data-stu-id="b00d3-115">Customers shouldn't need to worry about this breaking change unless they were using types returned by the `Microsoft.Extensions.Caching.SqlServer` package and casting them to `System.Data.SqlClient` types.</span></span> <span data-ttu-id="b00d3-116">Par exemple, si quelqu’un jetait un `DbConnection` à [l’ancien type SqlConnection](xref:System.Data.SqlClient.SqlConnection), ils auraient besoin de changer le casting pour le nouveau `Microsoft.Data.SqlClient.SqlConnection` type.</span><span class="sxs-lookup"><span data-stu-id="b00d3-116">For example, if someone was casting a `DbConnection` to the [old SqlConnection type](xref:System.Data.SqlClient.SqlConnection), they would need to change the cast to the new `Microsoft.Data.SqlClient.SqlConnection` type.</span></span>

#### <a name="category"></a><span data-ttu-id="b00d3-117">Category</span><span class="sxs-lookup"><span data-stu-id="b00d3-117">Category</span></span>

<span data-ttu-id="b00d3-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b00d3-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b00d3-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="b00d3-119">Affected APIs</span></span>

<span data-ttu-id="b00d3-120">None</span><span class="sxs-lookup"><span data-stu-id="b00d3-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
