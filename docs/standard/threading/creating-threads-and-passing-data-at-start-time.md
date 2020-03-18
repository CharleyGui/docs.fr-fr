---
title: Création de threads et passage de données au démarrage
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
ms.openlocfilehash: a628cbb4c9ec8e1c9ccd9fd73e72a82ecf2b2836
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138101"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a>Création de threads et passage de données au démarrage

Lorsqu’un processus de système d’exploitation est créé, le système d’exploitation injecte un thread pour exécuter du code dans ce processus, y compris un domaine d’application d’origine. À ce stade, des domaines d’application peuvent être créés et détruits sans nécessairement avoir à créer ou à détruire des threads de système d’exploitation. Si le code en cours d’exécution est un code géré, un objet <xref:System.Threading.Thread> pour le thread s’exécutant dans le domaine d’application actuel peut être obtenu en récupérant la propriété statique <xref:System.Threading.Thread.CurrentThread%2A> de type <xref:System.Threading.Thread>. Cette rubrique décrit la création de threads et présente des alternatives pour transmettre des données à la procédure de thread.  
  
## <a name="creating-a-thread"></a>Création d’un thread

 La création d’un nouvel objet <xref:System.Threading.Thread> entraîne la création d’un thread managé. La classe <xref:System.Threading.Thread> a des constructeurs qui acceptent un délégué <xref:System.Threading.ThreadStart> ou <xref:System.Threading.ParameterizedThreadStart> ; le délégué inclut dans un wrapper la méthode qui est appelée par le nouveau thread lorsque vous appelez la méthode <xref:System.Threading.Thread.Start%2A>. L’appel de <xref:System.Threading.Thread.Start%2A> plus d’une fois entraîne la levée d’une <xref:System.Threading.ThreadStateException>.  
  
 La méthode <xref:System.Threading.Thread.Start%2A> est retournée immédiatement, souvent avant que le nouveau thread n’ait réellement démarré. Vous pouvez utiliser les propriétés <xref:System.Threading.Thread.ThreadState%2A> et <xref:System.Threading.Thread.IsAlive%2A> pour déterminer l’état du thread à tout moment, mais ces propriétés ne doivent jamais être utilisées pour synchroniser les activités de threads.  
  
> [!NOTE]
> Une fois qu’un thread a démarré, il n’est pas nécessaire de conserver une référence à l’objet <xref:System.Threading.Thread>. Le thread continue à s’exécuter jusqu'à la fin de la procédure de thread.  
  
 L’exemple de code suivant crée deux nouveaux threads pour appeler des méthodes statiques et d’instance sur un autre objet.  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a>Passage de données à des threads

 Dans la version 2.0 de .NET Framework, le délégué <xref:System.Threading.ParameterizedThreadStart> permet de transmettre facilement un objet contenant des données à un thread lorsque vous appelez la surcharge de la méthode <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>. Pour obtenir un exemple de code, consultez <xref:System.Threading.ParameterizedThreadStart>.  
  
 L’utilisation du délégué <xref:System.Threading.ParameterizedThreadStart> n’est pas une méthode de type sécurisé pour transmettre des données, car la surcharge de la méthode <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> accepte tous les objets. Une alternative consiste à encapsuler la procédure de thread et les données dans une classe d’assistance et à utiliser le délégué <xref:System.Threading.ThreadStart> pour exécuter la procédure de thread. L’exemple suivant montre cette technique :

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

Ni le délégué <xref:System.Threading.ThreadStart> ni le délégué <xref:System.Threading.ParameterizedThreadStart> n’ont de valeur de retour, car il n’existe pas d’endroit où retourner les données provenant d’un appel asynchrone. Pour récupérer les résultats d’une méthode de thread, vous pouvez utiliser une méthode de rappel, comme montré dans la section suivante.
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a>Récupération de données provenant de threads avec des méthodes de rappel

 L’exemple suivant montre une méthode de rappel qui récupère des données à partir d’un thread. Le constructeur de la classe qui contient les données et la méthode de thread accepte également un délégué représentant la méthode de rappel ; avant la fin de la méthode de thread, il appelle le délégué de rappel.  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [Thread](index.md)
- [Utilisation des threads et du threading](using-threads-and-threading.md)
