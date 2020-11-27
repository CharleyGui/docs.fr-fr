---
title: Autorisations web et socket
description: Découvrez comment les classes WebPermission et SocketPermission assurent la sécurité Internet pour l’utilisation de l’espace de noms System.Net dans l' .NET Framework.
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
ms.openlocfilehash: b940e6deb98686051847728da6fa5e20debc0f11
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276605"
---
# <a name="web-and-socket-permissions"></a><span data-ttu-id="ea3ef-103">Autorisations web et socket</span><span class="sxs-lookup"><span data-stu-id="ea3ef-103">Web and Socket Permissions</span></span>

<span data-ttu-id="ea3ef-104">La sécurité Internet pour les applications utilisant l’espace de noms <xref:System.Net> est apportée par les classes <xref:System.Net.WebPermission> et <xref:System.Net.SocketPermission>.</span><span class="sxs-lookup"><span data-stu-id="ea3ef-104">Internet security for applications using the <xref:System.Net> namespace is provided by the <xref:System.Net.WebPermission> and <xref:System.Net.SocketPermission> classes.</span></span> <span data-ttu-id="ea3ef-105">La classe **WebPermission** détermine si une application est autorisée à demander des données à partir d’un URI ou d’utiliser un URI sur Internet.</span><span class="sxs-lookup"><span data-stu-id="ea3ef-105">The **WebPermission** class controls an application's right to request data from a URI or to serve a URI to the Internet.</span></span> <span data-ttu-id="ea3ef-106">La classe **SocketPermission** détermine si une application est autorisée à utiliser un <xref:System.Net.Sockets.Socket> pour accepter des données sur un port local ou pour communiquer avec des appareils distants utilisant un protocole de transport à une autre adresse, en fonction de l’hôte, du numéro de port et du protocole de transport du socket.</span><span class="sxs-lookup"><span data-stu-id="ea3ef-106">The **SocketPermission** class controls an application's right to use a <xref:System.Net.Sockets.Socket> to accept data on a local port or to contact remote devices using a transport protocol at another address, based on the host, port number, and transport protocol of the socket.</span></span>  
  
 <span data-ttu-id="ea3ef-107">La classe d’autorisation à utiliser dépend du type de votre application.</span><span class="sxs-lookup"><span data-stu-id="ea3ef-107">Which permission class you use depends on your application type.</span></span> <span data-ttu-id="ea3ef-108">Les applications qui utilisent <xref:System.Net.WebRequest> et ses descendants doivent utiliser la classe **WebPermission** pour gérer les autorisations.</span><span class="sxs-lookup"><span data-stu-id="ea3ef-108">Applications that use <xref:System.Net.WebRequest> and its descendants should use the **WebPermission** class to manage permissions.</span></span> <span data-ttu-id="ea3ef-109">Les applications qui utilisent un accès de niveau socket doivent utiliser la classe **SocketPermission** pour gérer les autorisations.</span><span class="sxs-lookup"><span data-stu-id="ea3ef-109">Applications that use socket-level access should use the **SocketPermission** class to manage permissions.</span></span>  
  
 <span data-ttu-id="ea3ef-110">**WebPermission** et **SocketPermission** définissent deux autorisations : Accept et Connect.</span><span class="sxs-lookup"><span data-stu-id="ea3ef-110">**WebPermission** and **SocketPermission** define two permissions: accept and connect.</span></span> <span data-ttu-id="ea3ef-111">Accept autorise l’application à répondre à une connexion entrante à partir d’une autre partie.</span><span class="sxs-lookup"><span data-stu-id="ea3ef-111">Accept grants the application the right to answer an incoming connection from another party.</span></span> <span data-ttu-id="ea3ef-112">Connect l’autorise à démarrer une connexion à une autre partie.</span><span class="sxs-lookup"><span data-stu-id="ea3ef-112">Connect grants the application the right to initiate a connection to another party.</span></span>  
  
 <span data-ttu-id="ea3ef-113">Pour les instances **SocketPermission**, Accept signifie qu’une application peut accepter des connexions entrantes sur une adresse de transport locale et Connect signifie qu’une application peut se connecter à une adresse de transport distante (ou locale).</span><span class="sxs-lookup"><span data-stu-id="ea3ef-113">For **SocketPermission** instances, accept means that an application can accept incoming connections on a local transport address; connect means that an application can connect to some remote (or local) transport address.</span></span>  
  
 <span data-ttu-id="ea3ef-114">Pour les instances **WebPermission**, Accept signifie qu’une application peut exporter l’URI contrôlé par **WebPermission** sur Internet et Connect signifie qu’une application peut accéder à cet URI (distant ou local).</span><span class="sxs-lookup"><span data-stu-id="ea3ef-114">For **WebPermission** instances, accept means that an application can export the URI controlled by the **WebPermission** to the world; connect means that an application can access that URI (whether it is remote or local).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea3ef-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea3ef-115">See also</span></span>

- [<span data-ttu-id="ea3ef-116">Sécurité</span><span class="sxs-lookup"><span data-stu-id="ea3ef-116">Security</span></span>](../../standard/security/index.md)
- [<span data-ttu-id="ea3ef-117">Sécurité dans la programmation réseau</span><span class="sxs-lookup"><span data-stu-id="ea3ef-117">Security in Network Programming</span></span>](security-in-network-programming.md)
