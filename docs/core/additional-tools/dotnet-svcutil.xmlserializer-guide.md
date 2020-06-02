---
title: Utilisation de dotnet-Svcutil. XmlSerializer
description: Découvrez comment vous pouvez utiliser le package NuGet `dotnet-svcutil.xmlserializer` afin de prégénérer un assembly de sérialisation pour les projets .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 14bb2e8a85ec35f08b0a83b9734a64d751074f1b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284323"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="52137-103">Utiliser dotnet-svcutil.xmlserializer sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="52137-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="52137-104">Le package NuGet `dotnet-svcutil.xmlserializer` peut prégénérer un assembly de sérialisation pour les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="52137-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="52137-105">Il prégénère un code de sérialisation C# pour les types dans l’application cliente qui sont utilisés par le contrat de service WCF et qui peuvent être sérialisés par XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="52137-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="52137-106">Cela améliore les performances de démarrage de la sérialisation XML lors de la sérialisation ou de la désérialisation de ces types d’objets.</span><span class="sxs-lookup"><span data-stu-id="52137-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52137-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="52137-107">Prerequisites</span></span>

* <span data-ttu-id="52137-108">[.Net Core 2,1 SDK](https://dotnet.microsoft.com/download) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="52137-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later</span></span>
* <span data-ttu-id="52137-109">Votre éditeur de code favori</span><span class="sxs-lookup"><span data-stu-id="52137-109">Your favorite code editor</span></span>

<span data-ttu-id="52137-110">Vous pouvez utiliser la commande `dotnet --info` pour savoir quelles versions du runtime et du kit SDK .NET Core sont déjà installées.</span><span class="sxs-lookup"><span data-stu-id="52137-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="52137-111">Mise en route</span><span class="sxs-lookup"><span data-stu-id="52137-111">Getting started</span></span>

<span data-ttu-id="52137-112">Pour utiliser `dotnet-svcutil.xmlserializer` dans une application console .NET Core :</span><span class="sxs-lookup"><span data-stu-id="52137-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="52137-113">Créez un service WCF nommé « MyWCFService » selon le modèle par défaut « WCF Service Application » dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52137-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="52137-114">Ajoutez l’attribut `[XmlSerializerFormat]` sur la méthode de service :</span><span class="sxs-lookup"><span data-stu-id="52137-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="52137-115">créez une application console .NET Core comme application cliente WCF ciblant .NET Core 2.1 ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="52137-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="52137-116">Par exemple, créez une application nommée 'MyWCFClient' avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="52137-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="52137-117">Pour garantir que votre projet cible .NET Core 2.1 ou version ultérieure, inspectez l’élément XML `TargetFramework` dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="52137-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="52137-118">Ajoutez une référence de package à `System.ServiceModel.Http` en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="52137-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="52137-119">Ajoutez le code du client WCF :</span><span class="sxs-lookup"><span data-stu-id="52137-119">Add the WCF Client code:</span></span>

    ```csharp
    using System.ServiceModel;

        class Program
        {
            static void Main(string[] args)
            {
                var myBinding = new BasicHttpBinding();
                var myEndpoint = new EndpointAddress("http://localhost:2561/Service1.svc"); //Fill your service url here
                var myChannelFactory = new ChannelFactory<IService1>(myBinding, myEndpoint);
                IService1 client = myChannelFactory.CreateChannel();
                string s = client.GetData(1);
                ((ICommunicationObject)client).Close();
            }
        }

    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

5. <span data-ttu-id="52137-120">Ajoutez une référence au package `dotnet-svcutil.xmlserializer` en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="52137-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="52137-121">L’exécution de la commande doit ajouter à votre fichier projet une entrée similaire à ceci :</span><span class="sxs-lookup"><span data-stu-id="52137-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="52137-122">Générez l’application en exécutant `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="52137-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="52137-123">Si tout fonctionne, un assembly nommé *MyWCFClient.XmlSerializers.dll* est généré dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="52137-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="52137-124">Si l’outil n’est pas parvenu à générer l’assembly, des avertissements s’affichent dans la sortie de build.</span><span class="sxs-lookup"><span data-stu-id="52137-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="52137-125">Démarrez le service WCF, par exemple, en exécutant `http://localhost:2561/Service1.svc` dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="52137-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="52137-126">Ensuite, démarrez l’application cliente et elle chargera et utilisera automatiquement les sérialiseurs prégénérés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="52137-126">Then start the client application, and it will automatically load and use the pre-generated serializers at run time.</span></span>
