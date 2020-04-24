---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 7934dcaada4675bf687624bef5ed1ea25e842832
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344249"
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)
Indique si un exécutable 64 bits ou un exécutable marqué par l’option [de compilateur-Platform : AnyCPU](../../../visual-basic/reference/command-line-compiler/platform.md) prend en charge la randomisation du format d’espace d’adresse (ASLR) de forte entropie.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Facultatif. L’option est désactivée par défaut ou si `-highentropyva-`vous spécifiez. L’option est activée si vous `-highentropyva` spécifiez `-highentropyva+`ou.  
  
## <a name="remarks"></a>Notes  
 Si vous spécifiez cette option, les versions compatibles du noyau Windows peuvent utiliser un degré d’entropie plus élevé lorsque le noyau rend aléatoire la disposition de l’espace d’adressage d’un processus dans le cadre de l’ASLR. Si le noyau utilise un degré d’entropie plus élevé, un plus grand nombre d’adresses peuvent être allouées aux régions de mémoire, telles que les piles et les tas. Par conséquent, il est plus difficile de deviner l’emplacement d’une zone de mémoire.  
  
 Lorsque l’option est activée, l’exécutable cible et tous les modules dont il dépend doivent être en mesure de gérer les valeurs de pointeur supérieures à 4 gigaoctets (Go) lorsque ces modules s’exécutent en tant que processus 64 bits.  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
