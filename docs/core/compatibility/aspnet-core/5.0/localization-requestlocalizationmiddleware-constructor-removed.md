---
title: 'Modification avec rupture : localisation : le constructeur obsolète a été supprimé de l’intergiciel (middleware) de localisation des demandes'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 de localisation : le constructeur obsolète a été supprimé de l’intergiciel (middleware) de localisation des demandes'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 53dd0f25078dae140d34d6d21d66983f78b8bdb0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761195"
---
# <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="78fcf-103">Localisation : le constructeur obsolète a été supprimé de l’intergiciel (middleware) de localisation des demandes</span><span class="sxs-lookup"><span data-stu-id="78fcf-103">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="78fcf-104">Le <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructeur qui ne dispose pas d’un <xref:Microsoft.Extensions.Logging.ILoggerFactory> paramètre a été marqué comme obsolète [dans cette validation](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span><span class="sxs-lookup"><span data-stu-id="78fcf-104">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="78fcf-105">Dans ASP.NET Core 5,0, le constructeur obsolète a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="78fcf-105">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="78fcf-106">Pour plus d’informations, consultez [dotnet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).</span><span class="sxs-lookup"><span data-stu-id="78fcf-106">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="78fcf-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="78fcf-107">Version introduced</span></span>

<span data-ttu-id="78fcf-108">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="78fcf-108">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="78fcf-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="78fcf-109">Old behavior</span></span>

<span data-ttu-id="78fcf-110">Le `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructeur obsolète existe.</span><span class="sxs-lookup"><span data-stu-id="78fcf-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="78fcf-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="78fcf-111">New behavior</span></span>

<span data-ttu-id="78fcf-112">Le `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructeur obsolète n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="78fcf-112">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="78fcf-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="78fcf-113">Reason for change</span></span>

<span data-ttu-id="78fcf-114">Cette modification permet de s’assurer que l’intergiciel (middleware) de localisation des demandes a toujours accès à un enregistreur d’événements.</span><span class="sxs-lookup"><span data-stu-id="78fcf-114">This change ensures that the request localization middleware always has access to a logger.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="78fcf-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="78fcf-115">Recommended action</span></span>

<span data-ttu-id="78fcf-116">Lors de la construction manuelle d’une instance de `RequestLocalizationMiddleware` , passer une `ILoggerFactory` instance dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="78fcf-116">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="78fcf-117">Si une `ILoggerFactory` instance valide n’est pas disponible dans ce contexte, envisagez de passer le constructeur d’intergiciel (middleware) à une <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span><span class="sxs-lookup"><span data-stu-id="78fcf-117">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="78fcf-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="78fcf-118">Affected APIs</span></span>

[<span data-ttu-id="78fcf-119">RequestLocalizationMiddleware. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )</span><span class="sxs-lookup"><span data-stu-id="78fcf-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

### Category

ASP.NET Core

### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
