---
title: '#Directive const (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
ms.openlocfilehash: 031f35df24fd52aeeafcb7b4c0208806d7fc5fc4
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774756"
---
# <a name="const-directive"></a>#Const, directive
Définit les constantes conditionnelles du compilateur pour Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>Composants  
 `constname`  
 Requis. Nom de la constante définie.  
  
 `expression`  
 Requis. Littéral, autre constante de compilation conditionnelle ou toute combinaison qui comprend tout ou partie des opérateurs arithmétiques ou logiques, à l’exception de `Is`.  
  
## <a name="remarks"></a>Notes  
 Les constantes de compilateur conditionnel sont toujours privées pour le fichier dans lequel elles apparaissent. Vous ne pouvez pas créer de constantes de compilateur publiques à l’aide de la directive `#Const` ; vous pouvez les créer uniquement dans l’interface utilisateur ou avec l’option de compilateur `/define`.  
  
 Vous pouvez uniquement utiliser des constantes et des littéraux de compilateur conditionnels dans `expression`. L’utilisation d’une constante standard définie avec `Const` génère une erreur. À l’inverse, vous pouvez utiliser des constantes définies avec le mot clé `#Const` uniquement pour la compilation conditionnelle. Les constantes peuvent également être non définies, auquel cas leur valeur est `Nothing`.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise la directive `#Const`.  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [-définir (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)
- [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md)
- [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
