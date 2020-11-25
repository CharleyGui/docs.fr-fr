---
title: 'Modification avec rupture : fichiers statiques : le type de contenu CSV est passé à conforme aux normes'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 titres de fichiers statiques : le type de contenu CSV est passé à conforme aux normes'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c94a0cf213970d20559b7c061d8be220b43961e0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761292"
---
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="ca586-103">Fichiers statiques : le type de contenu CSV est passé à conforme aux normes</span><span class="sxs-lookup"><span data-stu-id="ca586-103">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="ca586-104">Dans ASP.NET Core 5,0, la `Content-Type` valeur d’en-tête de réponse par défaut utilisée par l’intergiciel de fichiers [statiques](/aspnet/core/fundamentals/static-files) pour les fichiers *. csv* est passée à la valeur conforme aux normes `text/csv` .</span><span class="sxs-lookup"><span data-stu-id="ca586-104">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="ca586-105">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="ca586-105">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="ca586-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="ca586-106">Version introduced</span></span>

<span data-ttu-id="ca586-107">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="ca586-107">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="ca586-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="ca586-108">Old behavior</span></span>

<span data-ttu-id="ca586-109">La `Content-Type` valeur d’en-tête `application/octet-stream` a été utilisée.</span><span class="sxs-lookup"><span data-stu-id="ca586-109">The `Content-Type` header value `application/octet-stream` was used.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="ca586-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="ca586-110">New behavior</span></span>

<span data-ttu-id="ca586-111">La `Content-Type` valeur d’en-tête `text/csv` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="ca586-111">The `Content-Type` header value `text/csv` is used.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="ca586-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="ca586-112">Reason for change</span></span>

<span data-ttu-id="ca586-113">Conformité avec la norme [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) .</span><span class="sxs-lookup"><span data-stu-id="ca586-113">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="ca586-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="ca586-114">Recommended action</span></span>

<span data-ttu-id="ca586-115">Si cette modification a un impact sur votre application, vous pouvez personnaliser le mappage de type extension de fichier en MIME.</span><span class="sxs-lookup"><span data-stu-id="ca586-115">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="ca586-116">Pour rétablir le `application/octet-stream` type MIME, modifiez l' <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> appel de méthode dans `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="ca586-116">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="ca586-117">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="ca586-117">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="ca586-118">Pour plus d’informations sur la personnalisation du mappage, consultez [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="ca586-118">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="ca586-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="ca586-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
