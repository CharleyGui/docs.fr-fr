---
title: Présentation de l’outil WCF svcutil
description: Vue d’ensemble de l’outil dotnet-svcutil Microsoft WCF, qui ajoute des fonctionnalités pour les projets .NET Core et ASP.NET Core, de manière similaire à l’outil svcutil WCF pour les projets .NET Framework.
author: mlacouture
ms.date: 02/22/2019
ms.custom: seodec18
ms.openlocfilehash: 723855401f3a81edbd34c77481e4ff12db7dcdaf
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926447"
---
# <a name="wcf-dotnet-svcutil-tool-for-net-core"></a><span data-ttu-id="323bf-103">Outil WCF dotnet-svcutil pour .NET Core</span><span class="sxs-lookup"><span data-stu-id="323bf-103">WCF dotnet-svcutil tool for .NET Core</span></span>

<span data-ttu-id="323bf-104">L’outil **dotnet-svcutil** Windows Communication Foundation (WCF) est un outil CLI .NET Core qui récupère les métadonnées d’un service web sur un emplacement réseau ou dans un fichier WSDL, puis génère une classe WCF contenant des méthodes de proxy clientes pour accéder aux opérations du service web.</span><span class="sxs-lookup"><span data-stu-id="323bf-104">The Windows Communication Foundation (WCF) **dotnet-svcutil** tool is a .NET Core CLI tool that retrieves metadata from a web service on a network location or from a WSDL file, and generates a WCF class containing client proxy methods that access the web service operations.</span></span>

<span data-ttu-id="323bf-105">Comme l’outil [**Métadonnées de modèle de service - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour les projets .NET Framework, **dotnet-svcutil** est un outil en ligne de commande pour générer une référence de service web compatible avec les projets .NET Core et .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="323bf-105">Similar to the [**Service Model Metadata - svcutil**](../../framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool for .NET Framework projects, the **dotnet-svcutil** is a command-line tool for generating a web service reference compatible with .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="323bf-106">L’outil **dotnet-svcutil** est une option alternative au fournisseur de services connectés Visual Studio [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) inclus dans Visual Studio 2017 v15.5.</span><span class="sxs-lookup"><span data-stu-id="323bf-106">The **dotnet-svcutil** tool is an alternative option to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider that first shipped with Visual Studio 2017 v15.5.</span></span> <span data-ttu-id="323bf-107">L’outil **dotnet-svcutil**, en tant qu’outil CLI .NET Core, est disponible sur les plateformes Linux, macOS et Windows.</span><span class="sxs-lookup"><span data-stu-id="323bf-107">The **dotnet-svcutil** tool as a .NET Core CLI tool, is available cross-platform on Linux, macOS, and Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="323bf-108">Vous devez référencer des services uniquement à partir d’une source approuvée.</span><span class="sxs-lookup"><span data-stu-id="323bf-108">You should only reference services from a trusted source.</span></span> <span data-ttu-id="323bf-109">L’ajout de références à partir d’une source non fiable peut compromettre la sécurité.</span><span class="sxs-lookup"><span data-stu-id="323bf-109">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="323bf-110">Prérequis</span><span class="sxs-lookup"><span data-stu-id="323bf-110">Prerequisites</span></span>

# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="323bf-111">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="323bf-111">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

* <span data-ttu-id="323bf-112">[Kit SDK .NET Core 2.1](https://dotnet.microsoft.com/download) (ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="323bf-112">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="323bf-113">Votre éditeur de code favori</span><span class="sxs-lookup"><span data-stu-id="323bf-113">Your favorite code editor</span></span>

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="323bf-114">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="323bf-114">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

* <span data-ttu-id="323bf-115">[Kit SDK .NET Core 1.0.4](https://dotnet.microsoft.com/download) (ou version ultérieure)</span><span class="sxs-lookup"><span data-stu-id="323bf-115">[.NET Core 1.0.4 SDK](https://dotnet.microsoft.com/download) or later versions</span></span>
* <span data-ttu-id="323bf-116">Votre éditeur de code favori</span><span class="sxs-lookup"><span data-stu-id="323bf-116">Your favorite code editor</span></span>

---

## <a name="getting-started"></a><span data-ttu-id="323bf-117">Prise en main</span><span class="sxs-lookup"><span data-stu-id="323bf-117">Getting started</span></span>

<span data-ttu-id="323bf-118">L’exemple suivant explique les étapes à suivre pour ajouter une référence de services web à un projet web .NET Core et appeler le service.</span><span class="sxs-lookup"><span data-stu-id="323bf-118">The following example walks you through the steps required to add a web service reference to a .NET Core web project and invoke the service.</span></span> <span data-ttu-id="323bf-119">Vous allez créer une application web .NET Core nommée _HelloSvcutil_ et ajouter une référence à un service web qui implémente le contrat suivant :</span><span class="sxs-lookup"><span data-stu-id="323bf-119">You'll create a .NET Core web application named _HelloSvcutil_ and add a reference to a web service that implements the following contract:</span></span>

```csharp
[ServiceContract]
public interface ISayHello
{
    [OperationContract]
    string Hello(string name);
}
```

<span data-ttu-id="323bf-120">Supposons dans cet exemple que le service web sera hébergé à l’adresse suivante : `http://contoso.com/SayHello.svc`.</span><span class="sxs-lookup"><span data-stu-id="323bf-120">For this example, let's assume the web service will be hosted at the following address: `http://contoso.com/SayHello.svc`</span></span>

<span data-ttu-id="323bf-121">À partir d’une fenêtre de commande Windows, macOS ou Linux, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="323bf-121">From a Windows, macOS, or Linux command window perform the following steps:</span></span>

1. <span data-ttu-id="323bf-122">Créez un répertoire nommé _HelloSvcutil_ pour votre projet et faites-en votre répertoire actuel, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="323bf-122">Create a directory named _HelloSvcutil_ for your project and make it your current directory, as in the following example:</span></span>

    ```console
    mkdir HelloSvcutil
    cd HelloSvcutil
    ```

2. <span data-ttu-id="323bf-123">Créez un projet web C# dans ce répertoire avec la commande [`dotnet new`](../tools/dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="323bf-123">Create a new C# web project in that directory using the [`dotnet new`](../tools/dotnet-new.md) command as follows:</span></span>

    ```console
    dotnet new web
    ```

3. <span data-ttu-id="323bf-124">Installez le [package NuGet `dotnet-svcutil`](https://nuget.org/packages/dotnet-svcutil) comme un outil CLI :  </span><span class="sxs-lookup"><span data-stu-id="323bf-124">Install the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool:  </span></span><!-- markdownlint-disable MD023 -->
    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="323bf-125">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="323bf-125">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```console
    dotnet tool install --global dotnet-svcutil
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="323bf-126">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="323bf-126">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)
    <span data-ttu-id="323bf-127">Ouvrez le fichier projet `HelloSvcutil.csproj` dans l’éditeur de votre projet, modifiez l’élément `Project` et ajoutez le [`dotnet-svcutil` package NuGet](https://nuget.org/packages/dotnet-svcutil) comme référence d’outil CLI à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="323bf-127">Open the `HelloSvcutil.csproj` project file in your editor, edit the `Project` element, and add the [`dotnet-svcutil` NuGet package](https://nuget.org/packages/dotnet-svcutil) as a CLI tool reference, using the following code:</span></span>

    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil" Version="1.0.*" />
    </ItemGroup>
    ```

    <span data-ttu-id="323bf-128">Ensuite, restaurez le package _dotnet-svcutil_ avec la commande [`dotnet restore`](../tools/dotnet-restore.md) :</span><span class="sxs-lookup"><span data-stu-id="323bf-128">Then restore the _dotnet-svcutil_ package using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```console
    dotnet restore
    ```

    ---

4. <span data-ttu-id="323bf-129">Exécutez la commande _dotnet-svcutil_ pour générer le fichier de référence de services web :</span><span class="sxs-lookup"><span data-stu-id="323bf-129">Run the _dotnet-svcutil_ command to generate the web service reference file as follows:</span></span>

    # <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="323bf-130">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="323bf-130">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

    ```console
    dotnet-svcutil http://contoso.com/SayHello.svc
    ```

    # <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="323bf-131">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="323bf-131">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

    ```console
    dotnet svcutil http://contoso.com/SayHello.svc
    ```

    ---

<span data-ttu-id="323bf-132">Le fichier généré est enregistré sous _HelloSvcutil/ServiceReference/Reference.cs_.</span><span class="sxs-lookup"><span data-stu-id="323bf-132">The generated file is saved as _HelloSvcutil/ServiceReference/Reference.cs_.</span></span> <span data-ttu-id="323bf-133">L’outil _dotnet-svcutil_ ajoute également au projet les packages WCF requis par le code proxy comme références de package.</span><span class="sxs-lookup"><span data-stu-id="323bf-133">The _dotnet-svcutil_ tool also adds to the project the appropriate WCF packages required by the proxy code as package references.</span></span>

## <a name="using-the-service-reference"></a><span data-ttu-id="323bf-134">Utiliser la référence de services</span><span class="sxs-lookup"><span data-stu-id="323bf-134">Using the Service Reference</span></span>

1. <span data-ttu-id="323bf-135">Restaurez les packages WCF à l’aide de la commande [`dotnet restore`](../tools/dotnet-restore.md), comme suit :</span><span class="sxs-lookup"><span data-stu-id="323bf-135">Restore the WCF packages using the [`dotnet restore`](../tools/dotnet-restore.md) command as follows:</span></span>

    ```console
    dotnet restore
    ```

2. <span data-ttu-id="323bf-136">Recherchez le nom de la classe cliente et l’opération que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="323bf-136">Find the name of the client class and operation you want to use.</span></span> <span data-ttu-id="323bf-137">`Reference.cs` contient une classe qui hérite de `System.ServiceModel.ClientBase`, avec des méthodes permettant d’appeler des opérations sur le service.</span><span class="sxs-lookup"><span data-stu-id="323bf-137">`Reference.cs` will contain a class that inherits from `System.ServiceModel.ClientBase`, with methods that can be used to call operations on the service.</span></span> <span data-ttu-id="323bf-138">L’objectif de cet exemple est d’appeler l’opération _Hello_ du service _SayHello_.</span><span class="sxs-lookup"><span data-stu-id="323bf-138">In this example, you want to call the _SayHello_ service's _Hello_ operation.</span></span> <span data-ttu-id="323bf-139">`ServiceReference.SayHelloClient` est le nom de la classe cliente et comporte une méthode `HelloAsync` servant à appeler l’opération.</span><span class="sxs-lookup"><span data-stu-id="323bf-139">`ServiceReference.SayHelloClient` is the name of the client class, and has a method called `HelloAsync` that can be used to call the operation.</span></span>

3. <span data-ttu-id="323bf-140">Ouvrez le fichier `Startup.cs` dans votre éditeur et ajoutez en haut une instruction using pour l’espace de noms de la référence de services :</span><span class="sxs-lookup"><span data-stu-id="323bf-140">Open the `Startup.cs` file in your editor, and add a using statement for the service reference namespace at the top:</span></span>

    ```csharp
    using ServiceReference;
    ```

4. <span data-ttu-id="323bf-141">Modifiez la méthode `Configure` de façon à appeler le service web.</span><span class="sxs-lookup"><span data-stu-id="323bf-141">Edit the `Configure` method to invoke the web service.</span></span> <span data-ttu-id="323bf-142">Pour cela, créez une instance de la classe qui hérite de `ClientBase` et appelez la méthode sur l’objet client :</span><span class="sxs-lookup"><span data-stu-id="323bf-142">You do this by creating an instance of the class that inherits from `ClientBase` and calling the method on the client object:</span></span>

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

5. <span data-ttu-id="323bf-143">Exécutez l’application en utilisant la commande [`dotnet run`](../tools/dotnet-run.md), comme suit :</span><span class="sxs-lookup"><span data-stu-id="323bf-143">Run the application using the [`dotnet run`](../tools/dotnet-run.md) command as follows:</span></span>

    ```console
    dotnet run
    ```

6. <span data-ttu-id="323bf-144">Accédez à l’URL figurant dans la console (par exemple, `http://localhost:5000`) dans votre navigateur web.</span><span class="sxs-lookup"><span data-stu-id="323bf-144">Navigate to the URL listed in the console (for example, `http://localhost:5000`) in your web browser.</span></span>

<span data-ttu-id="323bf-145">Vous devez voir la sortie suivante : "Hello dotnet-svcutil!"</span><span class="sxs-lookup"><span data-stu-id="323bf-145">You should see the following output: "Hello dotnet-svcutil!"</span></span>

<span data-ttu-id="323bf-146">Pour obtenir une description détaillée des paramètres de l’outil `dotnet-svcutil`, appelez l’outil en passant le paramètre d’aide comme suit :</span><span class="sxs-lookup"><span data-stu-id="323bf-146">For a detailed description of the `dotnet-svcutil` tool parameters, invoke the tool passing the help parameter as follows:</span></span>
# <a name="dotnet-svcutil-2xtabdotnetsvcutil2x"></a>[<span data-ttu-id="323bf-147">dotnet-svcutil 2.x</span><span class="sxs-lookup"><span data-stu-id="323bf-147">dotnet-svcutil 2.x</span></span>](#tab/dotnetsvcutil2x)

```console
dotnet-svcutil --help
```

# <a name="dotnet-svcutil-1xtabdotnetsvcutil1x"></a>[<span data-ttu-id="323bf-148">dotnet-svcutil 1.x</span><span class="sxs-lookup"><span data-stu-id="323bf-148">dotnet-svcutil 1.x</span></span>](#tab/dotnetsvcutil1x)

```console
dotnet svcutil --help
```

---

## <a name="feedback--questions"></a><span data-ttu-id="323bf-149">Commentaires et questions</span><span class="sxs-lookup"><span data-stu-id="323bf-149">Feedback & questions</span></span>

<span data-ttu-id="323bf-150">Si vous avez des questions ou des commentaires, [ouvrez un problème sur GitHub](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="323bf-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="323bf-151">Vous pouvez également consulter les questions ou problèmes existants dans le [dépôt WCF sur GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="323bf-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

## <a name="release-notes"></a><span data-ttu-id="323bf-152">Notes de publication</span><span class="sxs-lookup"><span data-stu-id="323bf-152">Release notes</span></span>

* <span data-ttu-id="323bf-153">Pour obtenir des informations à jour sur les versions, notamment les problèmes connus, consultez les [Notes de publication](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md).</span><span class="sxs-lookup"><span data-stu-id="323bf-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/dotnet-svcutil-notes.md) for updated release information, including known issues.</span></span>

## <a name="information"></a><span data-ttu-id="323bf-154">Information</span><span class="sxs-lookup"><span data-stu-id="323bf-154">Information</span></span>

* [<span data-ttu-id="323bf-155">Package NuGet dotnet-svcutil</span><span class="sxs-lookup"><span data-stu-id="323bf-155">dotnet-svcutil NuGet Package</span></span>](https://nuget.org/packages/dotnet-svcutil)
