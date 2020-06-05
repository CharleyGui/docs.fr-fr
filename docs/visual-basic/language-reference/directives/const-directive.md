---
title: '#Const, directive'
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
ms.openlocfilehash: 91152771a4ef5ec74a7408511ccc2afe28dd442e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415464"
---
# <a name="const-directive"></a>#Const, directive

Définit les constantes conditionnelles du compilateur pour Visual Basic.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
#Const constname = expression  
```  
  
## <a name="parts"></a>Éléments  

 `constname`  
 Obligatoire. Nom de la constante définie.  
  
 `expression`  
 Obligatoire. Littéral, autre constante de compilation conditionnelle ou toute combinaison qui comprend tout ou partie des opérateurs arithmétiques ou logiques, à l’exception de `Is` .  
  
## <a name="remarks"></a>Notes  

 Les constantes de compilateur conditionnel sont toujours privées pour le fichier dans lequel elles apparaissent. Vous ne pouvez pas créer de constantes de compilateur publiques à l’aide de la `#Const` directive ; vous pouvez les créer uniquement dans l’interface utilisateur ou avec l' `/define` option de compilateur.  
  
 Vous pouvez utiliser uniquement des constantes et des littéraux de compilateur conditionnels dans `expression` . L’utilisation d’une constante standard définie avec `Const` génère une erreur. À l’inverse, vous pouvez utiliser des constantes définies avec le `#Const` mot clé uniquement pour la compilation conditionnelle. Les constantes peuvent également être non définies. dans ce cas, elles ont la valeur `Nothing` .  
  
## <a name="example"></a>Exemple  

 Cet exemple utilise la directive `#Const`.  
  
 [!code-vb[VbVbalrConditionalComp#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [-définir (Visual Basic)](../../reference/command-line-compiler/define.md)
- [#If... Then... #Else directives](if-then-else-directives.md)
- [Const (instruction)](../statements/const-statement.md)
- [Compilation conditionnelle](../../programming-guide/program-structure/conditional-compilation.md)
- [If...Then...Else (instruction)](../statements/if-then-else-statement.md)
