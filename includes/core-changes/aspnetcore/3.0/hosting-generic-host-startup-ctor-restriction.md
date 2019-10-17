---
ms.openlocfilehash: be9a79f6ead3e72d7ffaade758704f0c1e2477f0
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394308"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>Hébergement : l’hôte générique limite l’injection du constructeur de démarrage

Les seuls types pris en charge par l’hôte générique pour l’injection de constructeur de classe `Startup` sont `IHostEnvironment`, `IWebHostEnvironment` et `IConfiguration`. Les applications qui utilisent `WebHost` ne sont pas affectées.

#### <a name="change-description"></a>Modifier la description

Avant le ASP.NET Core 3,0, l’injection de constructeur pouvait être utilisée pour les types arbitraires dans le constructeur de la classe `Startup`. Dans ASP.NET Core 3,0, la pile Web a été reconnectée à la bibliothèque d’hôte générique. Vous pouvez voir la modification dans le fichier *Program.cs* des modèles :

**ASP.NET Core 2. x :**

<https://github.com/aspnet/AspNetCore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3,0 :**

<https://github.com/aspnet/AspNetCore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host` utilise un conteneur d’injection de dépendances (DI) pour générer l’application. `WebHost` utilise deux conteneurs : un pour l’hôte et un pour l’application. Par conséquent, le constructeur `Startup` ne prend plus en charge l’injection de service personnalisée. Seules `IHostEnvironment`, `IWebHostEnvironment` et `IConfiguration` peuvent être injectées. Cette modification empêche les problèmes de DI, tels que la création en double d’un service Singleton.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="reason-for-change"></a>Motif de modification

Cette modification est une conséquence de la replateforme de la pile Web sur la bibliothèque hôte générique.

#### <a name="recommended-action"></a>Action recommandée

Injecter des services dans la signature de méthode `Startup.Configure`. Exemple :

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
