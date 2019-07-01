---
title: 'Procédure : utiliser des canaux nommés pour la communication entre processus en réseau'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ddd862480a5977a4bada17945e10a25753b44de4
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402497"
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a>Procédure : utiliser des canaux nommés pour la communication entre processus en réseau
Les canaux nommés fournissent la communication entre un serveur de canaux et un ou plusieurs clients de canaux. Ils offrent plus de fonctionnalités que les canaux anonymes, qui fournissent la communication entre processus sur un ordinateur local. Les canaux nommés prennent en charge la communication en duplex intégrale sur un réseau et plusieurs instances de serveur, la communication basée sur message et l’emprunt d’identité du client, ce qui permet aux processus de connexion d’utiliser leur propre jeu d’autorisations sur des serveurs distants.  
  
 Pour implémenter des canaux nommés, utilisez les classes <xref:System.IO.Pipes.NamedPipeServerStream> et <xref:System.IO.Pipes.NamedPipeClientStream>.  
  
## <a name="example"></a>Exemples  
 L’exemple suivant illustre la création d’un canal nommé à l’aide de la classe <xref:System.IO.Pipes.NamedPipeServerStream>. Dans cet exemple, le processus serveur crée quatre threads. Chaque thread peut accepter une connexion cliente. Le processus client connecté fournit ensuite au serveur un nom de fichier. Si le client dispose des autorisations suffisantes, le processus serveur ouvre le fichier et renvoie son contenu au client.  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a>Exemples  
 L’exemple suivant présente le processus client, qui utilise la classe <xref:System.IO.Pipes.NamedPipeClientStream>. Le client se connecte au processus serveur et envoie un nom de fichier au serveur. L’exemple utilise l’emprunt d’identité, donc l’identité qui exécute l’application cliente doit avoir l’autorisation d’accéder au fichier. Le serveur renvoie ensuite le contenu du fichier au client. Le contenu du fichier est ensuite affiché sur la console.  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les processus client et serveur dans cet exemple sont censés être exécutés sur le même ordinateur, donc le nom du serveur fourni à l’objet <xref:System.IO.Pipes.NamedPipeClientStream> est `"."`. Si les processus client et serveur se trouvent sur des ordinateurs distincts, `"."` est remplacé par le nom réseau de l’ordinateur qui exécute le processus serveur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Principal.TokenImpersonationLevel>
- <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>
- [Canaux](../../../docs/standard/io/pipe-operations.md)
- [Guide pratique pour utiliser des canaux anonymes pour la communication entre processus en local](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
