---
title: Opérations de canal dans .NET
description: 'En savoir plus sur les opérations de canal dans .NET. Les canaux sont un moyen de communication entre processus. Il existe deux types de canaux : les canaux anonymes et les canaux nommés.'
ms.date: 03/30/2017
helpviewer_keywords:
- pipes [.NET]
- pipe operations [.NET]
- interprocess communication [.NET], pipes
- I/O [.NET], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: bb8804c32b9f2b54b05298779bddae117c10dcf5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734801"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="909c8-105">Opérations de canal dans .NET</span><span class="sxs-lookup"><span data-stu-id="909c8-105">Pipe Operations in .NET</span></span>

<span data-ttu-id="909c8-106">Les canaux sont un moyen de communication entre processus.</span><span class="sxs-lookup"><span data-stu-id="909c8-106">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="909c8-107">Il existe deux types de canaux :</span><span class="sxs-lookup"><span data-stu-id="909c8-107">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="909c8-108">Canaux anonymes.</span><span class="sxs-lookup"><span data-stu-id="909c8-108">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="909c8-109">Les canaux anonymes fournissent une communication entre processus sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="909c8-109">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="909c8-110">Les canaux anonymes nécessitent moins de traitement que les canaux nommés, mais ils offrent des services limités.</span><span class="sxs-lookup"><span data-stu-id="909c8-110">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="909c8-111">Ils sont unidirectionnels et ne peuvent pas être utilisés sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="909c8-111">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="909c8-112">Ils prennent seulement en charge une instance de serveur.</span><span class="sxs-lookup"><span data-stu-id="909c8-112">They support only a single server instance.</span></span> <span data-ttu-id="909c8-113">Les canaux anonymes sont utiles pour la communication entre threads, ou entre processus parents et enfants où les handles de canaux peuvent être facilement passés au processus enfant durant sa création.</span><span class="sxs-lookup"><span data-stu-id="909c8-113">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="909c8-114">Dans .NET, l’implémentation de canaux anonymes s’effectue avec les classes <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="909c8-114">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="909c8-115">Consultez [Guide pratique pour utiliser des canaux anonymes pour la communication entre processus en local](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="909c8-115">See [How to: Use Anonymous Pipes for Local Interprocess Communication](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="909c8-116">Canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="909c8-116">Named pipes.</span></span>  
  
     <span data-ttu-id="909c8-117">Les canaux nommés fournissent la communication entre un serveur de canaux et un ou plusieurs clients de canaux.</span><span class="sxs-lookup"><span data-stu-id="909c8-117">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="909c8-118">Ils peuvent être unidirectionnels ou en duplex.</span><span class="sxs-lookup"><span data-stu-id="909c8-118">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="909c8-119">Ils prennent en charge la communication basée sur les messages et permettent à plusieurs clients de se connecter simultanément au processus serveur à l’aide du même nom de canal.</span><span class="sxs-lookup"><span data-stu-id="909c8-119">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="909c8-120">Les canaux nommés prennent également en charge l’emprunt d’identité, ce qui permet aux processus de connexion d’utiliser leurs propres autorisations sur des serveurs distants.</span><span class="sxs-lookup"><span data-stu-id="909c8-120">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="909c8-121">Dans .NET, l’implémentation de canaux nommés s’effectue avec les classes <xref:System.IO.Pipes.NamedPipeServerStream> et <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="909c8-121">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="909c8-122">Consultez [Comment : utiliser des canaux nommés pour la communication entre processus en réseau](how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="909c8-122">See [How to: Use Named Pipes for Network Interprocess Communication](how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="909c8-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="909c8-123">See also</span></span>

- [<span data-ttu-id="909c8-124">E/s de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="909c8-124">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="909c8-125">Procédure : utiliser des canaux anonymes pour la communication entre processus en local</span><span class="sxs-lookup"><span data-stu-id="909c8-125">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="909c8-126">Procédure : utiliser des canaux nommés pour la communication entre processus en réseau</span><span class="sxs-lookup"><span data-stu-id="909c8-126">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
