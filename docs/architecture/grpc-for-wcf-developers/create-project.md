---
title: Créer un nouveau ASP.NET Core projet gRPC-gRPC pour les développeurs WCF
description: Découvrez comment créer un projet gRPC à l’aide de Visual Studio ou de la ligne de commande.
ms.date: 01/06/2021
ms.openlocfilehash: c9d66a773f0633c2ae93c42ce3ce53084032cd17
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970256"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Créer un projet gRPC ASP.NET Core

Le kit de développement logiciel (SDK) .NET est fourni avec un puissant outil CLI, `dotnet` , qui vous permet de créer et de gérer des projets et des solutions à partir de la ligne de commande. Le kit de développement logiciel (SDK) est étroitement intégré à Visual Studio, de sorte que tout est également disponible par le biais de l’interface utilisateur graphique familière. Ce chapitre présente les deux façons de créer un nouveau ASP.NET Core projet gRPC.

## <a name="create-the-project-by-using-visual-studio"></a>Créer le projet à l’aide de Visual Studio

> [!IMPORTANT]
> Pour développer une application ASP.NET Core 5,0, vous avez besoin de Visual Studio 2019 version 16,8 ou ultérieure, avec la charge de travail **ASP.net et développement Web** installée.

Créez une solution vide appelée **Traders** à partir du modèle de *solution vide* . Ajoutez un dossier de solution appelé `src` . Ensuite, cliquez avec le bouton droit sur le dossier et choisissez **Ajouter**  >  **nouveau projet**. Entrez `grpc` dans la zone de recherche du modèle, et un modèle de projet doit s’afficher `gRPC Service` .

![Capture d’écran de la boîte de dialogue Ajouter un nouveau projet](media/create-project/new-grpc-project.png)

Sélectionnez **suivant** pour passer à la boîte de dialogue **configurer votre nouveau projet** . Nommez le projet `TraderSys.Portfolios` et ajoutez un `src` sous-répertoire à l' **emplacement**.

![Capture d’écran de la boîte de dialogue Configurer votre nouveau projet](media/create-project/configure-project.png)

Sélectionnez **suivant** pour accéder à la boîte de dialogue **créer un service gRPC** .

![Capture d’écran de la boîte de dialogue créer un service gRPC](media/create-project/create-new-grpc-service-v2.png)

À l’heure actuelle, vous disposez d’options limitées pour la création du service. L’arrimeur sera présenté plus tard, donc pour l’instant, laissez cette option désélectionnée. Sélectionnez simplement **créer**. Votre premier projet ASP.NET Core 5,0 gRPC est généré et ajouté à la solution. Si vous ne souhaitez pas savoir comment utiliser le `dotnet CLI` , passez à la section [nettoyer l’exemple de code](#clean-up-the-example-code) .

## <a name="create-the-project-by-using-the-net-cli"></a>Créer le projet à l’aide de l’interface CLI .NET

Cette section décrit la création de solutions et de projets à partir de la ligne de commande.

Créez la solution comme indiqué dans la commande suivante. L' `-o` indicateur (ou `--output` ) spécifie le répertoire de sortie, qui est créé dans le répertoire actif s’il n’existe pas déjà. La solution porte le même nom que le répertoire : `TraderSys.sln` . Vous pouvez fournir un autre nom à l’aide de l' `-n` indicateur (ou `--name` ).

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 5,0 est fourni avec un modèle CLI pour les services gRPC. Créez le nouveau projet à l’aide de ce modèle, en le plaçant dans un `src` sous-répertoire comme conventionnel pour les projets ASP.net core. Le projet est nommé d’après le répertoire ( `TraderSys.Portfolios.csproj` ), sauf si vous spécifiez un nom différent avec l' `-n` indicateur.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Enfin, ajoutez le projet à la solution à l’aide de la `dotnet sln` commande :

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Étant donné que le répertoire particulier contient un seul `.csproj` fichier, vous pouvez spécifier uniquement le répertoire pour enregistrer la frappe.

Vous pouvez maintenant ouvrir cette solution dans Visual Studio 2019, Visual Studio Code ou dans l’éditeur de votre choix.

## <a name="clean-up-the-example-code"></a>Nettoyer l’exemple de code

Vous avez maintenant créé un exemple de service à l’aide du modèle gRPC, qui a été révisé précédemment dans le livre. Ce code n’est pas utile dans notre contexte commercial des actions. nous allons donc modifier les éléments de notre premier projet.

### <a name="rename-and-edit-the-proto-file"></a>Renommer et modifier le fichier proto

Continuez et renommez le `Protos/greet.proto` fichier `Protos/portfolios.proto` , puis ouvrez-le dans votre éditeur. Supprimer tout après la `package` ligne. Modifiez ensuite les `option csharp_namespace` `package` noms, et `service` , et supprimez le `SayHello` service par défaut. Le code ressemble maintenant à ce qui suit :

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> Le modèle n’ajoute pas la `Protos` partie espace de noms par défaut, mais il facilite la conservation des classes générées par gRPC et de vos propres classes clairement séparées dans votre code.

Si vous renommez le `greet.proto` fichier dans un environnement de développement intégré (IDE) tel que Visual Studio, une référence à ce fichier est automatiquement mise à jour dans le `.csproj` fichier. Mais dans d’autres éditeurs, tels que Visual Studio Code, cette référence n’est pas mise à jour automatiquement. vous devez donc modifier le fichier projet manuellement.

Dans les cibles de génération gRPC, il existe un `Protobuf` élément item qui vous permet de spécifier les `.proto` fichiers qui doivent être compilés et la forme de génération de code requise (autrement dit, « Server » ou « client »).

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>Renommer la `GreeterService` classe

La `GreeterService` classe se trouve dans le `Services` dossier et hérite de `Greeter.GreeterBase` . Renommez- `PortfolioService` le et remplacez la classe de base par `Portfolios.PortfoliosBase` . Supprimez les `override` méthodes.

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

Il y a eu une référence à la `GreeterService` classe dans la `Configure` méthode de la `Startup` classe. Si vous avez utilisé la refactorisation pour renommer la classe, cette référence doit avoir été mise à jour automatiquement. Toutefois, si vous ne l’avez pas fait, vous devez le modifier manuellement.

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

Dans la section suivante, nous ajouterons des fonctionnalités à ce nouveau service.

>[!div class="step-by-step"]
>[Précédent](migrate-wcf-to-grpc.md) 
> [Suivant](migrate-request-reply.md)
