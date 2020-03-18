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
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Utiliser dotnet-svcutil.xmlserializer sur .NET Core

Le package NuGet `dotnet-svcutil.xmlserializer` peut prégénérer un assembly de sérialisation pour les projets .NET Core. Il prégénère un code de sérialisation C# pour les types dans l’application cliente qui sont utilisés par le contrat de service WCF et qui peuvent être sérialisés par XmlSerializer. Cela améliore les performances de démarrage de la sérialisation XML lors de la sérialisation ou de la désérialisation de ces types d’objets.

## <a name="prerequisites"></a>Conditions préalables requises

* [.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) ou plus tard
* Votre éditeur de code favori

Vous pouvez utiliser la commande `dotnet --info` pour savoir quelles versions du runtime et du kit SDK .NET Core sont déjà installées.

## <a name="getting-started"></a>Prise en main

Pour utiliser `dotnet-svcutil.xmlserializer` dans une application console .NET Core :

1. Créez un service WCF nommé « MyWCFService » selon le modèle par défaut « WCF Service Application » dans .NET Framework. Ajoutez l’attribut `[XmlSerializerFormat]` sur la méthode de service :

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. créez une application console .NET Core comme application cliente WCF ciblant .NET Core 2.1 ou versions ultérieures. Par exemple, créez une application nommée 'MyWCFClient' avec la commande suivante :

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    Pour garantir que votre projet cible .NET Core 2.1 ou version ultérieure, inspectez l’élément XML `TargetFramework` dans votre fichier projet :

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Ajoutez une référence de package à `System.ServiceModel.Http` en exécutant la commande suivante :

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. Ajoutez le code du client WCF :

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

5. Ajoutez une référence au package `dotnet-svcutil.xmlserializer` en exécutant la commande suivante :
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    L’exécution de la commande doit ajouter à votre fichier projet une entrée similaire à ceci :
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Générez l’application en exécutant `dotnet build`. Si tout fonctionne, un assembly nommé *MyWCFClient.XmlSerializers.dll* est généré dans le dossier de sortie. Si l’outil n’est pas parvenu à générer l’assembly, des avertissements s’affichent dans la sortie de build.

7. Démarrez le service WCF, par exemple, en exécutant `http://localhost:2561/Service1.svc` dans le navigateur. Lancez ensuite l’application cliente, qui chargera et utilisera automatiquement les sérialiseurs prégénérés à l’exécution.
