---
title: 'Procédure : utiliser des canaux anonymes pour la communication entre processus en local'
description: Découvrez comment utiliser des canaux anonymes pour la communication interprocessus locale sur un ordinateur local dans .NET. Les canaux anonymes nécessitent moins de surcharge que les canaux nommés.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
ms.openlocfilehash: 090a25aea4f280fc2ad00cf7777a501c475dfc66
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594801"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="56554-104">Procédure : utiliser des canaux anonymes pour la communication entre processus en local</span><span class="sxs-lookup"><span data-stu-id="56554-104">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="56554-105">Les canaux anonymes fournissent une communication entre processus sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56554-105">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="56554-106">Ils offrent moins de fonctionnalités que les canaux nommés, mais nécessitent également moins de surcharge.</span><span class="sxs-lookup"><span data-stu-id="56554-106">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="56554-107">Vous pouvez utiliser les canaux anonymes pour établir plus facilement une communication entre processus sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="56554-107">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="56554-108">Vous ne pouvez pas utiliser les canaux anonymes pour la communication sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="56554-108">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="56554-109">Pour implémenter des canaux anonymes, utilisez les classes <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="56554-109">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56554-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="56554-110">Example</span></span>  
 <span data-ttu-id="56554-111">L’exemple suivant montre une façon d’envoyer une chaîne à partir d’un processus parent à un processus enfant à l’aide de canaux anonymes.</span><span class="sxs-lookup"><span data-stu-id="56554-111">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="56554-112">Cet exemple crée un objet <xref:System.IO.Pipes.AnonymousPipeServerStream> dans un processus parent avec une valeur <xref:System.IO.Pipes.PipeDirection> de <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="56554-112">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="56554-113">Le processus parent crée ensuite un processus enfant à l’aide d’un handle client pour créer un objet <xref:System.IO.Pipes.AnonymousPipeClientStream>.</span><span class="sxs-lookup"><span data-stu-id="56554-113">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="56554-114">Le processus enfant a une valeur <xref:System.IO.Pipes.PipeDirection> de <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="56554-114">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="56554-115">Le processus parent envoie ensuite une chaîne fournie par l’utilisateur au processus enfant.</span><span class="sxs-lookup"><span data-stu-id="56554-115">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="56554-116">La chaîne est affichée sur la console dans le processus enfant.</span><span class="sxs-lookup"><span data-stu-id="56554-116">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="56554-117">L’exemple suivant présente le processus serveur.</span><span class="sxs-lookup"><span data-stu-id="56554-117">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a><span data-ttu-id="56554-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="56554-118">Example</span></span>  
 <span data-ttu-id="56554-119">L’exemple suivant présente le processus client.</span><span class="sxs-lookup"><span data-stu-id="56554-119">The following example shows the client process.</span></span> <span data-ttu-id="56554-120">Le processus serveur démarre le processus client et donne à ce processus un handle client.</span><span class="sxs-lookup"><span data-stu-id="56554-120">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="56554-121">Le fichier exécutable obtenu à partir du code client doit être nommé `pipeClient.exe` et être copié dans le même répertoire que l’exécutable serveur avant d’exécuter le processus serveur.</span><span class="sxs-lookup"><span data-stu-id="56554-121">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="56554-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56554-122">See also</span></span>

- [<span data-ttu-id="56554-123">Canaux</span><span class="sxs-lookup"><span data-stu-id="56554-123">Pipes</span></span>](pipe-operations.md)
- [<span data-ttu-id="56554-124">Procédure : utiliser des canaux nommés pour la communication entre processus en réseau</span><span class="sxs-lookup"><span data-stu-id="56554-124">How to: Use Named Pipes for Network Interprocess Communication</span></span>](how-to-use-named-pipes-for-network-interprocess-communication.md)
