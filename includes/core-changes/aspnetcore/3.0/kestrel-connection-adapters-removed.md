---
ms.openlocfilehash: 06d5f48566c239e37355496c3f27163d952602c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901664"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="eca21-101">Kestrel: adaptateurs de connexion supprimés</span><span class="sxs-lookup"><span data-stu-id="eca21-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="eca21-102">Dans le cadre du mouvement des API `public`"pubtérinaires" à , le concept d’un `IConnectionAdapter` a été retiré de Kestrel.</span><span class="sxs-lookup"><span data-stu-id="eca21-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="eca21-103">Les adaptateurs de connexion sont remplacés par des middleware de connexion (semblable à HTTP middleware dans le pipeline ASP.NET Core, mais pour les connexions de niveau inférieur).</span><span class="sxs-lookup"><span data-stu-id="eca21-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="eca21-104">HTTPS et l’enregistrement de connexion sont passés des adaptateurs de connexion à la connexion middleware.</span><span class="sxs-lookup"><span data-stu-id="eca21-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="eca21-105">Ces méthodes d’extension devraient continuer à fonctionner de manière transparente, mais les détails de la mise en œuvre ont changé.</span><span class="sxs-lookup"><span data-stu-id="eca21-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="eca21-106">Pour plus d’informations, voir [dotnet/aspnetcore 11412](https://github.com/dotnet/aspnetcore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="eca21-106">For more information, see [dotnet/aspnetcore#11412](https://github.com/dotnet/aspnetcore/pull/11412).</span></span> <span data-ttu-id="eca21-107">Pour discussion, voir [dotnet/aspnetcore 11475](https://github.com/dotnet/aspnetcore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="eca21-107">For discussion, see [dotnet/aspnetcore#11475](https://github.com/dotnet/aspnetcore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="eca21-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="eca21-108">Version introduced</span></span>

<span data-ttu-id="eca21-109">3.0</span><span class="sxs-lookup"><span data-stu-id="eca21-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="eca21-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="eca21-110">Old behavior</span></span>

<span data-ttu-id="eca21-111">Kestrel extensibility composants ont `IConnectionAdapter`été créés en utilisant .</span><span class="sxs-lookup"><span data-stu-id="eca21-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="eca21-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="eca21-112">New behavior</span></span>

<span data-ttu-id="eca21-113">Kestrel extensibility composants sont créés comme [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="eca21-113">Kestrel extensibility components are created as [middleware](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="eca21-114">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="eca21-114">Reason for change</span></span>

<span data-ttu-id="eca21-115">Ce changement vise à fournir une architecture d’extéponsabilité plus flexible.</span><span class="sxs-lookup"><span data-stu-id="eca21-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="eca21-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="eca21-116">Recommended action</span></span>

<span data-ttu-id="eca21-117">Convertir toutes les `IConnectionAdapter` implémentations de pour utiliser le nouveau modèle middleware comme indiqué [ici](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="eca21-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/dotnet/aspnetcore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="eca21-118">Category</span><span class="sxs-lookup"><span data-stu-id="eca21-118">Category</span></span>

<span data-ttu-id="eca21-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="eca21-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eca21-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="eca21-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
