---
title: Sécurité des threads dans les expressions régulières
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: db25028e10872cfca08d28518c795414d06c5d49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124797"
---
# <a name="thread-safety-in-regular-expressions"></a>Sécurité des threads dans les expressions régulières
La classe <xref:System.Text.RegularExpressions.Regex> proprement dite est thread-safe et immuable (en lecture seule). Autrement dit, des objets **Regex** peuvent être créés sur n’importe quel thread et partagés par plusieurs threads ; les méthodes de mise en correspondance peuvent être appelées à partir de n’importe quel thread et elles ne modifient jamais un état global.  
  
 Toutefois, les objets de résultat (**Match** et **MatchCollection**) retournés par **Regex** doivent être utilisés sur un seul thread. Bien que bon nombre de ces objets soient logiquement immuables, leurs implémentations peuvent retarder le calcul de certains résultats pour améliorer les performances, et par conséquent, les appelants doivent en sérialiser l’accès.  
  
 S’il est nécessaire de partager des objets de résultat **Regex** sur plusieurs threads, ces objets peuvent être convertis en instances thread-safe en appelant leurs méthodes synchronisées. À l’exception des énumérateurs, toutes les classes d’expression régulière sont thread-safe ou peuvent être converties en objets thread-safe par une méthode synchronisée.  
  
 Les énumérateurs sont la seule exception. Une application doit sérialiser les appels aux énumérateurs de collections. La règle est que si une collection peut être énumérée simultanément sur plusieurs threads, vous devez synchroniser les méthodes d’énumération sur l’objet racine de la collection traversée par l’énumérateur.  
  
## <a name="see-also"></a>Voir aussi

- [Expressions régulières .NET](../../../docs/standard/base-types/regular-expressions.md)
