---
title: Optimisation de l'hébergement Web partagé
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
ms.openlocfilehash: 6398c6749028827e5e3ee79a5511ac0879facbef
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824465"
---
# <a name="optimization-for-shared-web-hosting"></a>Optimisation de l'hébergement Web partagé
Si vous êtes l’administrateur d’un serveur qui est partagé via l’hébergement de plusieurs petits sites web, vous pouvez optimiser les performances et augmenter la capacité du site en ajoutant le paramètre `gcTrimCommitOnLowMemory` suivant au nœud `runtime` dans le fichier Aspnet.config dans le répertoire .NET :  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
> Ce paramètre n’est recommandé que dans les scénarios d’hébergement web partagé.  
  
 Étant donné que le récupérateur de mémoire conserve de la mémoire pour les répartitions futures, l’espace alloué peut être supérieur à ce qui est strictement nécessaire. Vous pouvez réduire cet espace en cas de charge importante sur la mémoire système. La réduction de cet espace alloué améliore les performances et développe la capacité à héberger plusieurs sites.  
  
 Lorsque le paramètre `gcTrimCommitOnLowMemory` est activé, le récupérateur de mémoire évalue la charge de la mémoire système et entre en mode de suppression lorsque la charge atteint 90 %. Il conserve le mode de suppression jusqu'à ce que la charge soit inférieure à 85 %.  
  
 Lorsque les conditions le permettent, le récupérateur de mémoire peut décider que le paramètre `gcTrimCommitOnLowMemory` n’aidera pas l’application actuelle et l’ignorer.  
  
## <a name="example"></a>Exemple  
 Le fragment XML suivant montre comment activer le paramètre `gcTrimCommitOnLowMemory`. Les points de suspension indiquent d’autres paramètres dans le nœud `runtime`.  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Garbage collection](index.md)
