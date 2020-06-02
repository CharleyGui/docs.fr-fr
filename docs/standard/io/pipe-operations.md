---
title: Opérations de canal dans .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: a634cb87a5f25b520e5fe6fd5b39eae861120a28
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278686"
---
# <a name="pipe-operations-in-net"></a><span data-ttu-id="a3823-102">Opérations de canal dans .NET</span><span class="sxs-lookup"><span data-stu-id="a3823-102">Pipe Operations in .NET</span></span>
<span data-ttu-id="a3823-103">Les canaux sont un moyen de communication entre processus.</span><span class="sxs-lookup"><span data-stu-id="a3823-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="a3823-104">Il existe deux types de canaux :</span><span class="sxs-lookup"><span data-stu-id="a3823-104">There are two types of pipes:</span></span>  
  
- <span data-ttu-id="a3823-105">Canaux anonymes.</span><span class="sxs-lookup"><span data-stu-id="a3823-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="a3823-106">Les canaux anonymes fournissent une communication entre processus sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="a3823-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="a3823-107">Les canaux anonymes nécessitent moins de traitement que les canaux nommés, mais ils offrent des services limités.</span><span class="sxs-lookup"><span data-stu-id="a3823-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="a3823-108">Ils sont unidirectionnels et ne peuvent pas être utilisés sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="a3823-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="a3823-109">Ils prennent seulement en charge une instance de serveur.</span><span class="sxs-lookup"><span data-stu-id="a3823-109">They support only a single server instance.</span></span> <span data-ttu-id="a3823-110">Les canaux anonymes sont utiles pour la communication entre threads, ou entre processus parents et enfants où les handles de canaux peuvent être facilement passés au processus enfant durant sa création.</span><span class="sxs-lookup"><span data-stu-id="a3823-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="a3823-111">Dans .NET, l’implémentation de canaux anonymes s’effectue avec les classes <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="a3823-111">In .NET, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="a3823-112">Consultez [Guide pratique pour utiliser des canaux anonymes pour la communication entre processus en local](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="a3823-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
- <span data-ttu-id="a3823-113">Canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="a3823-113">Named pipes.</span></span>  
  
     <span data-ttu-id="a3823-114">Les canaux nommés fournissent la communication entre un serveur de canaux et un ou plusieurs clients de canaux.</span><span class="sxs-lookup"><span data-stu-id="a3823-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="a3823-115">Ils peuvent être unidirectionnels ou en duplex.</span><span class="sxs-lookup"><span data-stu-id="a3823-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="a3823-116">Ils prennent en charge la communication basée sur les messages et permettent à plusieurs clients de se connecter simultanément au processus serveur à l’aide du même nom de canal.</span><span class="sxs-lookup"><span data-stu-id="a3823-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="a3823-117">Les canaux nommés prennent également en charge l’emprunt d’identité, ce qui permet aux processus de connexion d’utiliser leurs propres autorisations sur des serveurs distants.</span><span class="sxs-lookup"><span data-stu-id="a3823-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="a3823-118">Dans .NET, l’implémentation de canaux nommés s’effectue avec les classes <xref:System.IO.Pipes.NamedPipeServerStream> et <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="a3823-118">In .NET, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="a3823-119">Consultez [Comment : utiliser des canaux nommés pour la communication entre processus en réseau](how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="a3823-119">See [How to: Use Named Pipes for Network Interprocess Communication](how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3823-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3823-120">See also</span></span>

- [<span data-ttu-id="a3823-121">E/s de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="a3823-121">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="a3823-122">Procédure : utiliser des canaux anonymes pour la communication entre processus en local</span><span class="sxs-lookup"><span data-stu-id="a3823-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [<span data-ttu-id="a3823-123">Procédure : utiliser des canaux nommés pour la communication entre processus en réseau</span><span class="sxs-lookup"><span data-stu-id="a3823-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
