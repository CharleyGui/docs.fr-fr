---
title: Gestion des connexions
description: Découvrez comment les applications qui utilisent HTTP pour les ressources de données peuvent utiliser les classes .NET Framework ServicePoint et ServicePointManager pour gérer les connexions.
ms.date: 01/25/2021
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
ms.openlocfilehash: 9ea93c3a9c484fd2a3de58b4d484b1e8445da155
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548056"
---
# <a name="managing-connections"></a><span data-ttu-id="99533-103">Gestion des connexions</span><span class="sxs-lookup"><span data-stu-id="99533-103">Managing Connections</span></span>

<span data-ttu-id="99533-104">Les applications qui utilisent HTTP pour se connecter aux ressources de données peuvent utiliser les classes <xref:System.Net.ServicePoint> et <xref:System.Net.ServicePointManager> du .NET Framework pour gérer les connexions à Internet et les aider à atteindre des performances et une évolutivité optimales.</span><span class="sxs-lookup"><span data-stu-id="99533-104">Applications that use HTTP to connect to data resources can use the .NET Framework's <xref:System.Net.ServicePoint> and <xref:System.Net.ServicePointManager> classes to manage connections to the Internet and to help them achieve optimum scale and performance.</span></span>  

> [!NOTE]
> <span data-ttu-id="99533-105">`ServicePoint` et `ServicePointManager` sont considérés comme hérités sur .net Core, .net 5 et les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="99533-105">`ServicePoint` and `ServicePointManager` are considered legacy on .NET Core, .NET 5, and later versions.</span></span> <span data-ttu-id="99533-106">La plupart de leurs propriétés et méthodes ne sont pas implémentées dans ces versions.</span><span class="sxs-lookup"><span data-stu-id="99533-106">Most of their properties and methods are not implemented in these versions.</span></span> <span data-ttu-id="99533-107">Lorsqu’elles sont implémentées, elles n’affectent pas et ne suivent rien sur les `HttpClient` API de mise en réseau.</span><span class="sxs-lookup"><span data-stu-id="99533-107">When they are implemented, they don't affect or track anything about `HttpClient` networking APIs.</span></span>
  
 <span data-ttu-id="99533-108">La classe **ServicePoint** fournit une application avec un point de terminaison auquel l’application peut se connecter pour accéder aux ressources Internet.</span><span class="sxs-lookup"><span data-stu-id="99533-108">The **ServicePoint** class provides an application with an endpoint to which the application can connect to access Internet resources.</span></span> <span data-ttu-id="99533-109">Chaque **ServicePoint** contient des informations qui vous aident à optimiser les connexions à un serveur Internet en partageant les informations d’optimisation entre les connexions pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="99533-109">Each **ServicePoint** contains information that helps optimize connections with an Internet server by sharing optimization information between connections to improve performance.</span></span>  
  
 <span data-ttu-id="99533-110">Chaque **ServicePoint** est identifié par un URI et est classé selon l’identificateur du schéma et les fragments d’hôte de l’URI.</span><span class="sxs-lookup"><span data-stu-id="99533-110">Each **ServicePoint** is identified by a Uniform Resource Identifier (URI) and is categorized according to the scheme identifier and host fragments of the URI.</span></span> <span data-ttu-id="99533-111">Par exemple, une même instance **ServicePoint** peut envoyer des requêtes aux URI `http://www.contoso.com/index.htm` et `http://www.contoso.com/news.htm?date=today`, car ces requêtes ont le même identificateur de schéma (http) et les mêmes fragments d’hôte (`www.contoso.com`).</span><span class="sxs-lookup"><span data-stu-id="99533-111">For example, the same **ServicePoint** instance would provide requests to the URIs `http://www.contoso.com/index.htm` and `http://www.contoso.com/news.htm?date=today` since they have the same scheme identifier (http) and host fragments (`www.contoso.com`).</span></span> <span data-ttu-id="99533-112">Si l’application a déjà une connexion permanente au serveur `www.contoso.com`, elle utilise cette connexion pour récupérer les deux requêtes, ce qui lui évite de créer deux connexions.</span><span class="sxs-lookup"><span data-stu-id="99533-112">If the application already has a persistent connection to the server `www.contoso.com`, it uses that connection to retrieve both requests, avoiding the need to create two connections.</span></span>  
  
 <span data-ttu-id="99533-113">**ServicePointManager** est une classe statique qui gère la création et la destruction des instances **ServicePoint**.</span><span class="sxs-lookup"><span data-stu-id="99533-113">**ServicePointManager** is a static class that manages the creation and destruction of **ServicePoint** instances.</span></span> <span data-ttu-id="99533-114">**ServicePointManager** crée un **ServicePoint** lorsque l’application demande une ressource Internet qui ne figure pas dans la collection existante d’instances **ServicePoint**.</span><span class="sxs-lookup"><span data-stu-id="99533-114">The **ServicePointManager** creates a **ServicePoint** when the application requests an Internet resource that is not in the collection of existing **ServicePoint** instances.</span></span> <span data-ttu-id="99533-115">Les instances **ServicePoint** sont détruites lorsqu’elles ont dépassé leur durée d’inactivité maximale ou lorsque le nombre d’instances **ServicePoint** existantes dépasse le nombre maximal d’instances **ServicePoint** de l’application.</span><span class="sxs-lookup"><span data-stu-id="99533-115">**ServicePoint** instances are destroyed when they have exceeded their maximum idle time or when the number of existing **ServicePoint** instances exceeds the maximum number of **ServicePoint** instances for the application.</span></span> <span data-ttu-id="99533-116">Vous pouvez contrôler la durée d’inactivité maximale par défaut et le nombre maximal d’instances **ServicePoint** en définissant les propriétés <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> et <xref:System.Net.ServicePointManager.MaxServicePoints%2A> du **ServicePointManager**.</span><span class="sxs-lookup"><span data-stu-id="99533-116">You can control both the default maximum idle time and the maximum number of **ServicePoint** instances by setting the <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> and <xref:System.Net.ServicePointManager.MaxServicePoints%2A> properties on the **ServicePointManager**.</span></span>  
  
 <span data-ttu-id="99533-117">Le nombre de connexions entre un client et un serveur peut avoir un impact considérable sur le débit de l’application.</span><span class="sxs-lookup"><span data-stu-id="99533-117">The number of connections between a client and server can have a dramatic impact on application throughput.</span></span> <span data-ttu-id="99533-118">Par défaut, une application qui utilise la classe <xref:System.Net.HttpWebRequest> utilise au maximum deux connexions persistantes à un serveur donné. Toutefois, vous pouvez définir le nombre maximal de connexions sur chaque application.</span><span class="sxs-lookup"><span data-stu-id="99533-118">By default, an application using the <xref:System.Net.HttpWebRequest> class uses a maximum of two persistent connections to a given server, but you can set the maximum number of connections on a per-application basis.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99533-119">La spécification HTTP/1.1 limite le nombre de connexions d’une application à deux connexions par serveur.</span><span class="sxs-lookup"><span data-stu-id="99533-119">The HTTP/1.1 specification limits the number of connections from an application to two connections per server.</span></span>  
  
 <span data-ttu-id="99533-120">Le nombre optimal de connexions dépend des conditions réelles dans lesquelles l’application s’exécute.</span><span class="sxs-lookup"><span data-stu-id="99533-120">The optimum number of connections depends on the actual conditions in which the application runs.</span></span> <span data-ttu-id="99533-121">L’augmentation du nombre de connexions disponibles pour l’application n’affecte pas nécessairement les performances de l’application.</span><span class="sxs-lookup"><span data-stu-id="99533-121">Increasing the number of connections available to the application may not affect application performance.</span></span> <span data-ttu-id="99533-122">Pour déterminer l’impact d’un plus grand nombre de connexions, exécutez des tests de performances avec différents nombres de connexions.</span><span class="sxs-lookup"><span data-stu-id="99533-122">To determine the impact of more connections, run performance tests while varying the number of connections.</span></span> <span data-ttu-id="99533-123">Vous pouvez modifier le nombre de connexions qu’utilise une application en modifiant la propriété statique <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> dans la classe **ServicePointManager** lors de l’initialisation de l’application, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="99533-123">You can change the number of connections that an application uses by changing the static <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> property on the **ServicePointManager** class at application initialization, as shown in the following code sample.</span></span>  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 <span data-ttu-id="99533-124">La modification de la propriété **ServicePointManager.DefaultConnectionLimit** n’affecte pas les instances de **ServicePoint** précédemment initialisées.</span><span class="sxs-lookup"><span data-stu-id="99533-124">Changing the **ServicePointManager.DefaultConnectionLimit** property does not affect previously initialized **ServicePoint** instances.</span></span> <span data-ttu-id="99533-125">Le code suivant change le nombre limite de connexions d’un **ServicePoint** existant pour le serveur `http://www.contoso.com` par la valeur stockée dans `newLimit`.</span><span class="sxs-lookup"><span data-stu-id="99533-125">The following code demonstrates changing the connection limit on an existing **ServicePoint** for the server `http://www.contoso.com` to the value stored in `newLimit`.</span></span>  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a><span data-ttu-id="99533-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99533-126">See also</span></span>

- [<span data-ttu-id="99533-127">Regroupement de connexions</span><span class="sxs-lookup"><span data-stu-id="99533-127">Connection Grouping</span></span>](connection-grouping.md)
- [<span data-ttu-id="99533-128">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="99533-128">Using Application Protocols</span></span>](using-application-protocols.md)
