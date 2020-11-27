---
title: Ajout d'états en ligne et hors connexion
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 08ae4a20ced9626504c9fd2045416460e0878c5b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292920"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="bd553-102">Ajout d'états en ligne et hors connexion</span><span class="sxs-lookup"><span data-stu-id="bd553-102">Adding Online and Offline Status</span></span>

<span data-ttu-id="bd553-103">Dans de nombreux cas, il est important qu'une application surveille les informations relatives à l'état d'une connexion de canal homologue.</span><span class="sxs-lookup"><span data-stu-id="bd553-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="bd553-104">Vous pouvez obtenir ces informations en appelant la méthode `GetProperty` depuis une implémentation de l'interface <xref:System.ServiceModel.IOnlineStatus>.</span><span class="sxs-lookup"><span data-stu-id="bd553-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="bd553-105">Un objet implémenté sur cette interface peut en effet surveiller l'état de la connexion ou s'inscrire à des gestionnaires d'événements, tels que `OnOnline` et `OnOffline`. Cet objet réagira immédiatement à toutes modifications de l'état en ligne.</span><span class="sxs-lookup"><span data-stu-id="bd553-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="bd553-106">Dans l'infrastructure de canal homologue, un client est considéré comme étant en ligne s'il est connecté à au moins un autre homologue et comme étant hors connexion dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="bd553-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="bd553-107">Ceci peut s'avérer particulièrement utile à la fois pour déboguer les applications en cours de développement ou pour communiquer des informations détaillées à l'utilisateur final.</span><span class="sxs-lookup"><span data-stu-id="bd553-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd553-108">Un gestionnaire d'événements en ligne doit en premier lieu garantir l'ouverture du nœud avant l'envoi de tout message.</span><span class="sxs-lookup"><span data-stu-id="bd553-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd553-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd553-109">See also</span></span>

- [<span data-ttu-id="bd553-110">Création d'une application de canal homologue</span><span class="sxs-lookup"><span data-stu-id="bd553-110">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
