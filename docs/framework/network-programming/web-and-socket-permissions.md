---
title: Autorisations web et socket
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- positions [.NET Framework], accepting
- sockets, permissions
- network, permissions
- Internet, permissions
- Network Resources
- SocketPermission class, about SocketPermission class
- positions [.NET Framework], connecting
- WebPermission class, about WebPermission class
- permissions [.NET Framework], sockets
- security [.NET Framework], Internet
- positions [.NET Framework], granting
ms.assetid: d51ad8cb-03ae-4a51-bfcd-cfcf6b98afa9
ms.openlocfilehash: d1b993acbf20eac244e596075c3f826bba3211a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046866"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="ba844-102">Autorisations web et socket</span><span class="sxs-lookup"><span data-stu-id="ba844-102">Web and Socket Permissions</span></span>
<span data-ttu-id="ba844-103">La sécurité Internet pour les applications utilisant l’espace de noms <xref:System.Net> est apportée par les classes <xref:System.Net.WebPermission> et <xref:System.Net.SocketPermission>.</span><span class="sxs-lookup"><span data-stu-id="ba844-103">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="ba844-104">La classe **WebPermission** détermine si une application est autorisée à demander des données à partir d’un URI ou d’utiliser un URI sur Internet.</span><span class="sxs-lookup"><span data-stu-id="ba844-104">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="ba844-105">La classe **SocketPermission** détermine si une application est autorisée à utiliser un <xref:System.Net.Sockets.Socket> pour accepter des données sur un port local ou pour communiquer avec des appareils distants utilisant un protocole de transport à une autre adresse, en fonction de l’hôte, du numéro de port et du protocole de transport du socket.</span><span class="sxs-lookup"><span data-stu-id="ba844-105">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="ba844-106">La classe d’autorisation à utiliser dépend du type de votre application.</span><span class="sxs-lookup"><span data-stu-id="ba844-106">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="ba844-107">Les applications qui utilisent <xref:System.Net.WebRequest> et ses descendants doivent utiliser la classe **WebPermission** pour gérer les autorisations.</span><span class="sxs-lookup"><span data-stu-id="ba844-107">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="ba844-108">Les applications qui utilisent un accès de niveau socket doivent utiliser la classe **SocketPermission** pour gérer les autorisations.</span><span class="sxs-lookup"><span data-stu-id="ba844-108">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="ba844-109">**WebPermission** et **SocketPermission** définissent deux autorisations : Accept et Connect.</span><span class="sxs-lookup"><span data-stu-id="ba844-109">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="ba844-110">Accept autorise l’application à répondre à une connexion entrante à partir d’une autre partie.</span><span class="sxs-lookup"><span data-stu-id="ba844-110">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="ba844-111">Connect l’autorise à démarrer une connexion à une autre partie.</span><span class="sxs-lookup"><span data-stu-id="ba844-111">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="ba844-112">Pour les instances **SocketPermission**, Accept signifie qu’une application peut accepter des connexions entrantes sur une adresse de transport locale et Connect signifie qu’une application peut se connecter à une adresse de transport distante (ou locale).</span><span class="sxs-lookup"><span data-stu-id="ba844-112">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="ba844-113">Pour les instances **WebPermission**, Accept signifie qu’une application peut exporter l’URI contrôlé par **WebPermission** sur Internet et Connect signifie qu’une application peut accéder à cet URI (distant ou local).</span><span class="sxs-lookup"><span data-stu-id="ba844-113">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba844-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba844-114">See also</span></span>

- [<span data-ttu-id="ba844-115">Sécurité</span><span class="sxs-lookup"><span data-stu-id="ba844-115">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="ba844-116">Sécurité dans la programmation réseau</span><span class="sxs-lookup"><span data-stu-id="ba844-116">Security in Network Programming</span></span>](security-in-network-programming.md)
