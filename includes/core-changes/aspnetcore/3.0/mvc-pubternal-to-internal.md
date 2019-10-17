---
ms.openlocfilehash: 09fd95ba5f3aee59f2abdfbb4e64eb6202e2b873
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394024"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a>MVC : les types « Pubternal » sont devenus internes

Dans ASP.NET Core 3,0, tous les types « pubternal » dans MVC ont été mis à jour pour être `public` dans un espace de noms pris en charge ou `internal`, le cas échéant.

#### <a name="change-description"></a>Modifier la description

Dans ASP.NET Core, les types « pubternal » sont déclarés comme `public`, mais ils résident dans un espace de noms @no__t avec suffixe 1. Bien que ces types soient `public`, ils n’ont aucune stratégie de prise en charge et sont soumis à des modifications avec rupture. Malheureusement, l’utilisation accidentelle de ces types est courante, entraînant des modifications avec rupture de ces projets et limitant la capacité à gérer l’infrastructure.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Certains types dans MVC étaient `public`, mais dans un espace de noms `.Internal`. Ces types n’ont pas de stratégie de prise en charge et ont fait l’objet de modifications avec rupture.

#### <a name="new-behavior"></a>Nouveau comportement

Tous ces types sont mis à jour pour être `public` dans un espace de noms pris en charge ou marqués comme `internal`.

#### <a name="reason-for-change"></a>Motif de modification

L’utilisation accidentelle des types « pubternal » a été courante, entraînant des modifications avec rupture de ces projets et limitant la capacité à gérer l’infrastructure.

#### <a name="recommended-action"></a>Action recommandée

Si vous utilisez des types qui sont réellement `public` et qui ont été déplacés dans un nouvel espace de noms pris en charge, mettez à jour vos références pour qu’elles correspondent aux nouveaux espaces de noms.

Si vous utilisez des types qui ont été marqués comme `internal`, vous devez trouver une alternative. Les types « pubternal » précédemment n’étaient jamais pris en charge pour une utilisation publique. S’il existe des types spécifiques dans ces espaces de noms qui sont essentiels à vos applications, émettez un problème au niveau de [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues). Des considérations peuvent être prises pour effectuer les types demandés `public`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Cette modification comprend des types dans les espaces de noms suivants :

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
