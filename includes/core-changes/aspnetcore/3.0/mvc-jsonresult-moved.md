---
ms.openlocfilehash: 4f2ace670884d154b219d2146a242d2cee098831
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344305"
---
### <a name="mvc-jsonresult-moved-to-microsoftaspnetcoremvccore"></a>MVC : JsonResult déplacé vers Microsoft. AspNetCore. Mvc. Core

`JsonResult` a été déplacée vers l’assembly `Microsoft.AspNetCore.Mvc.Core`. Ce type a été utilisé pour être défini dans [Microsoft. AspNetCore. Mvc. Formatters. JSON](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Formatters.Json). Un attribut [[TypeForwardedTo]](xref:System.Runtime.CompilerServices.TypeForwardedToAttribute) au niveau de l’assembly a été ajouté à `Microsoft.AspNetCore.Mvc.Formatters.Json` pour résoudre ce problème pour la majorité des utilisateurs. Les applications qui utilisent des bibliothèques tierces peuvent rencontrer des problèmes.

#### <a name="version-introduced"></a>Version introduite

3,0 Preview 6

#### <a name="old-behavior"></a>Ancien comportement

Une application utilisant une bibliothèque 2,2 est générée avec succès.

#### <a name="new-behavior"></a>Nouveau comportement

Une application utilisant une bibliothèque 2,2 ne parvient pas à se compiler. Une erreur contenant une variante du texte suivant est fournie :

```
The type 'JsonResult' exists in both 'Microsoft.AspNetCore.Mvc.Core, Version=3.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60' and 'Microsoft.AspNetCore.Mvc.Formatters.Json, Version=2.0.0.0, Culture=neutral, PublicKeyToken=adb9793829ddae60'
```

Pour obtenir un exemple de ce type de problème, consultez [ASPNET/AspNetCore # 7220](https://github.com/aspnet/AspNetCore/issues/7220).

#### <a name="reason-for-change"></a>Motif de modification

Modifications au niveau de la plateforme de la composition de ASP.NET Core comme décrit dans [ASPNET/announcements # 325](https://github.com/aspnet/Announcements/issues/325).

#### <a name="recommended-action"></a>Action recommandée

Les bibliothèques compilées avec la version 2,2 de `Microsoft.AspNetCore.Mvc.Formatters.Json` peuvent avoir besoin d’être recompilées pour résoudre le problème pour tous les consommateurs. S’il est affecté, contactez l’auteur de la bibliothèque. Demandez la recompilation de la bibliothèque pour cibler ASP.NET Core 3,0.

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Mvc.JsonResult?displayProperty=nameWithType>

<!-- 

### Affected APIs

`T:Microsoft.AspNetCore.Mvc.JsonResult`

-->
