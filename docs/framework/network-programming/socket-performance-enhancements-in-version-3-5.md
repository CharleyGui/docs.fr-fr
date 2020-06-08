---
title: Améliorations des performances de socket dans la version 3.5
description: Découvrez les améliorations des performances de la classe System .net. Sockets. Socket dans la version 3,5 dans le .NET Framework.
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 5a640c58e47bf1630a3a551aed72b9bc9d4fd6fe
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502143"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Améliorations des performances de socket dans la version 3.5
La classe <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> a été améliorée dans la version 3.5 pour les applications qui utilisent des E/S réseau asynchrones pour optimiser les performances. Dans le cadre d’un ensemble d’améliorations apportées à la classe <xref:System.Net.Sockets.Socket>, plusieurs nouvelles classes ont été ajoutées pour fournir un autre modèle asynchrone pouvant être utilisé par les applications de socket hautes performances spécialisées. Ces améliorations ont été spécialement conçues pour les applications serveur réseau qui nécessitent un niveau de performance élevé. Une application peut utiliser exclusivement le modèle asynchrone amélioré, ou l’utiliser seulement dans des zones ciblées de l’application (lors de la réception de grandes quantités de données, par exemple).  
  
## <a name="class-enhancements"></a>Améliorations de la classe  
 L’objectif principal de ces améliorations est d’éviter la répétition des opérations d’allocation et de synchronisation d’objets durant les processus impliquant de nombreuses entrées/sorties de socket asynchrones. Le modèle de conception Begin/End actuellement implémenté par la classe <xref:System.Net.Sockets.Socket> pour les entrées/sorties asynchrones nécessite l’allocation d’un objet <xref:System.IAsyncResult?displayProperty=nameWithType> pour chaque opération de socket asynchrone.  
  
 Dans la classe <xref:System.Net.Sockets.Socket> améliorée, les opérations de socket asynchrones sont décrites par des objets de la classe <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> réutilisables qui sont alloués et gérés par l’application. Les applications de socket à hautes performances peuvent ainsi mieux évaluer le nombre d’opérations de socket superposées à conserver. L’application peut créer autant d’objets <xref:System.Net.Sockets.SocketAsyncEventArgs> qu’elle a besoin. Par exemple, si une application serveur doit toujours avoir 15 opérations d’acceptation de socket en attente pour prendre en charge toutes les connexions client entrantes, elle peut préalablement allouer 15 objets <xref:System.Net.Sockets.SocketAsyncEventArgs> réutilisables à cette fin.  
  
 Le modèle pour effectuer une opération de socket asynchrone avec cette classe comprend les étapes suivantes :  
  
1. Allouer un nouvel objet de contexte <xref:System.Net.Sockets.SocketAsyncEventArgs>, ou en obtenir un gratuitement à partir d’un pool d’applications.  
  
2. Définir les propriétés de l’objet de contexte pour l’opération à effectuer (la méthode déléguée de rappel et le tampon de données, par exemple).  
  
3. Appeler la méthode de socket appropriée (xxxAsync) pour lancer l’opération asynchrone.  
  
4. Si la méthode de socket asynchrone (xxxAsync) retourne la valeur true dans le rappel, obtenir les propriétés de contexte pour connaître l’état de complétion.  
  
5. Si la méthode de socket asynchrone (xxxAsync) retourne la valeur false dans le rappel, l’opération a été effectuée de façon synchrone. L’obtention des propriétés de contexte peut être nécessaire pour le résultat de l’opération.  
  
6. Réutiliser le contexte pour une autre opération, le replacer dans le pool ou le supprimer.  
  
 La durée de vie du nouvel objet de contexte de l’opération de socket asynchrone est déterminée par les références dans le code d’application et par les références aux E/S asynchrones. L’application n’a pas besoin de conserver de référence à un objet de contexte de l’opération de socket asynchrone une fois qu’elle a été transmise comme paramètre à l’une des méthodes de l’opération de socket asynchrone. La référence est conservée jusqu’au retour du rappel d’achèvement. Toutefois, l’application peut conserver la référence à l’objet de contexte pour la réutiliser lors d’une opération de socket asynchrone ultérieure.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [Exemples de programmation réseau](network-programming-samples.md)
- [Exemples de code de socket](socket-code-examples.md)
