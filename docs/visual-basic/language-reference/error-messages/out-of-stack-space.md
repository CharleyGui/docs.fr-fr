---
title: Espace de pile insuffisant
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349180"
---
# <a name="out-of-stack-space-visual-basic"></a>Espace de pile insuffisant (Visual Basic)
La pile est une zone de travail de la mémoire qui augmente et diminue de manière dynamique avec les demandes de votre programme en cours d’exécution. Ses limites ont été dépassées.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Vérifiez que les procédures ne sont pas imbriquées trop profondément.  
  
2. Vérifiez que les procédures récursives se terminent correctement.  
  
3. Si les variables locales requièrent plus d’espace de variable locale que le nombre disponible, essayez de déclarer des variables au niveau du module. Vous pouvez également déclarer toutes les variables de la procédure statique en faisant précéder le mot clé `Property`, `Sub`ou `Function` par `Static`. Vous pouvez utiliser l’instruction `Static` pour déclarer des variables statiques individuelles dans des procédures.  
  
4. Redéfinissez certaines chaînes de longueur fixe en tant que chaînes de longueur variable, car les chaînes de longueur fixe utilisent plus d’espace de pile que les chaînes de longueur variable. Vous pouvez également définir la chaîne au niveau du module, où elle ne requiert aucun espace de pile.  
  
5. Vérifiez le nombre d’appels de fonction `DoEvents` imbriqués, à l’aide de la boîte de dialogue `Calls` pour afficher les procédures actives sur la pile.  
  
6. Assurez-vous que vous n’avez pas provoqué une « cascade d’événements » en déclenchant un événement qui appelle une procédure d’événement déjà sur la pile. Une cascade d’événements est similaire à un appel de procédure récursive inachevé, mais elle est moins évidente, puisque l’appel est effectué par Visual Basic plutôt qu’un appel explicite dans le code. Utilisez la boîte de dialogue `Calls` pour afficher les procédures actives sur la pile.  
  
## <a name="see-also"></a>Voir aussi

- [Fenêtres Mémoire](/visualstudio/debugger/memory-windows)
