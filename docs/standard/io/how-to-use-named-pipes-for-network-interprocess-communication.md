---
title: 'Comment : utiliser des canaux nommés pour la communication entre processus en réseau'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communication [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
ms.openlocfilehash: 71f3a8d38b46993762b2673ea5fe735d8d54d351
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706632"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="6e3f2-102">Comment : utiliser des canaux nommés pour la communication entre processus en réseau</span><span class="sxs-lookup"><span data-stu-id="6e3f2-102">How to: Use Named Pipes for Network Interprocess Communication</span></span>
<span data-ttu-id="6e3f2-103">Les canaux nommés fournissent la communication entre un serveur de canaux et un ou plusieurs clients de canaux.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-103">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="6e3f2-104">Ils offrent plus de fonctionnalités que les canaux anonymes, qui fournissent la communication entre processus sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-104">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="6e3f2-105">Les canaux nommés prennent en charge la communication en duplex intégrale sur un réseau et plusieurs instances de serveur, la communication basée sur message et l’emprunt d’identité du client, ce qui permet aux processus de connexion d’utiliser leur propre jeu d’autorisations sur des serveurs distants.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-105">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="6e3f2-106">Pour implémenter des canaux nommés, utilisez les classes <xref:System.IO.Pipes.NamedPipeServerStream> et <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-106">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e3f2-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e3f2-107">Example</span></span>  
 <span data-ttu-id="6e3f2-108">L’exemple suivant illustre la création d’un canal nommé à l’aide de la classe <xref:System.IO.Pipes.NamedPipeServerStream>.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-108">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="6e3f2-109">Dans cet exemple, le processus serveur crée quatre threads.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-109">In this example, the server process creates four threads.</span></span> <span data-ttu-id="6e3f2-110">Chaque thread peut accepter une connexion cliente.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-110">Each thread can accept a client connection.</span></span> <span data-ttu-id="6e3f2-111">Le processus client connecté fournit ensuite au serveur un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-111">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="6e3f2-112">Si le client dispose des autorisations suffisantes, le processus serveur ouvre le fichier et renvoie son contenu au client.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-112">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="6e3f2-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e3f2-113">Example</span></span>  
 <span data-ttu-id="6e3f2-114">L’exemple suivant présente le processus client, qui utilise la classe <xref:System.IO.Pipes.NamedPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-114">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="6e3f2-115">Le client se connecte au processus serveur et envoie un nom de fichier au serveur.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-115">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="6e3f2-116">L’exemple utilise l’emprunt d’identité, donc l’identité qui exécute l’application cliente doit avoir l’autorisation d’accéder au fichier.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-116">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="6e3f2-117">Le serveur renvoie ensuite le contenu du fichier au client.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-117">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="6e3f2-118">Le contenu du fichier est ensuite affiché sur la console.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-118">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6e3f2-119">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="6e3f2-119">Robust Programming</span></span>  
 <span data-ttu-id="6e3f2-120">Les processus client et serveur dans cet exemple sont censés être exécutés sur le même ordinateur, donc le nom du serveur fourni à l’objet <xref:System.IO.Pipes.NamedPipeClientStream> est `"."`.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-120">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="6e3f2-121">Si les processus client et serveur se trouvent sur des ordinateurs distincts, `"."` est remplacé par le nom réseau de l’ordinateur qui exécute le processus serveur.</span><span class="sxs-lookup"><span data-stu-id="6e3f2-121">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e3f2-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e3f2-122">See also</span></span>

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [<span data-ttu-id="6e3f2-123">Canaux</span><span class="sxs-lookup"><span data-stu-id="6e3f2-123">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)
- [<span data-ttu-id="6e3f2-124">Guide pratique pour utiliser des canaux anonymes pour la communication entre processus en local</span><span class="sxs-lookup"><span data-stu-id="6e3f2-124">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
