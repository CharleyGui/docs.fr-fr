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
# <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>Fichiers statiques : le type de contenu CSV est passé à conforme aux normes

Dans ASP.NET Core 5,0, la `Content-Type` valeur d’en-tête de réponse par défaut utilisée par l’intergiciel de fichiers [statiques](/aspnet/core/fundamentals/static-files) pour les fichiers *. csv* est passée à la valeur conforme aux normes `text/csv` .

Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 17385](https://github.com/dotnet/AspNetCore/issues/17385).

## <a name="version-introduced"></a>Version introduite

5,0 Preview 1

## <a name="old-behavior"></a>Ancien comportement

La `Content-Type` valeur d’en-tête `application/octet-stream` a été utilisée.

## <a name="new-behavior"></a>Nouveau comportement

La `Content-Type` valeur d’en-tête `text/csv` est utilisée.

## <a name="reason-for-change"></a>Motif de modification

Conformité avec la norme [RFC 7111](https://tools.ietf.org/html/rfc7111#section-5.1) .

## <a name="recommended-action"></a>Action recommandée

Si cette modification a un impact sur votre application, vous pouvez personnaliser le mappage de type extension de fichier en MIME. Pour rétablir le `application/octet-stream` type MIME, modifiez l' <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> appel de méthode dans `Startup.Configure` . Par exemple :

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

Pour plus d’informations sur la personnalisation du mappage, consultez [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).

## <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
