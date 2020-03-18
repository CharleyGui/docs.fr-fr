---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901888"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hébergement: L’hôte générique restreint l’injection de constructeurs startup

Les seuls types que `Startup` l’hôte générique `IHostEnvironment` `IWebHostEnvironment`prend `IConfiguration`en charge pour l’injection de constructeur de classe sont , , et . Les `WebHost` applications utilisant ne sont pas affectées.

#### <a name="change-description"></a>Description de la modification

Avant ASP.NET Core 3.0, l’injection de constructeurs pouvait être `Startup` utilisée pour des types arbitraires dans le constructeur de la classe. Dans ASP.NET Core 3.0, la pile Web a été réplatformée sur la bibliothèque d’accueil générique. Vous pouvez voir la modification du *fichier Program.cs* des modèles :

**ASP.NET Noyau 2.x:**

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Noyau 3.0:**

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host`utilise un conteneur d’injection de dépendance (DI) pour construire l’application. `WebHost`utilise deux conteneurs : un pour l’hôte et un pour l’application. Par conséquent, `Startup` le constructeur ne prend plus en charge l’injection de service personnalisé. Seulement `IHostEnvironment` `IWebHostEnvironment`, `IConfiguration` , et peut être injecté. Ce changement empêche les problèmes d’DI tels que la création en double d’un service singleton.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Raison du changement

Ce changement est une conséquence de la réplatformation de la pile Web sur la bibliothèque d’accueil générique.

#### <a name="recommended-action"></a>Action recommandée

Injecter des `Startup.Configure` services dans la signature de la méthode. Par exemple :

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
