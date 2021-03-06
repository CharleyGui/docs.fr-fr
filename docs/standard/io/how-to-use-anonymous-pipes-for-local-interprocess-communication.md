---
title: 'Procédure : utiliser des canaux anonymes pour la communication entre processus en local'
description: Découvrez comment utiliser des canaux anonymes pour la communication interprocessus locale sur un ordinateur local dans .NET. Les canaux anonymes nécessitent moins de surcharge que les canaux nommés.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- anonymous pipes [.NET]
- parent-child communication [.NET]
- pipes [.NET]
- one-way communication [.NET]
- local computer communication [.NET], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
ms.openlocfilehash: 389451d1c6c313ac4a10652c7aa614a5e4e7bf1c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734554"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Procédure : utiliser des canaux anonymes pour la communication entre processus en local

Les canaux anonymes fournissent une communication entre processus sur un ordinateur local. Ils offrent moins de fonctionnalités que les canaux nommés, mais nécessitent également moins de surcharge. Vous pouvez utiliser les canaux anonymes pour établir plus facilement une communication entre processus sur un ordinateur local. Vous ne pouvez pas utiliser les canaux anonymes pour la communication sur un réseau.  
  
 Pour implémenter des canaux anonymes, utilisez les classes <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream>.  
  
## <a name="example"></a>Exemple  

 L’exemple suivant montre une façon d’envoyer une chaîne à partir d’un processus parent à un processus enfant à l’aide de canaux anonymes. Cet exemple crée un objet <xref:System.IO.Pipes.AnonymousPipeServerStream> dans un processus parent avec une valeur <xref:System.IO.Pipes.PipeDirection> de <xref:System.IO.Pipes.PipeDirection.Out>. Le processus parent crée ensuite un processus enfant à l’aide d’un handle client pour créer un objet <xref:System.IO.Pipes.AnonymousPipeClientStream>. Le processus enfant a une valeur <xref:System.IO.Pipes.PipeDirection> de <xref:System.IO.Pipes.PipeDirection.In>.  
  
 Le processus parent envoie ensuite une chaîne fournie par l’utilisateur au processus enfant. La chaîne est affichée sur la console dans le processus enfant.  
  
 L’exemple suivant présente le processus serveur.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a>Exemple  

 L’exemple suivant présente le processus client. Le processus serveur démarre le processus client et donne à ce processus un handle client. Le fichier exécutable obtenu à partir du code client doit être nommé `pipeClient.exe` et être copié dans le même répertoire que l’exécutable serveur avant d’exécuter le processus serveur.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Voir aussi

- [Canaux](pipe-operations.md)
- [Procédure : utiliser des canaux nommés pour la communication entre processus en réseau](how-to-use-named-pipes-for-network-interprocess-communication.md)
