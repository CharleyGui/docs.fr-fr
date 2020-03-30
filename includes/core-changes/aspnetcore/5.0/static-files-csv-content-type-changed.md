---
ms.openlocfilehash: 8e077d5cde6e824af5aac3742308593f1d91dd92
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391180"
---
### <a name="static-files-csv-content-type-changed-to-standards-compliant"></a>Fichiers statiques : type de contenu CSV modifié pour être conforme aux normes

Dans ASP.NET Core 5.0, la `Content-Type` valeur d’en-tête de réponse par défaut que le Static File `text/csv` [Middleware](/aspnet/core/fundamentals/static-files) utilise pour les fichiers *.csv* a changé pour la valeur conforme aux normes .

Pour discussion sur cette question, voir [dotnet/aspnetcore 17385](https://github.com/dotnet/AspNetCore/issues/17385).

#### <a name="version-introduced"></a>Version introduite

5.0 Aperçu 1

#### <a name="old-behavior"></a>Ancien comportement

La `Content-Type` valeur `application/octet-stream` de l’en-tête a été utilisée.

#### <a name="new-behavior"></a>Nouveau comportement

La `Content-Type` valeur `text/csv` de l’en-tête est utilisée.

#### <a name="reason-for-change"></a>Raison du changement

Conformité à la norme [RFC 7111.](https://tools.ietf.org/html/rfc7111#section-5.1)

#### <a name="recommended-action"></a>Action recommandée

Si cette modification a un impact sur votre application, vous pouvez personnaliser la cartographie de type extension de fichier à MIME. Pour revenir `application/octet-stream` au type MIME, modifiez la <xref:Microsoft.AspNetCore.Builder.StaticFileExtensions.UseStaticFiles%2A> méthode `Startup.Configure`appelez. Par exemple :

```csharp
var provider = new FileExtensionContentTypeProvider();
provider.Mappings[".csv"] = MediaTypeNames.Application.Octet;

app.UseStaticFiles(new StaticFileOptions
{
    ContentTypeProvider = provider
});
```

Pour plus d’informations sur la personnalisation de la cartographie, voir [FileExtensionContentTypeProvider](/aspnet/core/fundamentals/static-files#fileextensioncontenttypeprovider).

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.StaticFiles.FileExtensionContentTypeProvider`

-->
