---
ms.openlocfilehash: a916af91670dc9c5ceb2ff759cd8ae308fb2c2dc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394175"
---
### <a name="kestrel-connection-adapters-removed"></a><span data-ttu-id="25f3d-101">Kestrel : adaptateurs de connexion supprimés</span><span class="sxs-lookup"><span data-stu-id="25f3d-101">Kestrel: Connection adapters removed</span></span>

<span data-ttu-id="25f3d-102">Dans le cadre du déplacement pour déplacer les API « pubternal » vers `public`, le concept d’une `IConnectionAdapter` a été supprimé de Kestrel.</span><span class="sxs-lookup"><span data-stu-id="25f3d-102">As part of the move to move "pubternal" APIs to `public`, the concept of an `IConnectionAdapter` was removed from Kestrel.</span></span> <span data-ttu-id="25f3d-103">Les adaptateurs de connexion sont remplacés par un intergiciel de connexion (similaire à l’intergiciel HTTP dans le pipeline ASP.NET Core, mais pour les connexions de niveau inférieur).</span><span class="sxs-lookup"><span data-stu-id="25f3d-103">Connection adapters are being replaced with connection middleware (similar to HTTP middleware in the ASP.NET Core pipeline, but for lower-level connections).</span></span> <span data-ttu-id="25f3d-104">HTTPs et la journalisation des connexions ont été déplacées des adaptateurs de connexion vers l’intergiciel de connexion.</span><span class="sxs-lookup"><span data-stu-id="25f3d-104">HTTPS and connection logging have moved from connection adapters to connection middleware.</span></span> <span data-ttu-id="25f3d-105">Ces méthodes d’extension doivent continuer à fonctionner de manière transparente, mais les détails de l’implémentation ont changé.</span><span class="sxs-lookup"><span data-stu-id="25f3d-105">Those extension methods should continue to work seamlessly, but the implementation details have changed.</span></span>

<span data-ttu-id="25f3d-106">Pour plus d’informations, consultez [ASPNET/AspNetCore # 11412](https://github.com/aspnet/AspNetCore/pull/11412).</span><span class="sxs-lookup"><span data-stu-id="25f3d-106">For more information, see [aspnet/AspNetCore#11412](https://github.com/aspnet/AspNetCore/pull/11412).</span></span> <span data-ttu-id="25f3d-107">Pour plus d’informations, consultez [ASPNET/AspNetCore # 11475](https://github.com/aspnet/AspNetCore/issues/11475).</span><span class="sxs-lookup"><span data-stu-id="25f3d-107">For discussion, see [aspnet/AspNetCore#11475](https://github.com/aspnet/AspNetCore/issues/11475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="25f3d-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="25f3d-108">Version introduced</span></span>

<span data-ttu-id="25f3d-109">3,0</span><span class="sxs-lookup"><span data-stu-id="25f3d-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="25f3d-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="25f3d-110">Old behavior</span></span>

<span data-ttu-id="25f3d-111">Les composants d’extensibilité de Kestrel ont été créés à l’aide de `IConnectionAdapter`.</span><span class="sxs-lookup"><span data-stu-id="25f3d-111">Kestrel extensibility components were created using `IConnectionAdapter`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="25f3d-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="25f3d-112">New behavior</span></span>

<span data-ttu-id="25f3d-113">Les composants d’extensibilité Kestrel sont créés en tant que [middleware](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="25f3d-113">Kestrel extensibility components are created as [middleware](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="25f3d-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="25f3d-114">Reason for change</span></span>

<span data-ttu-id="25f3d-115">Cette modification vise à fournir une architecture d’extensibilité plus flexible.</span><span class="sxs-lookup"><span data-stu-id="25f3d-115">This change is intended to provide a more flexible extensibility architecture.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="25f3d-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="25f3d-116">Recommended action</span></span>

<span data-ttu-id="25f3d-117">Convertissez toutes les implémentations de `IConnectionAdapter` pour utiliser le nouveau modèle d’intergiciel (middleware) comme indiqué [ici](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span><span class="sxs-lookup"><span data-stu-id="25f3d-117">Convert any implementations of `IConnectionAdapter` to use the new middleware pattern as shown [here](https://github.com/aspnet/AspNetCore/pull/11412/files#diff-89acc06acf1b2e96bbdb811ce523619f).</span></span>

#### <a name="category"></a><span data-ttu-id="25f3d-118">Category</span><span class="sxs-lookup"><span data-stu-id="25f3d-118">Category</span></span>

<span data-ttu-id="25f3d-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="25f3d-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="25f3d-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="25f3d-120">Affected APIs</span></span>

`Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal.IConnectionAdapter`

-->
