---
title: configuration de valeurs du délai d'attente sur une liaison
description: Apprenez à gérer les paramètres de délai d’attente pour les liaisons WCF afin d’améliorer les performances, la facilité d’utilisation et la sécurité de votre service.
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 6582568f3579f784d4c91c707dbb35c38533551d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284041"
---
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="2aa66-103">configuration de valeurs du délai d'attente sur une liaison</span><span class="sxs-lookup"><span data-stu-id="2aa66-103">Configuring Timeout Values on a Binding</span></span>

<span data-ttu-id="2aa66-104">Il existe plusieurs paramètres de délai d'attente disponibles dans les liaisons WCF.</span><span class="sxs-lookup"><span data-stu-id="2aa66-104">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="2aa66-105">Définir ces paramètres de délai d'attente correctement peut non seulement améliorer les performances de votre service, mais également jouer un rôle dans la facilité d'utilisation et la sécurité de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="2aa66-105">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="2aa66-106">Les délais d'attente suivants sont disponibles sur les liaisons WCF :</span><span class="sxs-lookup"><span data-stu-id="2aa66-106">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="2aa66-107">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="2aa66-107">OpenTimeout</span></span>  
  
2. <span data-ttu-id="2aa66-108">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="2aa66-108">CloseTimeout</span></span>  
  
3. <span data-ttu-id="2aa66-109">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="2aa66-109">SendTimeout</span></span>  
  
4. <span data-ttu-id="2aa66-110">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="2aa66-110">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="2aa66-111">Délais d'attente de liaison WCF</span><span class="sxs-lookup"><span data-stu-id="2aa66-111">WCF Binding Timeouts</span></span>  

 <span data-ttu-id="2aa66-112">Chacun des paramètres décrits dans cette rubrique sont créés sur la liaison elle-même, dans le code ou la configuration.</span><span class="sxs-lookup"><span data-stu-id="2aa66-112">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="2aa66-113">Le code suivant montre comment définir des délais d’attente par programme sur une liaison WCF dans le contexte d’un service auto-hébergé.</span><span class="sxs-lookup"><span data-stu-id="2aa66-113">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");

    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));

        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);

        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 <span data-ttu-id="2aa66-114">L’exemple suivant montre comment configurer des délais d’attente sur une liaison dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="2aa66-114">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00"
                 closeTimeout="00:10:00"
                 sendTimeout="00:10:00"
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 <span data-ttu-id="2aa66-115">Plus d'informations sur ces paramètres se trouvent dans la documentation de la classe <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="2aa66-115">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="2aa66-116">Délais d'attente côté client</span><span class="sxs-lookup"><span data-stu-id="2aa66-116">Client-side Timeouts</span></span>  

 <span data-ttu-id="2aa66-117">Côté client :</span><span class="sxs-lookup"><span data-stu-id="2aa66-117">On the client side:</span></span>  
  
1. <span data-ttu-id="2aa66-118">SendTimeout – utilisé pour initialiser OperationTimeout, qui détermine le processus entier pour envoyer un message, y compris recevoir un message de réponse pour une opération de service de demande/réponse.</span><span class="sxs-lookup"><span data-stu-id="2aa66-118">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="2aa66-119">Ce délai d'attente s'applique également lors de l'envoi des messages de réponse d'une méthode du contrat de rappel.</span><span class="sxs-lookup"><span data-stu-id="2aa66-119">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="2aa66-120">OpenTimeout : utilisé lors de l’ouverture de canaux quand aucune valeur de délai d’attente explicite n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2aa66-120">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="2aa66-121">CloseTimeout : utilisé lors de la fermeture des canaux quand aucune valeur de délai d’attente explicite n’est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2aa66-121">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="2aa66-122">ReceiveTimeout – n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="2aa66-122">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="2aa66-123">Délais d’attente côté service</span><span class="sxs-lookup"><span data-stu-id="2aa66-123">Service-side Timeouts</span></span>  

 <span data-ttu-id="2aa66-124">Du côté service :</span><span class="sxs-lookup"><span data-stu-id="2aa66-124">On the service side:</span></span>  
  
1. <span data-ttu-id="2aa66-125">SendTimeout, OpenTimeout, CloseTimeout sont les mêmes que sur le client.</span><span class="sxs-lookup"><span data-stu-id="2aa66-125">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="2aa66-126">ReceiveTimeout – utilisé par la couche d'infrastructure de service pour initialiser le délai d'inactivité de session qui contrôle la durée pendant laquelle une session peut être inactive avant expiration.</span><span class="sxs-lookup"><span data-stu-id="2aa66-126">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
