---
title: Appel d'un service REST à partir d'un service WCF
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: eaa5d08faa335740124fcf698b22d2d324cd2c54
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576484"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="dd168-102">Appel d'un service REST à partir d'un service WCF</span><span class="sxs-lookup"><span data-stu-id="dd168-102">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="dd168-103">Lors de l'appel d'un service REST à partir d'un service WCF (SOAP-) normal, le contexte d'opération sur la méthode de service (qui contient des informations sur la requête entrante) remplace le contexte qui doit être utilisé par la requête sortante.</span><span class="sxs-lookup"><span data-stu-id="dd168-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="dd168-104">Ceci entraîne le remplacement des requêtes HTTP GET en requêtes HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="dd168-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="dd168-105">Pour forcer le service WCF à utiliser le contexte approprié pour appeler le service REST, créez un <xref:System.ServiceModel.OperationContextScope> et appelez le service REST à partir de l'étendue du contexte d'opération.</span><span class="sxs-lookup"><span data-stu-id="dd168-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="dd168-106">Cette rubrique explique comment créer un exemple simple qui illustre cette technique.</span><span class="sxs-lookup"><span data-stu-id="dd168-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="dd168-107">Définir le contrat de service REST</span><span class="sxs-lookup"><span data-stu-id="dd168-107">Define the REST-style service contract</span></span>

<span data-ttu-id="dd168-108">Définir un contrat de service REST simple :</span><span class="sxs-lookup"><span data-stu-id="dd168-108">Define a simple  REST-style service contract:</span></span>

```csharp
[ServiceContract]
public interface IRestInterface
{
    [OperationContract, WebGet]
    int Add(int x, int y);

    [OperationContract, WebGet]
    string Echo(string input);
}
```

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="dd168-109">Implémenter le contrat de service REST</span><span class="sxs-lookup"><span data-stu-id="dd168-109">Implement the REST-style service contract</span></span>

<span data-ttu-id="dd168-110">Implémenter le contrat de service REST :</span><span class="sxs-lookup"><span data-stu-id="dd168-110">Implement the REST-style service contract:</span></span>

```csharp
public class RestService : IRestInterface
{
    public int Add(int x, int y)
    {
        return x + y;
    }

    public string Echo(string input)
    {
        return input;
    }
}
```

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="dd168-111">Définir le contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="dd168-111">Define the WCF service contract</span></span>

<span data-ttu-id="dd168-112">Définir un contrat de service WCF à utiliser pour appeler le service REST :</span><span class="sxs-lookup"><span data-stu-id="dd168-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

```csharp
[ServiceContract]
public interface INormalInterface
{
    [OperationContract]
    int CallAdd(int x, int y);

    [OperationContract]
    string CallEcho(string input);
}
```

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="dd168-113">Implémenter le contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="dd168-113">Implement the WCF service contract</span></span>

<span data-ttu-id="dd168-114">Implémenter le contrat de service WCF :</span><span class="sxs-lookup"><span data-stu-id="dd168-114">Implement the WCF service contract:</span></span>

```csharp
public class NormalService : INormalInterface
{
    static MyRestClient client = new MyRestClient(RestServiceBaseAddress);
    public int CallAdd(int x, int y)
    {
        return client.Add(x, y);
    }

    public string CallEcho(string input)
    {
        return client.Echo(input);
    }
}
```

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="dd168-115">Créer le proxy client pour le service REST</span><span class="sxs-lookup"><span data-stu-id="dd168-115">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="dd168-116">Utilisation <xref:System.ServiceModel.ClientBase%601> de pour implémenter le proxy client.</span><span class="sxs-lookup"><span data-stu-id="dd168-116">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="dd168-117">Pour chaque méthode appelée, un <xref:System.ServiceModel.OperationContextScope> est créé et utilisé pour appeler l'opération.</span><span class="sxs-lookup"><span data-stu-id="dd168-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

```csharp
public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
{
    public MyRestClient(string address)
        : base(new WebHttpBinding(), new EndpointAddress(address))
    {
        this.Endpoint.Behaviors.Add(new WebHttpBehavior());
    }

    public int Add(int x, int y)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Add(x, y);
        }
    }

    public string Echo(string input)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Echo(input);
        }
    }
}
```

## <a name="host-and-call-the-services"></a><span data-ttu-id="dd168-118">Héberger et appeler les services</span><span class="sxs-lookup"><span data-stu-id="dd168-118">Host and call the services</span></span>

<span data-ttu-id="dd168-119">Hébergez les deux services dans une application console, en ajoutant les points de terminaison et les comportements nécessaires.</span><span class="sxs-lookup"><span data-stu-id="dd168-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="dd168-120">Puis appelez le service WCF normal :</span><span class="sxs-lookup"><span data-stu-id="dd168-120">And then call the regular WCF service:</span></span>

```csharp
public static void Main()
{
    ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
    restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
    restHost.Open();

    ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
    normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
    normalHost.Open();

    Console.WriteLine("Hosts opened");

    ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
    INormalInterface proxy = factory.CreateChannel();

    Console.WriteLine(proxy.CallAdd(123, 456));
    Console.WriteLine(proxy.CallEcho("Hello world"));
}
```

## <a name="complete-code-listing"></a><span data-ttu-id="dd168-121">Liste de codes complets</span><span class="sxs-lookup"><span data-stu-id="dd168-121">Complete code listing</span></span>

<span data-ttu-id="dd168-122">L'intégralité de l'exemple implémenté dans cette rubrique est présentée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="dd168-122">The following is a complete listing of the sample implemented in this topic:</span></span>

```csharp
public class CallingRESTSample
{
    static readonly string RestServiceBaseAddress = "http://" + Environment.MachineName + ":8008/Service";
    static readonly string NormalServiceBaseAddress = "http://" + Environment.MachineName + ":8000/Service";

    [ServiceContract]
    public interface IRestInterface
    {
        [OperationContract, WebGet]
        int Add(int x, int y);
        [OperationContract, WebGet]
        string Echo(string input);
    }

    [ServiceContract]
    public interface INormalInterface
    {
        [OperationContract]
        int CallAdd(int x, int y);
        [OperationContract]
        string CallEcho(string input);
    }

    public class RestService : IRestInterface
    {
        public int Add(int x, int y)
        {
            return x + y;
        }

        public string Echo(string input)
        {
            return input;
        }
    }

    public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
    {
        public MyRestClient(string address)
            : base(new WebHttpBinding(), new EndpointAddress(address))
        {
            this.Endpoint.Behaviors.Add(new WebHttpBehavior());
        }

        public int Add(int x, int y)
        {
            using (new OperationContextScope(this.InnerChannel))
            {
                return base.Channel.Add(x, y);
            }
        }

        public string Echo(string input)
        {
            using (new OperationContextScope(this.InnerChannel))
            {
                return base.Channel.Echo(input);
            }
        }
    }

    public class NormalService : INormalInterface
    {
        static MyRestClient client = new MyRestClient(RestServiceBaseAddress);
        public int CallAdd(int x, int y)
        {
            return client.Add(x, y);
        }

        public string CallEcho(string input)
        {
            return client.Echo(input);
        }
    }

    public static void Main()
    {
        ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
        restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
        restHost.Open();

        ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
        normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
        normalHost.Open();

        Console.WriteLine("Hosts opened");

        ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
        INormalInterface proxy = factory.CreateChannel();

        Console.WriteLine(proxy.CallAdd(123, 456));
        Console.WriteLine(proxy.CallEcho("Hello world"));
    }
}
```

## <a name="see-also"></a><span data-ttu-id="dd168-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd168-123">See also</span></span>

- [<span data-ttu-id="dd168-124">Procédure : créer un service Web HTTP WCF de base</span><span class="sxs-lookup"><span data-stu-id="dd168-124">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="dd168-125">Modèle objet de programmation HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="dd168-125">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
