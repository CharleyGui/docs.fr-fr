---
title: Présentation de l’outil WCF svcutil
description: Vue d’ensemble de l’outil dotnet-svcutil Microsoft WCF, qui ajoute des fonctionnalités pour les projets .NET Core et ASP.NET Core, de manière similaire à l’outil svcutil WCF pour les projets .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.openlocfilehash: 0607c73935f319f2cc0d8d9f92d96a4c71c54edf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920947"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="e16c0-103">Outil WCF dotnet-svcutil pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="e16c0-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="e16c0-104">L’outil **dotnet-svcutil de** la Windows Communication Foundation (WCF) est un outil .NET qui récupère les métadonnées d’un service Web sur un emplacement réseau ou à partir d’un fichier WSDL, et génère une classe WCF contenant des méthodes de proxy client qui accèdent aux opérations de service Web.</span><span class="sxs-lookup"><span data-stu-id="e16c0-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="e16c0-105">Comme l’outil [**Métadonnées de modèle de service - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour les projets .NET Framework, **dotnet-svcutil** est un outil en ligne de commande pour générer une référence de service web compatible avec les projets .NET Core et .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="e16c0-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="e16c0-106">**L’outil dotnet-svcutil** est une option alternative au fournisseur de services connectés [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio qui a d’abord expédié avec Visual Studio 2017 version 15.5.</span><span class="sxs-lookup"><span data-stu-id="e16c0-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="e16c0-107">**L’outil dotnet-svcutil** comme un outil .NET, est disponible multi-plateforme sur Linux, macOS, et Windows.</span><span class="sxs-lookup"><span data-stu-id="e16c0-107">The **dotnet-svcutil** tool as a .NET tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e16c0-108">Vous devez référencer des services uniquement à partir d’une source approuvée.</span><span class="sxs-lookup"><span data-stu-id="e16c0-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="e16c0-109">L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.</span><span class="sxs-lookup"><span data-stu-id="e16c0-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e16c0-110">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="e16c0-110">Prerequisites</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="e16c0-111">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="e16c0-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

- <span data-ttu-id="e16c0-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="e16c0-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="e16c0-113">Votre éditeur de code favori</span><span class="sxs-lookup"><span data-stu-id="e16c0-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="e16c0-114">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="e16c0-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

- <span data-ttu-id="e16c0-115">[Kit SDK .NET Core 1.0.4](https://dotnet.microsoft.com/download) (ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="e16c0-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
- <span data-ttu-id="e16c0-116">Votre éditeur de code favori</span><span class="sxs-lookup"><span data-stu-id="e16c0-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="e16c0-117">Prise en main</span><span class="sxs-lookup"><span data-stu-id="e16c0-117">Getting started</span></span>

<span data-ttu-id="e16c0-118">L’exemple suivant explique les étapes à suivre pour ajouter une référence de services web à un projet web .NET Core et appeler le service.</span><span class="sxs-lookup"><span data-stu-id="e16c0-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="e16c0-119">Vous allez créer une application web .NET Core nommée *HelloSvcutil* et ajouter une référence à un service web qui implémente le contrat suivant :</span><span class="sxs-lookup"><span data-stu-id="e16c0-119">You'll create a .NET Core web application named *HelloSvcutil* and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="e16c0-120">Supposons dans cet exemple que le service web sera hébergé à l’adresse suivante : `http://contoso.com/SayHello.svc`.</span><span class="sxs-lookup"><span data-stu-id="e16c0-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="e16c0-121">À partir d’une fenêtre de commande Windows, macOS ou Linux, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="e16c0-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="e16c0-122">Créez un répertoire nommé _HelloSvcutil_ pour votre projet et faites-en votre répertoire actuel, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e16c0-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="e16c0-123">Créez un nouveau projet web CMD [`dotnet new`](../tools/dotnet-new.md) dans ce répertoire en utilisant la commande comme suit :</span><span class="sxs-lookup"><span data-stu-id="e16c0-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```dotnetcli
    dotnet new web
    ```

3. <span data-ttu-id="e16c0-124">Installez le [ `dotnet-svcutil` paquet NuGet](https://nuget.org/packages/dotnet-svcutil) comme outil CLI : </span><span class="sxs-lookup"><span data-stu-id="e16c0-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="e16c0-125">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="e16c0-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="e16c0-126">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="e16c0-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="e16c0-127">Ouvrez `HelloSvcutil.csproj` le fichier de projet `Project` dans votre éditeur, modifiez l’élément et ajoutez le [ `dotnet-svcutil` paquet NuGet](https://nuget.org/packages/dotnet-svcutil) comme référence d’outil CLI, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e16c0-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="e16c0-128">Ensuite, restaurez le package _dotnet-svcutil_ avec la commande [`dotnet restore`](../tools/dotnet-restore.md) :</span><span class="sxs-lookup"><span data-stu-id="e16c0-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

    ---

4. <span data-ttu-id="e16c0-129">Exécutez la commande _dotnet-svcutil_ pour générer le fichier de référence de services web :</span><span class="sxs-lookup"><span data-stu-id="e16c0-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="e16c0-130">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="e16c0-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```dotnetcli
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="e16c0-131">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="e16c0-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```dotnetcli
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="e16c0-132">Le fichier généré est enregistré sous _HelloSvcutil/ServiceReference/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="e16c0-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="e16c0-133">L’outil _dotnet-svcutil_ ajoute également au projet les packages WCF requis par le code proxy comme références de package.</span><span class="sxs-lookup"><span data-stu-id="e16c0-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="e16c0-134">Utiliser la référence de services</span><span class="sxs-lookup"><span data-stu-id="e16c0-134">Using the Service Reference</span></span>

1. <span data-ttu-id="e16c0-135">Restaurer les paquets [`dotnet restore`](../tools/dotnet-restore.md) WCF en utilisant la commande comme suit :</span><span class="sxs-lookup"><span data-stu-id="e16c0-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```dotnetcli
    dotnet restore
    ```

2. <span data-ttu-id="e16c0-136">Recherchez le nom de la classe cliente et l’opération que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="e16c0-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="e16c0-137">`Reference.cs` contient une classe qui hérite de `System.ServiceModel.ClientBase`, avec des méthodes permettant d’appeler des opérations sur le service.</span><span class="sxs-lookup"><span data-stu-id="e16c0-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="e16c0-138">L’objectif de cet exemple est d’appeler l’opération _Hello_ du service _SayHello_.</span><span class="sxs-lookup"><span data-stu-id="e16c0-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="e16c0-139">`ServiceReference.SayHelloClient` est le nom de la classe cliente et comporte une méthode `HelloAsync` servant à appeler l’opération.</span><span class="sxs-lookup"><span data-stu-id="e16c0-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="e16c0-140">Ouvrez le fichier `Startup.cs` dans votre éditeur et ajoutez en haut une instruction using pour l’espace de noms de la référence de services :</span><span class="sxs-lookup"><span data-stu-id="e16c0-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="e16c0-141">Modifiez la méthode `Configure` de façon à appeler le service web.</span><span class="sxs-lookup"><span data-stu-id="e16c0-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="e16c0-142">Pour cela, créez une instance de la classe qui hérite de `ClientBase` et appelez la méthode sur l’objet client :</span><span class="sxs-lookup"><span data-stu-id="e16c0-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

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

5. <span data-ttu-id="e16c0-143">Exécutez l’application à l’aide de la [`dotnet run`](../tools/dotnet-run.md) commande comme suit :</span><span class="sxs-lookup"><span data-stu-id="e16c0-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```dotnetcli
    dotnet run
    ```

6. <span data-ttu-id="e16c0-144">Accédez à l’URL figurant dans la console (par exemple, `http://localhost:5000`) dans votre navigateur web.</span><span class="sxs-lookup"><span data-stu-id="e16c0-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="e16c0-145">La sortie suivante devrait s'afficher : « Hello dotnet-svcutil! »</span><span class="sxs-lookup"><span data-stu-id="e16c0-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="e16c0-146">Pour obtenir une description détaillée des paramètres de l’outil `dotnet-svcutil`, appelez l’outil en passant le paramètre d’aide comme suit :</span><span class="sxs-lookup"><span data-stu-id="e16c0-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2x"></a>[<span data-ttu-id="e16c0-147">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="e16c0-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```dotnetcli
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1x"></a>[<span data-ttu-id="e16c0-148">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="e16c0-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```dotnetcli
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="e16c0-149">Commentaires et questions</span><span class="sxs-lookup"><span data-stu-id="e16c0-149">Feedback & questions</span></span>

<span data-ttu-id="e16c0-150">Si vous avez des questions ou des commentaires, [ouvrez un problème sur GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="e16c0-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="e16c0-151">Vous pouvez également consulter les questions ou problèmes existants dans le [dépôt WCF sur GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="e16c0-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="e16c0-152">Notes de publication</span><span class="sxs-lookup"><span data-stu-id="e16c0-152">Release notes</span></span>

- <span data-ttu-id="e16c0-153">Pour obtenir des informations à jour sur les versions, notamment les problèmes connus, consultez les [Notes de publication](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md).</span><span class="sxs-lookup"><span data-stu-id="e16c0-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="e16c0-154">Information</span><span class="sxs-lookup"><span data-stu-id="e16c0-154">Information</span></span>

- [<span data-ttu-id="e16c0-155">Package NuGet dotnet-svcutil</span><span class="sxs-lookup"><span data-stu-id="e16c0-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
