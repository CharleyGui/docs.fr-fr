---
title: Sockets
description: En savoir plus sur la classe de Socket .NET Framework, qui est une version de code managé des services de socket fournis par l’API Winsock32.
ms.date: 03/30/2017
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- Windows Sockets
- sockets, about sockets
- Socket class, about Socket class
- sockets
- requesting data from Internet, sockets
- network, sockets
- receiving data, sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 10d22735-bd37-42c1-a2be-c1932f979a7d
ms.openlocfilehash: e00d04164f7ce5251b7f30b5abd16c14643f6862
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263124"
---
# <a name="sockets"></a>Sockets

L’espace de noms <xref:System.Net.Sockets> contient une implémentation managée de l’interface Windows Sockets. Toutes les autres classes d’accès réseau dans l’espace de noms <xref:System.Net> s’appuient sur cette implémentation de sockets.  
  
 La classe <xref:System.Net.Sockets.Socket> du .NET Framework est une version de code managé des services de socket fournis par l’API Winsock32. Dans la plupart des cas, les méthodes de la classe **Socket** ne font que marshaler les données dans leurs équivalents Win32 natifs et gérer les vérifications de sécurité nécessaires.  
  
 La classe **Socket** prend en charge deux modes de base : le mode synchrone et le mode asynchrone. En mode synchrone, les appels aux fonctions qui effectuent des opérations réseau (telles que <xref:System.Net.Sockets.Socket.Send%2A> et <xref:System.Net.Sockets.Socket.Receive%2A>) attendent que l’opération soit terminée avant de restituer le contrôle au programme appelant. En mode asynchrone, ces appels retournent immédiatement.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : créer un socket](how-to-create-a-socket.md)

- [Utilisation de protocoles d’application](using-application-protocols.md)
