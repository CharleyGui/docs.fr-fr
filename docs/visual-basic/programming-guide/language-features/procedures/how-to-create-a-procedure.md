---
title: 'Procédure : Créer une procédure (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 2cf4c788ec421c1e74ef7198496a92149e049752
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216723"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Procédure : Créer une procédure (Visual Basic)

Vous devez placer une procédure entre une instruction de début`Sub` de `Function`déclaration (ou) et une instruction`End Sub` de `End Function`déclaration de fin (ou). Tout le code de la procédure se trouve entre ces instructions.

 Une procédure ne peut pas contenir une autre procédure, donc ses instructions de début et de fin doivent être en dehors de toute autre procédure.

 Si vous avez du code qui effectue la même tâche dans différents emplacements, vous pouvez écrire la tâche une seule fois en tant que procédure, puis l’appeler à partir de différents emplacements dans votre code.

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Pour créer une procédure qui ne retourne pas de valeur

1. En dehors de toute autre procédure, `Sub` utilisez une instruction, suivie `End Sub` d’une instruction.

2. Dans l' `Sub` instruction, `Sub` suivez le mot clé avec le nom de la procédure, puis la liste de paramètres entre parenthèses.

3. Placez les instructions de code de la procédure `Sub` entre `End Sub` les instructions et.

### <a name="to-create-a-procedure-that-returns-a-value"></a>Pour créer une procédure qui retourne une valeur

1. En dehors de toute autre procédure, `Function` utilisez une instruction, suivie `End Function` d’une instruction.

2. Dans l' `Function` instruction, `Function` suivez le mot clé avec le nom de la procédure, puis la liste de paramètres entre parenthèses, et `As` enfin une clause qui spécifie le type de données de la valeur de retour.

3. Placez les instructions de code de la procédure `Function` entre `End Function` les instructions et.

4. Utilisez une `Return` instruction pour retourner la valeur au code appelant.

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Pour connecter votre nouvelle procédure avec les anciens blocs de code répétitifs

1. Veillez à définir la nouvelle procédure à un endroit où l’ancien code y a accès.

2. Dans votre ancien bloc de code répétitif, remplacez les instructions qui exécutent la tâche répétitive par une instruction unique qui appelle `Sub` la `Function` procédure ou.

3. Si votre procédure est un `Function` qui retourne une valeur, assurez-vous que votre instruction appelante effectue une action avec la valeur retournée, telle que le stockage dans une variable, sinon la valeur sera perdue.

## <a name="example"></a>Exemple

 La procédure `Function` suivante calcule le côté le plus long, ou hypoténuse, d’un triangle rectangle, en fonction des valeurs des deux autres côtés :

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a>Voir aussi

- [Procédures](index.md)
- [Procédures Sub](sub-procedures.md)
- [Procédures Function](function-procedures.md)
- [Procédures de propriété](property-procedures.md)
- [Procédures d’opérateur](operator-procedures.md)
- [Paramètres et arguments d’une procédure](procedure-parameters-and-arguments.md)
- [Procédures récursives](recursive-procedures.md)
- [Surcharge de procédure](procedure-overloading.md)
- [Objets et classes](../objects-and-classes/index.md)
- [Programmation orientée objet (Visual Basic)](../../concepts/object-oriented-programming.md)
