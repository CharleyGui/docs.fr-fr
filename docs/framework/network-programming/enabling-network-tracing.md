---
title: Activation du suivi réseau
description: Découvrez comment activer le traçage réseau, qui fournit des informations sur les appels de méthode et le trafic réseau pour une application managée dans la .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- trace destinations
- sending traces to log file
- trace listeners, network tracing
- network tracing, enabling
- CLR Debugger
- default listeners
- logs, trace
- destination for tracing output
ms.assetid: 5fff458c-51a6-4134-ba47-8a6137ddc41e
ms.openlocfilehash: 4ad0b23fc93ddcdc11cebcc556d12148df5e8ae2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502598"
---
# <a name="enabling-network-tracing"></a>Activation du suivi réseau
Le traçage réseau fournit l’accès aux informations sur les appels de méthodes et le trafic réseau généré par une application managée. Vous devez effectuer les tâches suivantes pour activer le traçage réseau dans votre application :  
  
- Compiler votre code avec le traçage activé. Pour plus d’informations sur les commutateurs du compilateur nécessaires pour activer le traçage, consultez [Guide pratique pour effectuer une compilation conditionnelle avec Trace et Debug](../debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md).  
  
- Spécifier une destination de sortie de traçage.  
  
- Configurer le comportement du traçage réseau. Pour obtenir des informations détaillées, consultez [Guide pratique pour configurer le traçage réseau](how-to-configure-network-tracing.md).  
  
 Les destinations de trace les plus courantes, également appelées écouteurs de suivi, sont l’écouteur par défaut et le fichier journal.  
  
 Le traçage utilise l’écouteur par défaut si vous ne spécifiez pas d’écouteur de suivi. Vous pouvez afficher les messages envoyés à l’écouteur par défaut en exécutant votre code dans un débogueur compatible avec le code managé tel que le débogueur CLR fourni avec le SDK .NET Framework ou DBwin32.exe fourni avec le SDK Windows. Avec le débogueur CLR, les messages de trace s’affichent dans la fenêtre **Sortie**.  
  
 Si vous préférez utiliser un fichier pour recevoir des traces, vous pouvez spécifier un fichier journal à l’aide des paramètres de configuration, comme indiqué dans l’exemple suivant. (Pour obtenir une présentation générale des fichiers de configuration, consultez [Fichiers de configuration](../configure-apps/index.md).)  
  
 Pour envoyer des traces vers un fichier journal, ajoutez le nœud suivant au nœud `<system.diagnostics>` du fichier de configuration approprié (application ou ordinateur). Vous pouvez modifier le nom du fichier (trace.log) en fonction de vos besoins.  
  
```xml  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>
  </trace>  
</system.diagnostics>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Interprétation du suivi réseau](interpreting-network-tracing.md)
- [Traçage réseau dans .NET Framework](network-tracing.md)
- [Traçage et instrumentation d'applications](../debug-trace-profile/tracing-and-instrumenting-applications.md)
