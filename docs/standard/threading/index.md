---
title: Threading managé
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: e4c19b664e8fc040fdc4a284b30f6104d676088d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279152"
---
# <a name="managed-threading"></a>Threading managé
Que votre développement s’applique à des ordinateurs avec un ou plusieurs processeurs, votre application doit fournir l’interaction la plus réactive avec l’utilisateur, même si l’application effectue actuellement d’autres opérations. Utiliser plusieurs threads d’exécution est l’une des manières les plus efficaces pour maintenir la réactivité de votre application vis-à-vis de l’utilisateur, tout en exploitant le processeur entre voire pendant des événements utilisateur. Bien que cette section présente les concepts de base du threading, elle se concentre sur les concepts de threading managé et son utilisation.  
  
> [!NOTE]
> À compter de .NET Framework 4, la programmation multithread est considérablement simplifiée avec les classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), de nouvelles classes de collections simultanées dans l’espace de noms <xref:System.Collections.Concurrent?displayProperty=nameWithType> et un nouveau modèle de programmation basé sur le concept de tâches au lieu de threads. Pour plus d’informations, consultez [programmation parallèle](../parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Concepts de base du threading managé](managed-threading-basics.md)  
 Fournit une vue d’ensemble des threads managés et explique quand utiliser plusieurs threads.  
  
 [Utilisation des threads et du threading](using-threads-and-threading.md)  
 Explique comment créer, démarrer, suspendre, reprendre et abandonner des threads.  
  
 [Meilleures pratiques pour le threading managé](managed-threading-best-practices.md)  
 Décrit les niveaux de synchronisation, comment éviter les interblocages et les conditions de concurrence, et d’autres problèmes liés aux threads.  
  
 [Objets et fonctionnalités de Threading](threading-objects-and-features.md)  
 Décrit les classes managées que vous pouvez utiliser pour synchroniser les activités de threads et les données d’objets ouvertes sur différents threads, et fournit une vue d’ensemble des threads du pool.  
  
## <a name="reference"></a>Référence  
 <xref:System.Threading>  
 Contient des classes pour l’utilisation et la synchronisation de threads managés.  
  
 <xref:System.Collections.Concurrent>  
 Contient des classes de collection qui peuvent être utilisées en toute sécurité avec plusieurs threads.  
  
 <xref:System.Threading.Tasks>  
 Contient des classes pour la création et la planification de tâches de traitement simultanées.  
  
## <a name="related-sections"></a>Sections connexes  
 [Domaines d'application](../../framework/app-domains/application-domains.md)  
 Fournit une vue d'ensemble des domaines d'application et de leur utilisation dans le Common Language Infrastructure.  
  
 [E/s de fichier asynchrones](../io/asynchronous-file-i-o.md)  
 Décrit les opérations élémentaires des E/S asynchrones et leurs avantages en termes de performances.  
  
 [Modèle asynchrone basé sur les tâches (TAP, Task-based Asynchronous Pattern)](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 Offre une vue d’ensemble du modèle recommandé pour la programmation asynchrone dans .NET.  
  
 [Appel de méthodes synchrones de manière asynchrone](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Explique comment appeler des méthodes sur les threads d’un pool à l’aide des fonctionnalités intégrées des délégués.  
  
 [Programmation parallèle](../parallel-programming/index.md)  
 Décrit les bibliothèques de programmation parallèle qui simplifient l’utilisation de plusieurs threads dans les applications.  
  
 [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md)  
 Décrit un système permettant d’exécuter des requêtes en parallèle afin de tirer parti de plusieurs processeurs.
