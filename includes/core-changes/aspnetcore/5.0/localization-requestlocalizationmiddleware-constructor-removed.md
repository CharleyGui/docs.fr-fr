---
ms.openlocfilehash: db941229e02064ee856829417d6762aa17b0b926
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309143"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="30123-101">Localisation : le constructeur obsolète a été supprimé de l’intergiciel (middleware) de localisation des demandes</span><span class="sxs-lookup"><span data-stu-id="30123-101">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="30123-102">Le <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructeur qui ne dispose pas d’un <xref:Microsoft.Extensions.Logging.ILoggerFactory> paramètre a été marqué comme obsolète [dans cette validation](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span><span class="sxs-lookup"><span data-stu-id="30123-102">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="30123-103">Dans ASP.NET Core 5,0, le constructeur obsolète a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="30123-103">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="30123-104">Pour plus d’informations, consultez [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).</span><span class="sxs-lookup"><span data-stu-id="30123-104">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="30123-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="30123-105">Version introduced</span></span>

<span data-ttu-id="30123-106">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="30123-106">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="30123-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="30123-107">Old behavior</span></span>

<span data-ttu-id="30123-108">Le `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructeur obsolète existe.</span><span class="sxs-lookup"><span data-stu-id="30123-108">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="30123-109">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="30123-109">New behavior</span></span>

<span data-ttu-id="30123-110">Le `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructeur obsolète n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="30123-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="30123-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="30123-111">Reason for change</span></span>

<span data-ttu-id="30123-112">Cette modification permet de s’assurer que l’intergiciel (middleware) de localisation des demandes a toujours accès à un enregistreur d’événements.</span><span class="sxs-lookup"><span data-stu-id="30123-112">This change ensures that the request localization middleware always has access to a logger.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="30123-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="30123-113">Recommended action</span></span>

<span data-ttu-id="30123-114">Lors de la construction manuelle d’une instance de `RequestLocalizationMiddleware` , passer une `ILoggerFactory` instance dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="30123-114">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="30123-115">Si une `ILoggerFactory` instance valide n’est pas disponible dans ce contexte, envisagez de passer le constructeur d’intergiciel (middleware) à une <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span><span class="sxs-lookup"><span data-stu-id="30123-115">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

#### <a name="category"></a><span data-ttu-id="30123-116">Category</span><span class="sxs-lookup"><span data-stu-id="30123-116">Category</span></span>

<span data-ttu-id="30123-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="30123-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="30123-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="30123-118">Affected APIs</span></span>

[<span data-ttu-id="30123-119">RequestLocalizationMiddleware. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )</span><span class="sxs-lookup"><span data-stu-id="30123-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
