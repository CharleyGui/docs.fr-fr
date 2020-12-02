---
title: Gestion et accès aux données
description: Découvrez comment accéder aux données et les gérer dans ASP.NET Web Forms et Blazor .
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 66e6001cbcac612cb556e90fb86fd694ca7d1459
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509752"
---
# <a name="work-with-data"></a>Utilisation des données

L’accès aux données est le segment principal d’une application Web Forms ASP.NET. Si vous créez des formulaires pour le Web, que se passe-t-il pour ces données ? Avec Web Forms, plusieurs techniques d’accès aux données peuvent être utilisées pour interagir avec une base de données :

- Sources de données
- ADO.NET
- Entity Framework

Les sources de données étaient des contrôles que vous pouviez placer sur une page de Web Forms et configurer comme d’autres contrôles. Visual Studio a fourni un ensemble convivial de boîtes de dialogue pour configurer et lier les contrôles à vos pages de Web Forms. Les développeurs qui bénéficient d’une approche « code faible » ou « sans code » favorisent cette technique lors de la première publication de Web Forms.

![Sources de données](media/data/datasources.png)

ADO.NET est l’approche de bas niveau pour interagir avec une base de données. Vos applications peuvent créer une connexion à la base de données avec des commandes, des jeux d’enregistrements et des jeux de données pour interagir. Les résultats peuvent ensuite être liés à des champs sur l’écran sans trop de code. L’inconvénient de cette approche était que chaque ensemble d’objets ADO.NET ( `Connection` , `Command` et `Recordset` ) était lié aux bibliothèques fournies par un fournisseur de base de données. L’utilisation de ces composants rend le code rigide et difficile à migrer vers une autre base de données.

## <a name="entity-framework"></a>Entity Framework

Entity Framework (EF) est l’infrastructure de mappage objet/relationnel Open source gérée par .NET Foundation. Initialement publiée avec .NET Framework, EF permet de générer du code pour les connexions de base de données, les schémas de stockage et les interactions. Avec cette abstraction, vous pouvez vous concentrer sur les règles d’entreprise de votre application et autoriser la gestion de la base de données par un administrateur de base de données approuvé. Dans .NET, vous pouvez utiliser une version mise à jour d’EF appelée EF Core. EF Core permet de générer et de gérer les interactions entre votre code et la base de données avec une série de commandes qui sont disponibles pour vous à l’aide de l' `dotnet ef` outil en ligne de commande. Jetons un coup d’œil à quelques exemples pour vous aider à utiliser une base de données.

### <a name="ef-code-first"></a>Code First EF

Un moyen rapide de commencer à créer vos interactions de base de données consiste à commencer par les objets de classe que vous souhaitez utiliser. EF fournit un outil pour vous aider à générer le code de base de données approprié pour vos classes. Cette approche est appelée développement « Code First ». Considérons la `Product` classe suivante pour un exemple d’application vitrine que nous voulons stocker dans une base de données relationnelle comme Microsoft SQL Server.

```csharp
public class Product
{
    public int Id { get; set; }

    [Required]
    public string Name { get; set; }

    [MaxLength(4000)]
    public string Description { get; set; }

    [Range(0, 99999,99)]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }
}
```

Le produit a une clé primaire et trois champs supplémentaires qui seraient créés dans notre base de données :  

- EF identifie la `Id` propriété en tant que clé primaire par Convention.
- `Name` seront stockées dans une colonne configurée pour le stockage de texte. L' `[Required]` attribut qui décorer cette propriété ajoute une `not null` contrainte pour permettre l’application de ce comportement déclaré de la propriété.
- `Description` sont stockées dans une colonne configurée pour le stockage de texte et ont une longueur maximale configurée de 4000 caractères, comme imposé par l' `[MaxLength]` attribut. Le schéma de base de données sera configuré avec une colonne nommée `MaxLength` à l’aide du type de données `varchar(4000)` .
- La `Price` propriété sera stockée en tant que devise. L' `[Range]` attribut génère des contraintes appropriées pour empêcher le stockage de données en dehors des valeurs minimales et maximales déclarées.

Nous devons ajouter cette `Product` classe à une classe de contexte de base de données qui définit les opérations de connexion et de traduction avec notre base de données.

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

La `MyDbContext` classe fournit la propriété qui définit l’accès et la traduction de la `Product` classe.  Votre application configure cette classe pour l’interaction avec la base de données à l’aide des entrées suivantes dans la `Startup` méthode de la classe `ConfigureServices` :

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

Le code précédent se connecte à une base de données SQL Server avec la chaîne de connexion spécifiée. Vous pouvez placer la chaîne de connexion dans votre *appsettings.jssur* un fichier, des variables d’environnement ou d’autres emplacements de stockage de configuration, et remplacer cette chaîne incorporée de manière appropriée.

Vous pouvez ensuite générer la table de base de données appropriée pour cette classe à l’aide des commandes suivantes :

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

La première commande définit les modifications que vous apportez au schéma de base de données en tant que nouvelle migration EF appelée `Create Product table` .  Une migration définit comment appliquer et supprimer vos nouvelles modifications de base de données.

Une fois l’application appliquée, vous disposez d’une `Product` table simple dans votre base de données et de nouvelles classes ajoutées au projet pour aider à gérer le schéma de base de données.  Vous trouverez ces classes générées, par défaut, dans un nouveau dossier nommé *migrations*.  Lorsque vous apportez des modifications à la `Product` classe ou ajoutez des classes connexes que vous souhaitez interagir avec votre base de données, vous devez réexécuter les commandes de ligne de commande avec un nouveau nom de migration.  Cette commande génère un autre ensemble de classes de migration pour mettre à jour votre schéma de base de données.

### <a name="ef-database-first"></a>Database First EF

Pour les bases de données existantes, vous pouvez générer les classes pour EF Core à l’aide des outils en ligne de commande .NET. Pour générer un modèle de structure des classes, utilisez une variante de la commande suivante :

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

La commande précédente se connecte à la base de données à l’aide de la chaîne de connexion et du fournisseur spécifiés `Microsoft.EntityFrameworkCore.SqlServer` . Une fois connecté, une classe de contexte de base de données nommée `MyDbContext` est créée. En outre, les classes de prise en charge sont créées pour les `Product` `Customer` tables et qui ont été spécifiées avec les `-t` options. Il existe de nombreuses options de configuration pour cette commande afin de générer la hiérarchie de classes appropriée pour votre base de données. Pour obtenir une référence complète, consultez [la documentation de la commande](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).

Vous trouverez plus d’informations sur [EF Core](/ef/core/) sur le site Microsoft docs.

## <a name="interact-with-web-services"></a>Interagir avec les services Web

Lorsque ASP.NET a été publié pour la première fois, les services SOAP étaient le meilleur moyen pour les serveurs Web et les clients d’échanger des données. De nombreuses modifications ont été apportées depuis ce moment, et les interactions préférées avec les services ont été déplacées vers les interactions directes du client HTTP. Avec ASP.NET Core et Blazor , vous pouvez inscrire la configuration de votre `HttpClient` dans la `Startup` méthode de la classe `ConfigureServices` . Utilisez cette configuration lorsque vous devez interagir avec le point de terminaison HTTP. Considérez le code de configuration suivant :

```csharp
services.AddHttpClient("github", client =>
{
    client.BaseAddress = new Uri("http://api.github.com/");
    // Github API versioning
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    // Github requires a user-agent
    client.DefaultRequestHeaders.Add("User-Agent", "BlazorWebForms-Sample");
});
```

Chaque fois que vous devez accéder aux données à partir de GitHub, créez un client avec le nom `github` . Le client est configuré avec l’adresse de base et les en-têtes de demande sont correctement définis. Injectez `IHttpClientFactory` dans vos Blazor composants avec la `@inject` directive ou un `[Inject]` attribut sur une propriété. Créez votre client nommé et interagissez avec les services à l’aide de la syntaxe suivante :

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = await response.Content.ReadAsStringAsync();
    }
}
```

Cette méthode retourne la chaîne décrivant la collection de problèmes dans le référentiel GitHub *dotnet/docs* . Elle retourne le contenu au format JSON et est désérialisée en objets de problème GitHub appropriés. Il existe de nombreuses façons de configurer le `HttpClientFactory` pour fournir des objets préconfigurés `HttpClient` . Essayez de configurer plusieurs `HttpClient` instances avec des noms et des points de terminaison différents pour les différents services Web que vous utilisez. Cette approche rendra vos interactions avec ces services plus faciles à utiliser sur chaque page. Pour plus d’informations, consultez [la documentation de IHttpClientFactory](/aspnet/core/fundamentals/http-requests).

>[!div class="step-by-step"]
>[Précédent](forms-validation.md) 
> [Suivant](middleware.md)
