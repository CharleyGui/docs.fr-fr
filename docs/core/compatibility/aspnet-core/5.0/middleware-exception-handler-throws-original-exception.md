---
title: 'Modification avec rupture : intergiciel : l’intergiciel (middleware) du gestionnaire d’exceptions lève une exception d’origine si le gestionnaire est introuvable'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé intergiciel : l’intergiciel (middleware) du gestionnaire d’exceptions lève une exception d’origine si le gestionnaire est introuvable'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 8801d3e6950d66fd9f24e051fd8729c50eb0b282
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761214"
---
# <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a><span data-ttu-id="e35a4-103">Intergiciel : l’intergiciel (middleware) du gestionnaire d’exceptions lève une exception d’origine si le gestionnaire est introuvable</span><span class="sxs-lookup"><span data-stu-id="e35a4-103">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>

<span data-ttu-id="e35a4-104">Avant le ASP.NET Core 5,0, l’intergiciel (middleware) du [Gestionnaire d’exceptions](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) exécute le gestionnaire d’exceptions configuré quand une exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e35a4-104">Before ASP.NET Core 5.0, the [Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executes the configured exception handler when an exception has occurred.</span></span> <span data-ttu-id="e35a4-105">Si le gestionnaire d’exceptions, configuré via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> , est introuvable, une réponse HTTP 404 est générée.</span><span class="sxs-lookup"><span data-stu-id="e35a4-105">If the exception handler, configured via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, can't be found, an HTTP 404 response is produced.</span></span> <span data-ttu-id="e35a4-106">La réponse est trompeuse en ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="e35a4-106">The response is misleading in that it:</span></span>

* <span data-ttu-id="e35a4-107">Semble être une erreur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e35a4-107">Seems to be a user error.</span></span>
* <span data-ttu-id="e35a4-108">Masque le fait qu’une exception s’est produite sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="e35a4-108">Obscures the fact that an exception occurred on the server.</span></span>

<span data-ttu-id="e35a4-109">Pour résoudre l’erreur trompeuse dans ASP.NET Core 5,0, le `ExceptionHandlerMiddleware` lève l’exception d’origine si le gestionnaire d’exceptions est introuvable.</span><span class="sxs-lookup"><span data-stu-id="e35a4-109">To address the misleading error in ASP.NET Core 5.0, the `ExceptionHandlerMiddleware` throws the original exception if the exception handler can't be found.</span></span> <span data-ttu-id="e35a4-110">Par conséquent, une réponse HTTP 500 est générée par le serveur.</span><span class="sxs-lookup"><span data-stu-id="e35a4-110">As a result, an HTTP 500 response is produced by the server.</span></span> <span data-ttu-id="e35a4-111">La réponse sera plus facile à examiner dans les journaux du serveur lors du débogage de l’erreur qui s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e35a4-111">The response will be easier to examine in the server logs when debugging the error that occurred.</span></span>

<span data-ttu-id="e35a4-112">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288).</span><span class="sxs-lookup"><span data-stu-id="e35a4-112">For discussion, see GitHub issue [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e35a4-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e35a4-113">Version introduced</span></span>

<span data-ttu-id="e35a4-114">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="e35a4-114">5.0 RC 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="e35a4-115">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="e35a4-115">Old behavior</span></span>

<span data-ttu-id="e35a4-116">L’intergiciel (middleware) du gestionnaire d’exceptions génère une réponse HTTP 404 si le gestionnaire d’exceptions configuré est introuvable.</span><span class="sxs-lookup"><span data-stu-id="e35a4-116">The Exception Handler Middleware produces an HTTP 404 response if the configured exception handler can't be found.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="e35a4-117">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="e35a4-117">New behavior</span></span>

<span data-ttu-id="e35a4-118">L’intergiciel (middleware) du gestionnaire d’exceptions lève l’exception d’origine si le gestionnaire d’exceptions configuré est introuvable.</span><span class="sxs-lookup"><span data-stu-id="e35a4-118">The Exception Handler Middleware throws the original exception if the configured exception handler can't be found.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e35a4-119">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="e35a4-119">Reason for change</span></span>

<span data-ttu-id="e35a4-120">L’erreur HTTP 404 ne fait pas de évidente qu’une exception s’est produite sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="e35a4-120">The HTTP 404 error doesn't make it obvious that an exception occurred on the server.</span></span> <span data-ttu-id="e35a4-121">Cette modification génère une erreur HTTP 500 pour le rendre évident :</span><span class="sxs-lookup"><span data-stu-id="e35a4-121">This change produces an HTTP 500 error to make it obvious that:</span></span>

* <span data-ttu-id="e35a4-122">Le problème n’est pas dû à une erreur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e35a4-122">The problem isn't caused by a user error.</span></span>
* <span data-ttu-id="e35a4-123">Une exception a été rencontrée sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="e35a4-123">An exception was encountered on the server.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e35a4-124">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e35a4-124">Recommended action</span></span>

<span data-ttu-id="e35a4-125">Il n’y a aucune modification de l’API.</span><span class="sxs-lookup"><span data-stu-id="e35a4-125">There are no API changes.</span></span> <span data-ttu-id="e35a4-126">Toutes les applications existantes continueront à se compiler et à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="e35a4-126">All existing apps will continue to compile and run.</span></span> <span data-ttu-id="e35a4-127">L’exception levée est gérée par le serveur.</span><span class="sxs-lookup"><span data-stu-id="e35a4-127">The exception thrown is handled by the server.</span></span> <span data-ttu-id="e35a4-128">Par exemple, l’exception est convertie en réponse d’erreur HTTP 500 par [Kestrel](/aspnet/core/fundamentals/servers/kestrel) ou [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span><span class="sxs-lookup"><span data-stu-id="e35a4-128">For example, the exception is converted to an HTTP 500 error response by [Kestrel](/aspnet/core/fundamentals/servers/kestrel) or [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e35a4-129">API affectées</span><span class="sxs-lookup"><span data-stu-id="e35a4-129">Affected APIs</span></span>

<span data-ttu-id="e35a4-130">None</span><span class="sxs-lookup"><span data-stu-id="e35a4-130">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
