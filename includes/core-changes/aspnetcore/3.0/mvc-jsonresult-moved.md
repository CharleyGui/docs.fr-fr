---
ms.openlocfilehash: 1356f3eee5e2d8090d7d96aafc07a19507a1aff1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721685"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC : JsonResult déplacé vers Microsoft. AspNetCore. Mvc. Core

`JsonResult`a été déplacé vers l' `Microsoft.AspNetCore.Mvc.Core` assembly. Ce type a été utilisé pour être défini dans [Microsoft. AspNetCore. Mvc. Formatters. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json). Un attribut [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) au niveau de l’assembly a été ajouté à `Microsoft.AspNetCore.Mvc.Formatters.Json` pour résoudre ce problème pour la majorité des utilisateurs. Les applications qui utilisent des bibliothèques tierces peuvent rencontrer des problèmes.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 6

#### <a name="old-behavior"></a>Ancien comportement

Une application utilisant une bibliothèque 2,2 est générée avec succès.

#### <a name="new-behavior"></a>Nouveau comportement

Une application utilisant une bibliothèque 2,2 ne parvient pas à se compiler. Une erreur contenant une variante du texte suivant est fournie :

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Pour obtenir un exemple de ce type de problème, consultez [dotnet/aspnetcore # 7220](https://github.com/dotnet/aspnetcore/issues/7220).

#### <a name="reason-for-change"></a>Motif de modification

Modifications au niveau de la plateforme de la composition de ASP.NET Core comme décrit dans [ASPNET/announcements # 325](https://github.com/aspnet/Announcements/issues/325).

#### <a name="recommended-action"></a>Action recommandée

Les bibliothèques compilées avec la version 2,2 de `Microsoft.AspNetCore.Mvc.Formatters.Json` peuvent avoir besoin d’être recompilées pour résoudre le problème pour tous les consommateurs. S’il est affecté, contactez l’auteur de la bibliothèque. Demandez la recompilation de la bibliothèque pour cibler ASP.NET Core 3,0.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
