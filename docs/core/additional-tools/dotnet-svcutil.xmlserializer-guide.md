---
title: Utilisation de dotnet-svcutil.xmlserializer
description: Découvrez comment vous pouvez utiliser le package NuGet `dotnet-svcutil.xmlserializer` afin de prégénérer un assembly de sérialisation pour les projets .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 4811647c294118cb160d25805e7d3ada97f071f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344902"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="2ab9a-103">Utiliser dotnet-svcutil.xmlserializer sur .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ab9a-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="2ab9a-104">Le package NuGet `dotnet-svcutil.xmlserializer` peut prégénérer un assembly de sérialisation pour les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="2ab9a-105">Il prégénère un code de sérialisation C# pour les types dans l’application cliente qui sont utilisés par le contrat de service WCF et qui peuvent être sérialisés par XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="2ab9a-106">Cela améliore les performances de démarrage de la sérialisation XML lors de la sérialisation ou de la désérialisation de ces types d’objets.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ab9a-107">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="2ab9a-107">Prerequisites</span></span>

* <span data-ttu-id="2ab9a-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) ou plus tard</span><span class="sxs-lookup"><span data-stu-id="2ab9a-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later</span></span>
* <span data-ttu-id="2ab9a-109">Votre éditeur de code favori</span><span class="sxs-lookup"><span data-stu-id="2ab9a-109">Your favorite code editor</span></span>

<span data-ttu-id="2ab9a-110">Vous pouvez utiliser la commande `dotnet --info` pour savoir quelles versions du runtime et du kit SDK .NET Core sont déjà installées.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="2ab9a-111">Prise en main</span><span class="sxs-lookup"><span data-stu-id="2ab9a-111">Getting started</span></span>

<span data-ttu-id="2ab9a-112">Pour utiliser `dotnet-svcutil.xmlserializer` dans une application console .NET Core :</span><span class="sxs-lookup"><span data-stu-id="2ab9a-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="2ab9a-113">Créez un service WCF nommé « MyWCFService » selon le modèle par défaut « WCF Service Application » dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="2ab9a-114">Ajoutez l’attribut `[XmlSerializerFormat]` sur la méthode de service :</span><span class="sxs-lookup"><span data-stu-id="2ab9a-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="2ab9a-115">créez une application console .NET Core comme application cliente WCF ciblant .NET Core 2.1 ou versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="2ab9a-116">Par exemple, créez une application nommée 'MyWCFClient' avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="2ab9a-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="2ab9a-117">Pour garantir que votre projet cible .NET Core 2.1 ou version ultérieure, inspectez l’élément XML `TargetFramework` dans votre fichier projet :</span><span class="sxs-lookup"><span data-stu-id="2ab9a-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="2ab9a-118">Ajoutez une référence de package à `System.ServiceModel.Http` en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="2ab9a-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="2ab9a-119">Ajoutez le code du client WCF :</span><span class="sxs-lookup"><span data-stu-id="2ab9a-119">Add the WCF Client code:</span></span>

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

5. <span data-ttu-id="2ab9a-120">Ajoutez une référence au package `dotnet-svcutil.xmlserializer` en exécutant la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="2ab9a-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="2ab9a-121">L’exécution de la commande doit ajouter à votre fichier projet une entrée similaire à ceci :</span><span class="sxs-lookup"><span data-stu-id="2ab9a-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="2ab9a-122">Générez l’application en exécutant `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="2ab9a-123">Si tout fonctionne, un assembly nommé *MyWCFClient.XmlSerializers.dll* est généré dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="2ab9a-124">Si l’outil n’est pas parvenu à générer l’assembly, des avertissements s’affichent dans la sortie de build.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="2ab9a-125">Démarrez le service WCF, par exemple, en exécutant `http://localhost:2561/Service1.svc` dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="2ab9a-126">Lancez ensuite l’application cliente, qui chargera et utilisera automatiquement les sérialiseurs prégénérés à l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2ab9a-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
