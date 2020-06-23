---
title: Appel d'un service REST à partir d'un service WCF
description: Découvrez comment faire en sorte qu’un service WCF utilise le contexte approprié avec un service de type REST en créant une étendue et en appelant le service de type REST à partir de cette étendue.
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: 15f468923cf55feb85e7aeca1a2cc5e38050d665
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245295"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="7cc75-103">Appel d'un service REST à partir d'un service WCF</span><span class="sxs-lookup"><span data-stu-id="7cc75-103">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="7cc75-104">Lors de l'appel d'un service REST à partir d'un service WCF (SOAP-) normal, le contexte d'opération sur la méthode de service (qui contient des informations sur la requête entrante) remplace le contexte qui doit être utilisé par la requête sortante.</span><span class="sxs-lookup"><span data-stu-id="7cc75-104">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="7cc75-105">Ceci entraîne le remplacement des requêtes HTTP GET en requêtes HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="7cc75-105">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="7cc75-106">Pour forcer le service WCF à utiliser le contexte approprié pour appeler le service REST, créez un <xref:System.ServiceModel.OperationContextScope> et appelez le service REST à partir de l'étendue du contexte d'opération.</span><span class="sxs-lookup"><span data-stu-id="7cc75-106">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="7cc75-107">Cette rubrique explique comment créer un exemple simple qui illustre cette technique.</span><span class="sxs-lookup"><span data-stu-id="7cc75-107">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="7cc75-108">Définir le contrat de service REST</span><span class="sxs-lookup"><span data-stu-id="7cc75-108">Define the REST-style service contract</span></span>

<span data-ttu-id="7cc75-109">Définir un contrat de service REST simple :</span><span class="sxs-lookup"><span data-stu-id="7cc75-109">Define a simple  REST-style service contract:</span></span>

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

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="7cc75-110">Implémenter le contrat de service REST</span><span class="sxs-lookup"><span data-stu-id="7cc75-110">Implement the REST-style service contract</span></span>

<span data-ttu-id="7cc75-111">Implémenter le contrat de service REST :</span><span class="sxs-lookup"><span data-stu-id="7cc75-111">Implement the REST-style service contract:</span></span>

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

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="7cc75-112">Définir le contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="7cc75-112">Define the WCF service contract</span></span>

<span data-ttu-id="7cc75-113">Définir un contrat de service WCF à utiliser pour appeler le service REST :</span><span class="sxs-lookup"><span data-stu-id="7cc75-113">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

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

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="7cc75-114">Implémenter le contrat de service WCF</span><span class="sxs-lookup"><span data-stu-id="7cc75-114">Implement the WCF service contract</span></span>

<span data-ttu-id="7cc75-115">Implémenter le contrat de service WCF :</span><span class="sxs-lookup"><span data-stu-id="7cc75-115">Implement the WCF service contract:</span></span>

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

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="7cc75-116">Créer le proxy client pour le service REST</span><span class="sxs-lookup"><span data-stu-id="7cc75-116">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="7cc75-117">Utilisation <xref:System.ServiceModel.ClientBase%601> de pour implémenter le proxy client.</span><span class="sxs-lookup"><span data-stu-id="7cc75-117">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="7cc75-118">Pour chaque méthode appelée, un <xref:System.ServiceModel.OperationContextScope> est créé et utilisé pour appeler l'opération.</span><span class="sxs-lookup"><span data-stu-id="7cc75-118">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

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

## <a name="host-and-call-the-services"></a><span data-ttu-id="7cc75-119">Héberger et appeler les services</span><span class="sxs-lookup"><span data-stu-id="7cc75-119">Host and call the services</span></span>

<span data-ttu-id="7cc75-120">Hébergez les deux services dans une application console, en ajoutant les points de terminaison et les comportements nécessaires.</span><span class="sxs-lookup"><span data-stu-id="7cc75-120">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="7cc75-121">Puis appelez le service WCF normal :</span><span class="sxs-lookup"><span data-stu-id="7cc75-121">And then call the regular WCF service:</span></span>

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

## <a name="complete-code-listing"></a><span data-ttu-id="7cc75-122">Liste de codes complets</span><span class="sxs-lookup"><span data-stu-id="7cc75-122">Complete code listing</span></span>

<span data-ttu-id="7cc75-123">L'intégralité de l'exemple implémenté dans cette rubrique est présentée ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="7cc75-123">The following is a complete listing of the sample implemented in this topic:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7cc75-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cc75-124">See also</span></span>

- [<span data-ttu-id="7cc75-125">Procédure : créer un service Web HTTP WCF de base</span><span class="sxs-lookup"><span data-stu-id="7cc75-125">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="7cc75-126">Modèle objet de programmation HTTP web WCF</span><span class="sxs-lookup"><span data-stu-id="7cc75-126">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
