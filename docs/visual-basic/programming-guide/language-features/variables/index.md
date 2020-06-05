---
title: Variables
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: ff617774d7e93ab4238ebc06617cc03fb6bc675a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410385"
---
# <a name="variables-in-visual-basic"></a>Variables en Visual Basic
Vous devez souvent stocker des valeurs lorsque vous effectuez des calculs avec Visual Basic. Par exemple, vous pouvez être amené à calculer plusieurs valeurs, à les comparer et à effectuer différentes opérations sur ces valeurs, en fonction du résultat de la comparaison. Vous devez conserver les valeurs si vous souhaitez les comparer.  
  
## <a name="usage"></a>Usage  
 Visual Basic, tout comme la plupart des langages de programmation, utilise des variables pour stocker les valeurs. Une *variable* a un nom (le mot que vous utilisez pour faire référence à la valeur que la variable contient). Une variable a également un type de données (lequel détermine le genre des données que la variable peut stocker). Une variable peut représenter un tableau si elle doit stocker un ensemble indexé d’éléments de données étroitement liés.  
  
 L’inférence de type de variable locale vous permet de déclarer des variables sans déclarer explicitement un type de données. À la place, le compilateur déduit le type de la variable à partir du type de l’expression d’initialisation. Pour plus d’informations, consultez [Inférence de type de variable locale](local-type-inference.md) et [Option Infer, instruction](../../../language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Assignation de valeurs  
 Vous utilisez des instructions d’assignation pour effectuer des calculs et assigner le résultat à une variable, comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> Dans cet exemple, le signe égal (`=`) représente un opérateur d’assignation, et non un opérateur d’égalité. La valeur est assignée à la variable `applesSold`.  
  
 Pour plus d’informations, consultez [Guide pratique pour placer des données dans et en dehors d’une variable](how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Variables et propriétés  
 À l’instar d’une variable, une *propriété* représente une valeur à laquelle vous pouvez accéder. Toutefois, elle est plus complexe qu’une variable. Une propriété utilise des blocs de code qui contrôlent la définition et la récupération de sa valeur. Pour plus d’informations, consultez [Différences entre les propriétés et les variables en Visual Basic](../procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Voir aussi

- [Déclaration de variable](variable-declaration.md)
- [Variables objets](object-variables.md)
- [Dépannage des variables](troubleshooting-variables.md)
- [Comment : placer des données dans et en dehors d'une variable](how-to-move-data-into-and-out-of-a-variable.md)
- [Différences entre les propriétés et les variables en Visual Basic](../procedures/differences-between-properties-and-variables.md)
- [Inférence de type local](local-type-inference.md)
