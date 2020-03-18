---
ms.openlocfilehash: f6fd75c5b49156f44d31c650ea452eb549f13b0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901962"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC: JsonResult a déménagé à Microsoft.AspNetCore.Mvc.Core

`JsonResult`a déménagé `Microsoft.AspNetCore.Mvc.Core` à l’assemblée. Ce type était défini dans [Microsoft.AspNetCore.Mvc.Formatters.Json](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json). Un attribut de niveau d’assemblage [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) a été ajouté pour `Microsoft.AspNetCore.Mvc.Formatters.Json` résoudre ce problème pour la majorité des utilisateurs. Les applications qui utilisent des bibliothèques tierces peuvent rencontrer des problèmes.

#### <a name="version-introduced"></a>Version introduite

3.0 Aperçu 6

#### <a name="old-behavior"></a>Ancien comportement

Une application utilisant une bibliothèque basée sur 2,2 se construit avec succès.

#### <a name="new-behavior"></a>Nouveau comportement

Une application utilisant une bibliothèque basée sur 2,2 échoue compilation. Une erreur contenant une variation du texte suivant est fournie :

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Pour un exemple d’un tel numéro, voir [dotnet/aspnetcore 7220](https://github.com/dotnet/aspnetcore/issues/7220).

#### <a name="reason-for-change"></a>Raison du changement

Modifications au niveau de la plate-forme dans la composition de ASP.NET Core, telle qu’elle est décrite à [l’aspnet/Announcements 325](https://github.com/aspnet/Announcements/issues/325).

#### <a name="recommended-action"></a>Action recommandée

Les bibliothèques compilées par rapport `Microsoft.AspNetCore.Mvc.Formatters.Json` à la version 2.2 de peut-être besoin de recompte pour résoudre le problème pour tous les consommateurs. En cas d’incidence, communiquez avec l’auteur de la bibliothèque. Demande de recomplification de la bibliothèque pour cibler ASP.NET Noyau 3.0.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
