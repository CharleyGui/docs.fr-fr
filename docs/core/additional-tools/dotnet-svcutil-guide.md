---
title: Présentation de l’outil WCF svcutil
description: Vue d’ensemble de l’outil dotnet-svcutil Microsoft WCF, qui ajoute des fonctionnalités pour les projets .NET Core et ASP.NET Core, de manière similaire à l’outil svcutil WCF pour les projets .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 0607c73935f319f2cc0d8d9f92d96a4c71c54edf
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920947"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a>Outil WCF dotnet-svcutil pour .NET Core

L’outil **dotnet-svcutil** Windows Communication Foundation (WCF) est un outil .net qui récupère les métadonnées d’un service Web sur un emplacement réseau ou à partir d’un fichier WSDL, et génère une classe WCF contenant les méthodes de proxy client qui accèdent aux opérations de service Web.

Comme l’outil [**Métadonnées de modèle de service - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour les projets .NET Framework, **dotnet-svcutil** est un outil en ligne de commande pour générer une référence de service web compatible avec les projets .NET Core et .NET Standard.

L’outil **dotnet-Svcutil** est une option alternative à la [**Référence du service Web WCF**](wcf-web-service-reference-guide.md) du fournisseur de services connectés Visual Studio qui a été livré avec visual studio 2017 version 15,5. L’outil **dotnet-Svcutil** comme outil .net est disponible sur plusieurs plateformes sur Linux, MacOS et Windows.

> [!IMPORTANT]
> Vous devez référencer des services uniquement à partir d’une source approuvée. L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.

## <a name="prerequisites"></a>Prerequisites

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

- [Kit SDK .NET Core 2.1](https://dotnet.microsoft.com/download) (ou version ultérieure)
- Votre éditeur de code favori

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

- [Kit SDK .NET Core 1.0.4](https://dotnet.microsoft.com/download) (ou version ultérieure)
- Votre éditeur de code favori

---

## <a name="getting-started"></a>Bien démarrer

L’exemple suivant explique les étapes à suivre pour ajouter une référence de services web à un projet web .NET Core et appeler le service. Vous allez créer une application web .NET Core nommée *HelloSvcutil* et ajouter une référence à un service web qui implémente le contrat suivant :

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

Supposons dans cet exemple que le service web sera hébergé à l’adresse suivante : `http://contoso.com/SayHello.svc`.

À partir d’une fenêtre de commande Windows, macOS ou Linux, procédez comme suit :

1. Créez un répertoire nommé _HelloSvcutil_ pour votre projet et faites-en votre répertoire actuel, comme dans l’exemple suivant :

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. Créez un projet web C# dans ce répertoire avec la commande [`dotnet new`](../tools/dotnet-new.md) :

    ```dotnetcli
    dotnet new web
    ```

3. Installez le [package NuGet `dotnet-svcutil`](https://nuget.org/packages/dotnet-svcutil) comme un outil CLI :  <!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)
    Ouvrez le fichier projet `HelloSvcutil.csproj` dans l’éditeur de votre projet, modifiez l’élément `Project` et ajoutez le [`dotnet-svcutil` package NuGet](https://nuget.org/packages/dotnet-svcutil) comme référence d’outil CLI à l’aide du code suivant :

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    Ensuite, restaurez le package _dotnet-svcutil_ avec la commande [`dotnet restore`](../tools/dotnet-restore.md) :

    ```dotnetcli
    dotnet restore
    ```

    ---

4. Exécutez la commande _dotnet-svcutil_ pour générer le fichier de référence de services web :

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

Le fichier généré est enregistré sous _HelloSvcutil/ServiceReference/Reference.cs_. L’outil _dotnet-svcutil_ ajoute également au projet les packages WCF requis par le code proxy comme références de package.

## <a name="using-the-service-reference"></a>Utiliser la référence de services

1. Restaurez les packages WCF à l’aide de la commande [`dotnet restore`](../tools/dotnet-restore.md), comme suit :

    ```dotnetcli
    dotnet restore
    ```

2. Recherchez le nom de la classe cliente et l’opération que vous souhaitez utiliser. `Reference.cs` contient une classe qui hérite de `System.ServiceModel.ClientBase`, avec des méthodes permettant d’appeler des opérations sur le service. L’objectif de cet exemple est d’appeler l’opération _Hello_ du service _SayHello_. `ServiceReference.SayHelloClient` est le nom de la classe cliente et comporte une méthode `HelloAsync` servant à appeler l’opération.

3. Ouvrez le fichier `Startup.cs` dans votre éditeur et ajoutez en haut une instruction using pour l’espace de noms de la référence de services :

    ```csharp
    using ServiceReference;
    ```

4. Modifiez la méthode `Configure` de façon à appeler le service web. Pour cela, créez une instance de la classe qui hérite de `ClientBase` et appelez la méthode sur l’objet client :

    ```csharp
    public void Configure(IApplicationBuilder app, IHostingEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            var client = new SayHelloClient();
            var response = await client.HelloAsync();
            await context.Response.WriteAsync(response);
        });
    }

    ```

5. Exécutez l’application en utilisant la commande [`dotnet run`](../tools/dotnet-run.md), comme suit :

    ```dotnetcli
    dotnet run
    ```

6. Accédez à l’URL figurant dans la console (par exemple, `http://localhost:5000`) dans votre navigateur web.

La sortie suivante devrait s'afficher : « Hello dotnet-svcutil! »

Pour obtenir une description détaillée des paramètres de l’outil `dotnet-svcutil`, appelez l’outil en passant le paramètre d’aide comme suit :
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[dotnet-svcutil 2.x](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[dotnet-svcutil 1.x](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a>Commentaires et questions

Si vous avez des questions ou des commentaires, [ouvrez un problème sur GitHub](https://github.com/dotnet/wcf/issues/new). Vous pouvez également consulter les questions ou problèmes existants dans le [dépôt WCF sur GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).

## <a name="release-notes"></a>Notes de publication

- Pour obtenir des informations à jour sur les versions, notamment les problèmes connus, consultez les [Notes de publication](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md).

## <a name="information"></a>Informations

- [Package NuGet dotnet-svcutil](https://nuget.org/packages/dotnet-svcutil)
