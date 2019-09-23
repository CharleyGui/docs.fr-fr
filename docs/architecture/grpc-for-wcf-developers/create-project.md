---
title: Créer un nouveau ASP.NET Core projet gRPC-gRPC pour les développeurs WCF
description: Découvrez comment créer un projet gRPC à l’aide de Visual Studio ou à partir de la ligne de commande.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a0fcc3f9c4e32e87260a6bc79205c909ea3800e0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184567"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a>Créer un projet de gRPC ASP.NET Core

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

.Net Core est fourni avec un puissant outil CLI `dotnet`,, qui vous permet de créer et de gérer des projets et des solutions à partir de la ligne de commande. L’outil est étroitement intégré à Visual Studio, de sorte que tout est également disponible par le biais de l’interface graphique familière. Ce chapitre présente les deux façons de créer un projet de ASP.NET Core gRPC : tout d’abord avec Visual Studio, puis avec le CLI .NET Core.

## <a name="create-the-project-using-visual-studio"></a>Créer le projet à l’aide de Visual Studio

> [!IMPORTANT]
> Pour développer une application ASP.NET Core 3,0, vous avez besoin de Visual Studio 2019,3 ou version ultérieure avec la charge de travail **ASP.net et développement Web** installée.

Créez une solution vide appelée **Traders** à partir du modèle de *solution vide* . Ajoutez un dossier de solution `src`appelé, puis cliquez avec le bouton droit sur le dossier et choisissez **Ajouter** > un**nouveau projet** dans le menu contextuel. Entrez `grpc` dans la zone de recherche de modèle et vous devriez voir un modèle `gRPC Service`de projet appelé.

![Boîte de dialogue Ajouter un nouveau projet avec le modèle de projet de service gRPC](media/create-project/new-grpc-project.png)

Cliquez **sur suivant** pour passer à la boîte de dialogue **configurer** le projet `TraderSys.Portfolios`et nommez le `src` projet, puis ajoutez un sous-répertoire à l' **emplacement**.

![Boîte de dialogue Configurer le projet](media/create-project/configure-project.png)

Cliquez sur **suivant** pour accéder à la boîte de dialogue **nouveau projet gRPC** .

![Boîte de dialogue Nouveau projet gRPC](media/create-project/create-new-grpc-service.png)

À l’heure actuelle, il existe des options limitées pour la création du service. La station d’accueil sera introduite plus tard dans le livre. n’activez pas cette case à cocher pour le moment et cliquez simplement sur **créer**. Votre premier projet ASP.NET Core 3,0 gRPC est généré et ajouté à la solution. Si vous ne souhaitez pas savoir comment utiliser le `dotnet CLI`, passez à la section [nettoyer l’exemple de code](#clean-up-the-example-code) .

## <a name="create-the-project-using-the-net-core-cli"></a>Créez le projet à l’aide de l’CLI .NET Core

Cette section décrit la création de solutions et de projets à partir de la ligne de commande.

Créez la solution comme indiqué ci-dessous. L' `-o` indicateur ( `--output`ou) spécifie le répertoire de sortie, qui sera créé dans le répertoire actif s’il n’existe pas. La solution se verra attribuer le même nom que le répertoire, c.-à-d. `TraderSys.sln`. Vous pouvez fournir un autre nom à l' `-n` aide de `--name`l’indicateur (ou).

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

ASP.NET Core 3,0 est fourni avec un modèle CLI pour les services gRPC. Créez le projet à l’aide de ce modèle, en le `src` plaçant dans un sous-répertoire, comme la Convention pour les projets ASP.net core. Le projet est nommé d’après le répertoire (c’est-à-dire `TraderSys.Portfolios.csproj`), sauf si vous spécifiez un nom différent avec l' `-n` indicateur.

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

Enfin, ajoutez le projet à la solution à l' `dotnet sln` aide de la commande.

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> Étant donné que le répertoire donné ne contient `.csproj` qu’un seul fichier, vous pouvez vous contenter de spécifier uniquement le répertoire pour enregistrer la frappe.

Vous pouvez maintenant ouvrir cette solution dans Visual Studio 2019, Visual Studio Code ou dans l’éditeur de votre choix.

## <a name="clean-up-the-example-code"></a>Nettoyer l’exemple de code

Vous avez maintenant créé un exemple de service à l’aide du modèle gRPC, qui a été révisé précédemment dans le livre. Cela n’est pas utile dans notre contexte commercial boursier. nous allons donc modifier les éléments de notre premier projet.

### <a name="rename-and-edit-the-proto-file"></a>Renommer et modifier le fichier proto

Continuez et renommez le `Protos/greet.proto` `Protos/portfolios.proto` fichier et ouvrez-le dans votre éditeur. Tout supprimer après la `package` ligne, modifier les `option csharp_namespace`noms, `package` et `service` , et supprimer le service par `SayHello` défaut, de sorte que le code ressemble à ceci.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> Le modèle n’ajoute pas `Protos` la partie espace de noms par défaut, mais il facilite la conservation des classes générées par gRPC et de vos propres classes clairement séparées dans votre code.

Si vous renommez `greet.proto` le fichier dans un environnement de développement intégré (IDE) tel que Visual Studio, une référence à ce fichier est automatiquement `.csproj` mise à jour dans le fichier. Mais dans d’autres éditeurs, tels que Visual Studio Code, cette référence n’est pas mise à jour automatiquement. vous devez donc modifier le fichier projet manuellement.

Dans les cibles de génération gRPC, il existe `Protobuf` un élément item qui vous permet de `.proto` spécifier les fichiers qui doivent être compilés et la forme de génération de code requise (c’est-à-dire « Server » ou « client »).

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a>Renommer la classe GreeterService

La `GreeterService` classe se trouve dans `Services` le dossier et hérite `Greeter.GreeterBase`de. Renommez- `PortfolioService` le et remplacez la classe de `Portfolios.PortfoliosBase`base par. Supprimez `override` les méthodes.

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

Il y a eu une référence `GreeterService` à la classe `Configure` dans la méthode `Startup` de la classe. Si vous avez utilisé la refactorisation pour renommer la classe, cette référence doit avoir été mise à jour automatiquement. Toutefois, si vous ne l’avez pas fait, vous devez le modifier manuellement.

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
>[Suivant](migrate-request-reply.md)
