---
title: Sécurité des threads dans les expressions régulières
ms.date: 03/30/2017
ms.topic: conceptual
helpviewer_keywords:
- .NET regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: 4be73ba89ff7114c52394ab23a8de02adb35e0e2
ms.sourcegitcommit: 4313614f57690f9a5119a37314f0a1fd738ebda2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98692550"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="1dd5b-102">Sécurité des threads dans les expressions régulières</span><span class="sxs-lookup"><span data-stu-id="1dd5b-102">Thread Safety in Regular Expressions</span></span>

<span data-ttu-id="1dd5b-103">La classe <xref:System.Text.RegularExpressions.Regex> proprement dite est thread-safe et immuable (en lecture seule).</span><span class="sxs-lookup"><span data-stu-id="1dd5b-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="1dd5b-104">Autrement dit, des objets **Regex** peuvent être créés sur n’importe quel thread et partagés par plusieurs threads ; les méthodes de mise en correspondance peuvent être appelées à partir de n’importe quel thread et elles ne modifient jamais un état global.</span><span class="sxs-lookup"><span data-stu-id="1dd5b-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="1dd5b-105">Toutefois, les objets de résultat (**Match** et **MatchCollection**) retournés par **Regex** doivent être utilisés sur un seul thread.</span><span class="sxs-lookup"><span data-stu-id="1dd5b-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="1dd5b-106">Bien que bon nombre de ces objets soient logiquement immuables, leurs implémentations peuvent retarder le calcul de certains résultats pour améliorer les performances, et par conséquent, les appelants doivent en sérialiser l’accès.</span><span class="sxs-lookup"><span data-stu-id="1dd5b-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="1dd5b-107">S’il est nécessaire de partager des objets de résultat **Regex** sur plusieurs threads, ces objets peuvent être convertis en instances thread-safe en appelant leurs méthodes synchronisées.</span><span class="sxs-lookup"><span data-stu-id="1dd5b-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="1dd5b-108">À l’exception des énumérateurs, toutes les classes d’expression régulière sont thread-safe ou peuvent être converties en objets thread-safe par une méthode synchronisée.</span><span class="sxs-lookup"><span data-stu-id="1dd5b-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="1dd5b-109">Les énumérateurs sont la seule exception.</span><span class="sxs-lookup"><span data-stu-id="1dd5b-109">Enumerators are the only exception.</span></span> <span data-ttu-id="1dd5b-110">Une application doit sérialiser les appels aux énumérateurs de collections.</span><span class="sxs-lookup"><span data-stu-id="1dd5b-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="1dd5b-111">La règle est que si une collection peut être énumérée simultanément sur plusieurs threads, vous devez synchroniser les méthodes d’énumération sur l’objet racine de la collection traversée par l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="1dd5b-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd5b-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dd5b-112">See also</span></span>

- [<span data-ttu-id="1dd5b-113">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="1dd5b-113">.NET Regular Expressions</span></span>](regular-expressions.md)
