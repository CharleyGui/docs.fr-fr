---
title: statique
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 2b7113424969b0b18c981b0c8932aeef3795ca4a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867675"
---
# <a name="static-visual-basic"></a>Static (Visual Basic)

Spécifie qu’une ou plusieurs variables locales déclarées doivent continuer à exister et conserver leurs valeurs les plus récentes après l’arrêt de la procédure dans laquelle elles sont déclarées.  
  
## <a name="remarks"></a>Notes  

 Normalement, une variable locale dans une procédure cesse d’exister dès que la procédure s’arrête. Une variable statique continue d’exister et conserve sa valeur la plus récente. La prochaine fois que votre code appellera la procédure, la variable n’est pas réinitialisée et contient toujours la valeur la plus récente que vous lui avez assignée. Une variable statique continue d’exister pendant la durée de vie de la classe ou du module dans lequel elle est définie.  
  
## <a name="rules"></a>Règles  
  
- **Contexte de déclaration.** Vous pouvez utiliser `Static` uniquement sur les variables locales. Cela signifie que le contexte de déclaration pour une `Static` variable doit être une procédure ou un bloc dans une procédure, et qu’il ne peut pas s’agir d’un fichier source, d’un espace de noms, d’une classe, d’une structure ou d’un module.  
  
     Vous ne pouvez pas utiliser `Static` à l’intérieur d’une procédure de structure.  
  
- Les types de données des `Static` variables locales ne peuvent pas être déduits. Pour plus d’informations, consultez [inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md).  
  
- **Modificateurs combinés.** Vous ne pouvez pas spécifier `Static` avec `ReadOnly` , `Shadows` ou `Shared` dans la même déclaration.  
  
## <a name="behavior"></a>Comportement  

 Lorsque vous déclarez une variable statique dans une `Shared` procédure, une seule copie de la variable statique est disponible pour l’ensemble de l’application. Vous appelez une `Shared` procédure en utilisant le nom de la classe, et non une variable qui pointe vers une instance de la classe.  
  
 Quand vous déclarez une variable statique dans une procédure qui n’est pas `Shared` , une seule copie de la variable est disponible pour chaque instance de la classe. Vous appelez une procédure non partagée à l’aide d’une variable qui pointe vers une instance spécifique de la classe.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant montre l'utilisation de `Static`.  
  
 [!code-vb[VbVbalrKeywords#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#5)]  
  
 La `Static` variable `totalSales` est initialisée à 0 une seule fois. Chaque fois que vous entrez `updateSales` , `totalSales` la valeur la plus récente que vous avez calculée est toujours la plus récente.  
  
 Le `Static` modificateur peut être utilisé dans ce contexte :  
  
 [Dim (instruction)](../statements/dim-statement.md)  
  
## <a name="see-also"></a>Voir aussi

- [Shadows](shadows.md)
- [Partagé](shared.md)
- [Durée de vie dans Visual Basic](../../programming-guide/language-features/declared-elements/lifetime.md)
- [Déclaration de variable](../../programming-guide/language-features/variables/variable-declaration.md)
- [Structures](../../programming-guide/language-features/data-types/structures.md)
- [Inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md)
- [Objets et classes](../../programming-guide/language-features/objects-and-classes/index.md)
