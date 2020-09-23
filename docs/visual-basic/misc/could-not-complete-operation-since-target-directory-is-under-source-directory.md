---
title: Impossible d’achever l’opération, car le répertoire cible se situe sous le répertoire source
ms.date: 07/20/2015
f1_keywords:
- vbrIO_CyclicOperation
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
ms.openlocfilehash: d159b9bb3a765a2fefe99fa15dff42e979fda9e3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079137"
---
# <a name="could-not-complete-operation-since-target-directory-is-under-source-directory"></a>Impossible d’achever l’opération, car le répertoire cible se situe sous le répertoire source

Une opération cyclique a échoué. Les opérations cycliques se répètent et, par conséquent, ne peuvent pas s’achever. Par exemple, l’objet A peut essayer d’hériter de l’objet B qui hérite, à son tour, de l’objet A.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Lors d’un héritage, vérifiez qu’il n’existe aucune référence cyclique.  
  
## <a name="see-also"></a>Voir aussi

- [Types d’erreurs](../programming-guide/language-features/error-types.md)
- [Utiliser des points d’arrêt dans le débogueur Visual Studio](/visualstudio/debugger/using-breakpoints)
