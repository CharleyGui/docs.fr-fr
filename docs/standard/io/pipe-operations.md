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
# <a name="pipe-operations-in-net"></a>Opérations de canal dans .NET
Les canaux sont un moyen de communication entre processus. Il existe deux types de canaux :  
  
- Canaux anonymes.  
  
     Les canaux anonymes fournissent une communication entre processus sur un ordinateur local. Les canaux anonymes nécessitent moins de traitement que les canaux nommés, mais ils offrent des services limités. Ils sont unidirectionnels et ne peuvent pas être utilisés sur un réseau. Ils prennent seulement en charge une instance de serveur. Les canaux anonymes sont utiles pour la communication entre threads, ou entre processus parents et enfants où les handles de canaux peuvent être facilement passés au processus enfant durant sa création.  
  
     Dans .NET, l’implémentation de canaux anonymes s’effectue avec les classes <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream>.  
  
     Consultez [Guide pratique pour utiliser des canaux anonymes pour la communication entre processus en local](how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Canaux nommés.  
  
     Les canaux nommés fournissent la communication entre un serveur de canaux et un ou plusieurs clients de canaux. Ils peuvent être unidirectionnels ou en duplex. Ils prennent en charge la communication basée sur les messages et permettent à plusieurs clients de se connecter simultanément au processus serveur à l’aide du même nom de canal. Les canaux nommés prennent également en charge l’emprunt d’identité, ce qui permet aux processus de connexion d’utiliser leurs propres autorisations sur des serveurs distants.  
  
     Dans .NET, l’implémentation de canaux nommés s’effectue avec les classes <xref:System.IO.Pipes.NamedPipeServerStream> et <xref:System.IO.Pipes.NamedPipeClientStream>.  
  
     Consultez [Comment : utiliser des canaux nommés pour la communication entre processus en réseau](how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Voir aussi

- [E/s de fichier et de flux](index.md)
- [Procédure : utiliser des canaux anonymes pour la communication entre processus en local](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Procédure : utiliser des canaux nommés pour la communication entre processus en réseau](how-to-use-named-pipes-for-network-interprocess-communication.md)
