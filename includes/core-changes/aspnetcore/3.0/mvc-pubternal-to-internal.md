---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901591"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC: "Pubternal" types changés à interne

Dans ASP.NET Core 3.0, tous les types de « pubternal `public` » dans MVC `internal` ont été mis à jour pour être soit dans un espace de nom pris en charge ou, le cas échéant.

#### <a name="change-description"></a>Description de la modification

Dans ASP.NET Core, les types "pubternal" `public` sont déclarés comme étant sauf dans un `.Internal`espace noméxé. Bien que `public`ces types sont , ils n’ont pas de politique de soutien et sont sujets à des changements de rupture. Malheureusement, l’utilisation accidentelle de ces types a été courante, ce qui a entraîné la rupture des changements à ces projets et la limitation de la capacité de maintenir le cadre.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Certains types dans `public` MVC `.Internal` étaient, mais dans un namespace. Ces types n’avaient pas de politique de soutien et étaient susceptibles de modifier en cassant.

#### <a name="new-behavior"></a>Nouveau comportement

Tous ces types sont `public` mis à jour soit `internal`pour être dans un namespace pris en charge ou marqué comme .

#### <a name="reason-for-change"></a>Raison du changement

L’utilisation accidentelle des types « pubtérinaux » a été courante, ce qui a entraîné la rupture des changements à ces projets et la limitation de la capacité de maintenir le cadre.

#### <a name="recommended-action"></a>Action recommandée

Si vous utilisez des types `public` qui sont devenus vraiment et ont été déplacés dans un nouvel espace de nom pris en charge, mettez à jour vos références pour correspondre aux nouveaux espaces de nom.

Si vous utilisez des types qui `internal`sont devenus marqués comme , vous aurez besoin de trouver une alternative. Les types auparavant «pubternal» n’ont jamais été pris en charge pour un usage public. S’il existe des types spécifiques dans ces espaces nominaux qui sont essentiels à vos applications, déposez un problème à [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues). Des considérations peuvent être prises `public`pour faire les types demandés .

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Ce changement inclut les types dans les espaces nominaux suivants :

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
