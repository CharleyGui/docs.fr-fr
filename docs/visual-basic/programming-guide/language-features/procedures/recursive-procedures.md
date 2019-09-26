---
title: Procédures récursives (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: b08a06a07f134b7c95251848862d39339e59fe61
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274342"
---
# <a name="recursive-procedures-visual-basic"></a>Procédures récursives (Visual Basic)

Une procédure *récursive* est une procédure qui s’appelle elle-même. En général, il ne s’agit pas de la méthode la plus efficace pour écrire du code Visual Basic.  
  
 La procédure suivante utilise la récursivité pour calculer la factorielle de son argument d’origine.  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a>Considérations relatives aux procédures récursives

 **Limitation des conditions**. Vous devez concevoir une procédure récursive pour tester au moins une condition qui peut mettre fin à la récursivité, et vous devez également gérer le cas où aucune condition n’est satisfaite dans un nombre raisonnable d’appels récursifs. Si au moins une condition peut être remplie sans échouer, votre procédure exécute un risque élevé d’exécution dans une boucle infinie.

 **Utilisation de la mémoire**. Votre application dispose d’une quantité limitée d’espace pour les variables locales. Chaque fois qu’une procédure s’appelle elle-même, elle utilise plus d’espace pour les copies supplémentaires de ses variables locales. Si ce processus se poursuit indéfiniment, il est <xref:System.StackOverflowException> finalement à l’origine d’une erreur.

 **Efficacité**. Vous pouvez presque toujours substituer une boucle pour la récursivité. Une boucle n’a pas la surcharge liée au passage des arguments, à l’initialisation d’un stockage supplémentaire et au retour de valeurs. Vos performances peuvent être nettement meilleures sans appels récursifs.

 **Récurrence mutuelle**. Vous pouvez observer des performances très médiocres, voire une boucle infinie, si deux procédures s’appellent mutuellement. Une telle conception présente les mêmes problèmes qu’une seule procédure récursive, mais peut être plus difficile à détecter et à déboguer.

 **Appel avec des parenthèses**. Quand une `Function` procédure s’appelle elle-même de manière récursive, vous devez faire suivre le nom de la procédure de parenthèses, même s’il n’y a pas de liste d’arguments. Dans le cas contraire, le nom de la fonction est considéré comme représentant la valeur de retour de la fonction.

 **Test**. Si vous écrivez une procédure récursive, vous devez la tester très attentivement pour vous assurer qu’elle répond toujours à certaines conditions de limitation. Vous devez également vous assurer que vous ne pouvez pas manquer de mémoire en raison d’un trop grand nombre d’appels récursifs.

## <a name="see-also"></a>Voir aussi

- <xref:System.StackOverflowException>
- [Procédures](index.md)
- [Procédures Sub](sub-procedures.md)
- [Procédures Function](function-procedures.md)
- [Procédures de propriété](property-procedures.md)
- [Procédures d’opérateur](operator-procedures.md)
- [Paramètres et arguments d’une procédure](procedure-parameters-and-arguments.md)
- [Surcharge de procédure](procedure-overloading.md)
- [Procédures de dépannage](troubleshooting-procedures.md)
- [Structures de boucle](../control-flow/loop-structures.md)
