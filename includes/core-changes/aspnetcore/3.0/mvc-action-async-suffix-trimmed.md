---
ms.openlocfilehash: 58b1190e3e6a3168d35700eed655f6756e076a29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901803"
---
### <a name="mvc-async-suffix-trimmed-from-controller-action-names"></a>MVC: Suffixe Async coupé à partir de noms d’action contrôleur

Dans le cadre de l’adresse [dotnet/aspnetcore 4849](https://github.com/dotnet/aspnetcore/issues/4849), ASP.NET Core `Async` MVC coupe le suffixe des noms d’action par défaut. En commençant par ASP.NET Core 3.0, ce changement affecte à la fois le routage et la génération de liaisons.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Considérez le contrôleur ASP.NET Core MVC suivant :

```csharp
public class ProductController : Controller
{
    public async IActionResult ListAsync()
    {
        var model = await DbContext.Products.ToListAsync();
        return View(model);
    }
}
```

L’action est `Product/ListAsync`routable via . La génération de `Async` liens nécessite de spécifier le suffixe. Par exemple :

```cshtml
<a asp-controller="Product" asp-action="ListAsync">List</a>
```

#### <a name="new-behavior"></a>Nouveau comportement

Dans ASP.NET Core 3.0, l’action est `Product/List`routable via . Le code de génération `Async` de lien doit omettre le suffixe. Par exemple :

```cshtml
<a asp-controller="Product" asp-action="List">List</a>
```

Cette modification n’affecte pas `[ActionName]` les noms spécifiés à l’aide de l’attribut. Le nouveau comportement peut `MvcOptions.SuppressAsyncSuffixInActionNames` être `false` `Startup.ConfigureServices`désactivé en définissant dans :

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="reason-for-change"></a>Raison du changement

Par convention, asynchrone .NET méthodes sont `Async`suffixes avec . Cependant, lorsqu’une méthode définit une action MVC, il n’est pas souhaitable d’utiliser le `Async` suffixe.

#### <a name="recommended-action"></a>Action recommandée

Si votre application dépend des actions MVC `Async` préservant le suffixe du nom, choisissez l’une des mesures d’atténuation suivantes :

- Utilisez `[ActionName]` l’attribut pour préserver le nom d’origine.
- Désactiver entièrement le changement de `MvcOptions.SuppressAsyncSuffixInActionNames` `false` nom `Startup.ConfigureServices`en mettant en place :

```csharp
services.AddMvc(options =>
{
   options.SuppressAsyncSuffixInActionNames = false;
});
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
