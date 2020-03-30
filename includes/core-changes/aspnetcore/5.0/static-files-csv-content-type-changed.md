---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391180"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a><span data-ttu-id="da525-101">Fichiers statiques : type de contenu CSV modifié pour être conforme aux normes</span><span class="sxs-lookup"><span data-stu-id="da525-101">Static files: CSV content type changed to standards-compliant</span></span>

<span data-ttu-id="da525-102">Dans ASP.NET Core 5.0, la `Content-Type` valeur d’en-tête de réponse par défaut que le Static File `text/csv` [Middleware](/aspnet/core/fundamentals/static-files) utilise pour les fichiers *.csv* a changé pour la valeur conforme aux normes .</span><span class="sxs-lookup"><span data-stu-id="da525-102">In ASP.NET Core 5.0, the default `Content-Type` response header value that the [Static File Middleware](/aspnet/core/fundamentals/static-files) uses for *.csv* files has changed to the standards-compliant value `text/csv`.</span></span>

<span data-ttu-id="da525-103">Pour discussion sur cette question, voir [dotnet/aspnetcore 17385](https://github.com/dotnet/AspNetCore/issues/17385).</span><span class="sxs-lookup"><span data-stu-id="da525-103">For discussion on this issue, see [dotnet/aspnetcore#17385](https://github.com/dotnet/AspNetCore/issues/17385).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da525-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="da525-104">Version introduced</span></span>

<span data-ttu-id="da525-105">5.0 Aperçu 1</span><span class="sxs-lookup"><span data-stu-id="da525-105">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="da525-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="da525-106">Old behavior</span></span>

<span data-ttu-id="da525-107">La `Content-Type` valeur `application/octet-stream` de l’en-tête a été utilisée.</span><span class="sxs-lookup"><span data-stu-id="da525-107">The `Content-Type` header value `application/octet-stream` was used.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="da525-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="da525-108">New behavior</span></span>

<span data-ttu-id="da525-109">La `Content-Type` valeur `text/csv` de l’en-tête est utilisée.</span><span class="sxs-lookup"><span data-stu-id="da525-109">The `Content-Type` header value `text/csv` is used.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="da525-110">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="da525-110">Reason for change</span></span>

<span data-ttu-id="da525-111">Conformité à la norme [RFC 7111.](https://tools.ietf.org/html/rfc7111#section-5.1)</span><span class="sxs-lookup"><span data-stu-id="da525-111">Compliance with the [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) standard.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da525-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="da525-112">Recommended action</span></span>

<span data-ttu-id="da525-113">Si cette modification a un impact sur votre application, vous pouvez personnaliser la cartographie de type extension de fichier à MIME.</span><span class="sxs-lookup"><span data-stu-id="da525-113">If this change impacts your app, you can customize the file extension-to-MIME type mapping.</span></span> <span data-ttu-id="da525-114">Pour revenir `application/octet-stream` au type MIME, modifiez la <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> méthode `Startup.Configure`appelez.</span><span class="sxs-lookup"><span data-stu-id="da525-114">To revert to the `application/octet-stream` MIME type, modify the <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> method call in `Startup.Configure`.</span></span> <span data-ttu-id="da525-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="da525-115">For example:</span></span>

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

<span data-ttu-id="da525-116">Pour plus d’informations sur la personnalisation de la cartographie, voir [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span><span class="sxs-lookup"><span data-stu-id="da525-116">For more information on customizing the mapping, see [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).</span></span>

#### <a name="category"></a><span data-ttu-id="da525-117">Category</span><span class="sxs-lookup"><span data-stu-id="da525-117">Category</span></span>

<span data-ttu-id="da525-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="da525-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da525-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="da525-119">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
