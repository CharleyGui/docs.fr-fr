---
title: Threads de premier plan et d'arrière-plan
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 5e7ec9e2c2a5ba3de1b4518cea15eb5f512640d3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279683"
---
# <a name="foreground-and-background-threads"></a>Threads de premier plan et d'arrière-plan
Un thread managé est un thread d’arrière-plan ou un thread de premier plan. Les threads d’arrière-plan sont identiques aux threads de premier plan à une exception près : un thread d’arrière-plan ne permet pas de poursuivre l’exécution de l’environnement d’exécution managé. Une fois que tous les threads de premier plan ont été arrêtés dans un processus managé (où le fichier .exe est un assembly managé), le système arrête tous les threads d’arrière-plan et se ferme.  
  
> [!NOTE]
> Lorsque le runtime arrête un thread d’arrière-plan parce que le processus est en cours d’arrêt, aucune exception n’est levée dans le thread. Toutefois, lorsque des threads sont arrêtés parce que la méthode <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> décharge le domaine d’application, une <xref:System.Threading.ThreadAbortException> est levée dans les threads de premier plan et d’arrière-plan.  
  
 Utilisez la propriété <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> pour déterminer si un thread est un thread d’arrière-plan ou de premier plan, ou pour modifier son état. Un thread peut être transformé en thread d’arrière-plan à tout moment en définissant sa propriété <xref:System.Threading.Thread.IsBackground%2A> sur `true`.  
  
> [!IMPORTANT]
> L’état de premier plan ou d’arrière-plan d’un thread n’affecte pas le résultat d’une exception non prise en charge dans le thread. Dans la version 2.0 de .NET Framework, une exception non prise en charge dans les threads de premier plan ou d’arrière-plan entraîne l’arrêt de l’application. Voir [Exceptions dans les threads managés](exceptions-in-managed-threads.md).  
  
 Les threads qui font partie du pool de threads managés (autrement dit, les threads dont la propriété <xref:System.Threading.Thread.IsThreadPoolThread%2A> est `true`) sont des threads d’arrière-plan. Tous les threads qui entrent dans l’environnement d’exécution managé à partir de code non managé sont marqués comme threads d’arrière-plan. Tous les threads générés en créant et en démarrant un nouvel objet <xref:System.Threading.Thread> sont par défaut des threads de premier plan.  
  
 Si vous utilisez un thread pour surveiller une activité, telle qu’une connexion de socket, définissez sa propriété <xref:System.Threading.Thread.IsBackground%2A> sur `true` afin que le thread n’empêche pas votre processus de s’arrêter.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
