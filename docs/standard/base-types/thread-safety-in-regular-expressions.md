---
title: Sécurité des threads dans les expressions régulières
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: 29ff647d623c047c63c52732a3e8bce5f0e95d6c
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889281"
---
# <a name="thread-safety-in-regular-expressions"></a>Sécurité des threads dans les expressions régulières
La classe <xref:System.Text.RegularExpressions.Regex> proprement dite est thread-safe et immuable (en lecture seule). Autrement dit, des objets **Regex** peuvent être créés sur n’importe quel thread et partagés par plusieurs threads ; les méthodes de mise en correspondance peuvent être appelées à partir de n’importe quel thread et elles ne modifient jamais un état global.  
  
 Toutefois, les objets de résultat ( **Match** et **MatchCollection** ) retournés par **Regex** doivent être utilisés sur un seul thread. Bien que bon nombre de ces objets soient logiquement immuables, leurs implémentations peuvent retarder le calcul de certains résultats pour améliorer les performances, et par conséquent, les appelants doivent en sérialiser l’accès.  
  
 S’il est nécessaire de partager des objets de résultat **Regex** sur plusieurs threads, ces objets peuvent être convertis en instances thread-safe en appelant leurs méthodes synchronisées. À l’exception des énumérateurs, toutes les classes d’expression régulière sont thread-safe ou peuvent être converties en objets thread-safe par une méthode synchronisée.  
  
 Les énumérateurs sont la seule exception. Une application doit sérialiser les appels aux énumérateurs de collections. La règle est que si une collection peut être énumérée simultanément sur plusieurs threads, vous devez synchroniser les méthodes d’énumération sur l’objet racine de la collection traversée par l’énumérateur.  
  
## <a name="see-also"></a>Voir aussi

- [Expressions régulières .NET](regular-expressions.md)
