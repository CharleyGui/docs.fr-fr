---
title: Compilation et réutilisation dans les expressions régulières
ms.date: 03/30/2017
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET regular expressions, engines
- .NET regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
ms.openlocfilehash: f0da4a226feb6bafc7e17c7333cbc507701311af
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823106"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Compilation et réutilisation dans les expressions régulières
Vous pouvez optimiser les performances des applications qui utilisent très souvent des expressions régulières en comprenant comment le moteur d’expression régulière compile les expressions et comment les expressions régulières sont mises en cache. Cette rubrique décrit la compilation et la mise en cache.  
  
## <a name="compiled-regular-expressions"></a>Expressions régulières compilées  
 Par défaut, le moteur d’expression régulière compile une expression régulière en une séquence d’instructions internes (il s’agit des codes généraux différents de MSIL, ou Microsoft Intermediate Language). Quand le moteur exécute une expression régulière, il interprète les codes internes.  
  
 Si un objet <xref:System.Text.RegularExpressions.Regex> est construit avec l’option <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>, il compile l’expression régulière en code MSIL explicite plutôt qu’en instructions internes d’expression régulière générale. Ainsi, le compilateur juste-à-temps (JIT) de .NET convertit l’expression en code machine natif pour de meilleures performances.  Le coût de la construction de l' <xref:System.Text.RegularExpressions.Regex> objet peut être plus élevé, mais le coût lié à l’exécution de correspondances est probablement plus petit.

 Une alternative serait d’utiliser des expressions régulières précompilées. Vous pouvez compiler l’ensemble de vos expressions dans une DLL réutilisable à l’aide de la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A>. Cela évite de devoir compiler au moment de l’exécution tout en bénéficiant de la vitesse des expressions régulières compilées.  
  
## <a name="the-regular-expressions-cache"></a>Cache des expressions régulières  
 Pour améliorer les performances, le moteur d’expression régulière gère un cache à l’échelle de l’application des expressions régulières compilées. Ce cache stocke les modèles d’expression régulière utilisés uniquement dans les appels de méthode statique. (Les modèles d’expression régulière fournis aux méthodes d’instance ne sont pas mis en cache.) Cela évite de devoir réanalyser une expression en code d’octet de haut niveau chaque fois qu’elle est utilisée.  
  
 Le nombre maximal d’expressions régulières mises en cache est déterminé par la valeur de la propriété <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType>`static` (`Shared` en Visual Basic). Par défaut, le moteur d’expression régulière met en cache jusqu’à 15 expressions régulières compilées. Si le nombre d’expressions régulières compilées dépasse la taille du cache, l’expression régulière la plus anciennement utilisée est ignorée et la nouvelle expression régulière est mise en cache.  
  
 Votre application peut réutiliser des expressions régulières de l’une des deux manières suivantes :  
  
- En utilisant une méthode statique de l’objet <xref:System.Text.RegularExpressions.Regex> pour définir l’expression régulière. Si vous utilisez un modèle d’expression régulière qui a déjà été défini par un autre appel de méthode statique, le moteur d’expression régulière essaiera de le récupérer à partir du cache. S’il n’est pas disponible dans le cache, le moteur compile l’expression régulière et l’ajoute au cache.
  
- En réutilisant un objet <xref:System.Text.RegularExpressions.Regex> existant tant que son modèle d’expression régulière est nécessaire.  
  
 En raison de la surcharge liée à l’instanciation d’objets et à la compilation d’expressions régulières, la création et la destruction rapide d’un grand nombre d’objets <xref:System.Text.RegularExpressions.Regex> est un processus très coûteux. Pour les applications qui utilisent un grand nombre d’expressions régulières différentes, vous pouvez optimiser les performances en utilisant des appels de méthodes `Regex` statiques et en augmentant éventuellement la taille du cache des expressions régulières.  
  
## <a name="see-also"></a>Voir aussi

- [Expressions régulières .NET](regular-expressions.md)
