---
title: Extensibilité des canaux
ms.date: 03/30/2017
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
ms.openlocfilehash: 1a734c305e2a6f2fc759647ab5bdf380f7c7eeee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253834"
---
# <a name="channels-extensibility"></a><span data-ttu-id="c1b46-102">Extensibilité des canaux</span><span class="sxs-lookup"><span data-stu-id="c1b46-102">Channels Extensibility</span></span>

<span data-ttu-id="c1b46-103">Cette section contient des exemples qui illustrent des canaux personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c1b46-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1b46-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c1b46-104">In This Section</span></span>  

 [<span data-ttu-id="c1b46-105">Local Channel</span><span class="sxs-lookup"><span data-stu-id="c1b46-105">Local Channel</span></span>](local-channel.md)  
 <span data-ttu-id="c1b46-106">Illustre le canal local, un canal de transport WCF utilisé pour la communication au sein du même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="c1b46-106">Demonstrates the local channel, a WCF transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="c1b46-107">Reliable Secure Profile</span><span class="sxs-lookup"><span data-stu-id="c1b46-107">Reliable Secure Profile</span></span>](reliable-secure-profile.md)  
 <span data-ttu-id="c1b46-108">Montre comment composer WCF et Reliable Secure Profile (RSP).</span><span class="sxs-lookup"><span data-stu-id="c1b46-108">Demonstrates how to compose WCF and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="c1b46-109">Custom Channel Dispatcher</span><span class="sxs-lookup"><span data-stu-id="c1b46-109">Custom Channel Dispatcher</span></span>](custom-channel-dispatcher.md)  
 <span data-ttu-id="c1b46-110">Montre comment générer la pile de canaux de façon personnalisée en implémentant <xref:System.ServiceModel.ServiceHostBase> directement et comment créer un répartiteur de canal personnalisé dans un environnement avec hôte Web.</span><span class="sxs-lookup"><span data-stu-id="c1b46-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="c1b46-111">Canal de segmentation</span><span class="sxs-lookup"><span data-stu-id="c1b46-111">Chunking Channel</span></span>](chunking-channel.md)  
 <span data-ttu-id="c1b46-112">Montre comment limiter la quantité de mémoire utilisée pour mettre en mémoire tampon des messages volumineux envoyés à l’aide de WCF.</span><span class="sxs-lookup"><span data-stu-id="c1b46-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using WCF.</span></span>
  
 [<span data-ttu-id="c1b46-113">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="c1b46-113">HttpCookieSession</span></span>](httpcookiesession.md)  
 <span data-ttu-id="c1b46-114">Montre comment générer un canal de protocole personnalisé pour utiliser des cookies HTTP pour la gestion des sessions.</span><span class="sxs-lookup"><span data-stu-id="c1b46-114">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="c1b46-115">Custom Message Interceptor</span><span class="sxs-lookup"><span data-stu-id="c1b46-115">Custom Message Interceptor</span></span>](custom-message-interceptor.md)  
 <span data-ttu-id="c1b46-116">Montre comment implémenter un élément de liaison personnalisé qui crée des fabriques et des écouteurs de canaux pour intercepter tous les messages entrants et sortants à un point spécifique de la pile d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c1b46-116">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
