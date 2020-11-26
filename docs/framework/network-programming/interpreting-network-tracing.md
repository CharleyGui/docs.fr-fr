---
title: Interprétation du traçage réseau
description: Découvrez comment utiliser le suivi pour capturer les appels effectués par votre application à différents membres de la classe System.Net dans le .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 63d7e36bb95054303fc4f26b0fd14dc3d10dbb7d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241562"
---
# <a name="interpreting-network-tracing"></a>Interprétation du traçage réseau

Quand le traçage réseau est activé, vous pouvez utiliser cette fonctionnalité pour capturer les appels effectués par votre application aux différents membres de la classe <xref:System.Net>. La sortie de ces appels peut ressembler aux exemples suivants.  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 Dans l’exemple précédent, [588] est l’identificateur unique du thread actuel. (4357) et (4387) sont des timestamps qui indiquent le nombre de millisecondes écoulées depuis le démarrage de l’application. Les données après les timestamps montrent l’entrée et la sortie de la méthode **Socket.Send** dans l’application. L’objet qui exécute la méthode **Send** a la valeur 33574638 comme identificateur unique. La trace de sortie de la méthode inclut la valeur de retour (61 dans l’exemple précédent).  
  
 Les traces réseau peuvent capturer le trafic réseau qui transite par votre application à l’aide de protocoles de niveau application comme le protocole HTTP. Ces données sont capturées au format texte et, éventuellement, au format hexadécimal. Les données hexadécimales sont disponibles si vous spécifiez la valeur **includehex** pour l’attribut **tracemode**. (Pour plus d’informations sur cet attribut, consultez [procédure : configurer le traçage réseau](how-to-configure-network-tracing.md).) L’exemple de trace suivant a été généré à l’aide de **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Pour omettre les données hexadécimales, spécifiez la valeur **protocolonly** pour l’attribut **tracemode**. L’exemple de trace suivant a été généré avec la valeur **protocolonly**.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Voir aussi

- [Activation du suivi réseau](enabling-network-tracing.md)
- [Procédure : configurer le traçage réseau](how-to-configure-network-tracing.md)
- [Traçage réseau dans le .NET Framework](network-tracing.md)
