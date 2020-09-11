---
ms.openlocfilehash: 26e521a86b504824f035ad5d40e4a04d2ea26abc
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022963"
---
### <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a><span data-ttu-id="992da-101">Intergiciel : l’intergiciel (middleware) du gestionnaire d’exceptions lève une exception d’origine si le gestionnaire est introuvable</span><span class="sxs-lookup"><span data-stu-id="992da-101">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>

<span data-ttu-id="992da-102">Avant le ASP.NET Core 5,0, l’intergiciel (middleware) du [Gestionnaire d’exceptions](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) exécute le gestionnaire d’exceptions configuré quand une exception s’est produite.</span><span class="sxs-lookup"><span data-stu-id="992da-102">Before ASP.NET Core 5.0, the [Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executes the configured exception handler when an exception has occurred.</span></span> <span data-ttu-id="992da-103">Si le gestionnaire d’exceptions, configuré via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> , est introuvable, une réponse HTTP 404 est générée.</span><span class="sxs-lookup"><span data-stu-id="992da-103">If the exception handler, configured via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, can't be found, an HTTP 404 response is produced.</span></span> <span data-ttu-id="992da-104">La réponse est trompeuse en ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="992da-104">The response is misleading in that it:</span></span>

* <span data-ttu-id="992da-105">Semble être une erreur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="992da-105">Seems to be a user error.</span></span>
* <span data-ttu-id="992da-106">Masque le fait qu’une exception s’est produite sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="992da-106">Obscures the fact that an exception occurred on the server.</span></span>

<span data-ttu-id="992da-107">Pour résoudre l’erreur trompeuse dans ASP.NET Core 5,0, le `ExceptionHandlerMiddleware` lève l’exception d’origine si le gestionnaire d’exceptions est introuvable.</span><span class="sxs-lookup"><span data-stu-id="992da-107">To address the misleading error in ASP.NET Core 5.0, the `ExceptionHandlerMiddleware` throws the original exception if the exception handler can't be found.</span></span> <span data-ttu-id="992da-108">Par conséquent, une réponse HTTP 500 est générée par le serveur.</span><span class="sxs-lookup"><span data-stu-id="992da-108">As a result, an HTTP 500 response is produced by the server.</span></span> <span data-ttu-id="992da-109">La réponse sera plus facile à examiner dans les journaux du serveur lors du débogage de l’erreur qui s’est produite.</span><span class="sxs-lookup"><span data-stu-id="992da-109">The response will be easier to examine in the server logs when debugging the error that occurred.</span></span>

<span data-ttu-id="992da-110">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288).</span><span class="sxs-lookup"><span data-stu-id="992da-110">For discussion, see GitHub issue [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="992da-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="992da-111">Version introduced</span></span>

<span data-ttu-id="992da-112">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="992da-112">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="992da-113">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="992da-113">Old behavior</span></span>

<span data-ttu-id="992da-114">L’intergiciel (middleware) du gestionnaire d’exceptions génère une réponse HTTP 404 si le gestionnaire d’exceptions configuré est introuvable.</span><span class="sxs-lookup"><span data-stu-id="992da-114">The Exception Handler Middleware produces an HTTP 404 response if the configured exception handler can't be found.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="992da-115">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="992da-115">New behavior</span></span>

<span data-ttu-id="992da-116">L’intergiciel (middleware) du gestionnaire d’exceptions lève l’exception d’origine si le gestionnaire d’exceptions configuré est introuvable.</span><span class="sxs-lookup"><span data-stu-id="992da-116">The Exception Handler Middleware throws the original exception if the configured exception handler can't be found.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="992da-117">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="992da-117">Reason for change</span></span>

<span data-ttu-id="992da-118">L’erreur HTTP 404 ne fait pas de évidente qu’une exception s’est produite sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="992da-118">The HTTP 404 error doesn't make it obvious that an exception occurred on the server.</span></span> <span data-ttu-id="992da-119">Cette modification génère une erreur HTTP 500 pour le rendre évident :</span><span class="sxs-lookup"><span data-stu-id="992da-119">This change produces an HTTP 500 error to make it obvious that:</span></span>

* <span data-ttu-id="992da-120">Le problème n’est pas dû à une erreur de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="992da-120">The problem isn't caused by a user error.</span></span>
* <span data-ttu-id="992da-121">Une exception a été rencontrée sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="992da-121">An exception was encountered on the server.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="992da-122">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="992da-122">Recommended action</span></span>

<span data-ttu-id="992da-123">Il n’y a aucune modification de l’API.</span><span class="sxs-lookup"><span data-stu-id="992da-123">There are no API changes.</span></span> <span data-ttu-id="992da-124">Toutes les applications existantes continueront à se compiler et à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="992da-124">All existing apps will continue to compile and run.</span></span> <span data-ttu-id="992da-125">L’exception levée est gérée par le serveur.</span><span class="sxs-lookup"><span data-stu-id="992da-125">The exception thrown is handled by the server.</span></span> <span data-ttu-id="992da-126">Par exemple, l’exception est convertie en réponse d’erreur HTTP 500 par [Kestrel](/aspnet/core/fundamentals/servers/kestrel) ou [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span><span class="sxs-lookup"><span data-stu-id="992da-126">For example, the exception is converted to an HTTP 500 error response by [Kestrel](/aspnet/core/fundamentals/servers/kestrel) or [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span></span>

#### <a name="category"></a><span data-ttu-id="992da-127">Category</span><span class="sxs-lookup"><span data-stu-id="992da-127">Category</span></span>

<span data-ttu-id="992da-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="992da-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="992da-129">API affectées</span><span class="sxs-lookup"><span data-stu-id="992da-129">Affected APIs</span></span>

<span data-ttu-id="992da-130">Aucun</span><span class="sxs-lookup"><span data-stu-id="992da-130">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
