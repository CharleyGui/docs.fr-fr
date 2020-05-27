---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391180"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="5b948-101">Fichiers statiques : le type de contenu CSV est passé à conforme aux normes</span><span class="sxs-lookup"><span data-stu-id="5b948-101">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="5b948-102">Dans ASP.NET Core 5,0, la `Content-Type` valeur d’en-tête de réponse par défaut utilisée par l’intergiciel de fichiers [statiques](/aspnet/core/fundamentals/static-files) pour les fichiers *. csv* est passée à la valeur conforme aux normes `text/csv` .</span><span class="sxs-lookup"><span data-stu-id="5b948-102">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="5b948-103">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="5b948-103">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5b948-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5b948-104">Version introduced</span></span>

<span data-ttu-id="5b948-105">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="5b948-105">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5b948-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="5b948-106">Old behavior</span></span>

<span data-ttu-id="5b948-107">La `Content-Type` valeur d’en-tête `application/octet-stream` a été utilisée.</span><span class="sxs-lookup"><span data-stu-id="5b948-107">The `Content-Type` header value `application/octet-stream` was used.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5b948-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="5b948-108">New behavior</span></span>

<span data-ttu-id="5b948-109">La `Content-Type` valeur d’en-tête `text/csv` est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5b948-109">The `Content-Type` header value `text/csv` is used.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5b948-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="5b948-110">Reason for change</span></span>

<span data-ttu-id="5b948-111">Conformité avec la norme [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) .</span><span class="sxs-lookup"><span data-stu-id="5b948-111">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5b948-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5b948-112">Recommended action</span></span>

<span data-ttu-id="5b948-113">Si cette modification a un impact sur votre application, vous pouvez personnaliser le mappage de type extension de fichier en MIME.</span><span class="sxs-lookup"><span data-stu-id="5b948-113">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="5b948-114">Pour rétablir le `application/octet-stream` type MIME, modifiez l' <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> appel de méthode dans `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="5b948-114">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="5b948-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="5b948-115">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="5b948-116">Pour plus d’informations sur la personnalisation du mappage, consultez [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="5b948-116">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

#### <a name="category"></a><span data-ttu-id="5b948-117">Category</span><span class="sxs-lookup"><span data-stu-id="5b948-117">Category</span></span>

<span data-ttu-id="5b948-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5b948-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5b948-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="5b948-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
