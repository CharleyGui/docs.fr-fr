---
title: '#If... Then... #Else directives (Visual Basic)'
ms.date: 04/11/2018
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
ms.openlocfilehash: 697521276e2d5a8d0a4aaae38789a21b7aa87fcb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940758"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else, directives
Compile conditionnellement les blocs sélectionnés de Visual Basic code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a>Composants  
 `expression`  
 Requis pour `#If` les `#ElseIf` instructions et, facultatif ailleurs. Toute expression, composée exclusivement d’une ou de plusieurs constantes de compilateur conditionnelles, de littéraux et d' `True` opérateurs, qui prend la valeur ou. `False`  
  
 `statements`  
 Requis pour `#If` le bloc d’instructions, facultatif ailleurs. Visual Basic des lignes de programme ou des directives de compilateur compilées si l’expression associée `True`prend la valeur.  
  
 `#End If`  
 Termine le `#If` bloc d’instructions.  
  
## <a name="remarks"></a>Notes  
 Sur la surface, le comportement des `#If...Then...#Else` directives est le même que celui `If...Then...Else` des instructions. Toutefois, les `#If...Then...#Else` directives évaluent ce qui est compilé par le compilateur, `If...Then...Else` tandis que les instructions évaluent les conditions au moment de l’exécution.  
  
 La compilation conditionnelle est généralement utilisée pour compiler le même programme pour différentes plateformes. Il est également utilisé pour empêcher le débogage du code d’apparaître dans un fichier exécutable. Le code exclu pendant la compilation conditionnelle est complètement omis du fichier exécutable final. il n’a donc aucun effet sur la taille ou les performances.  
  
 Quel que soit le résultat de l’évaluation, toutes les expressions sont `Option Compare Binary`évaluées à l’aide de. L' `Option Compare` instruction n’affecte pas les expressions `#If` dans `#ElseIf` les instructions et.  
  
> [!NOTE]
> Il n’existe pas de formulaire à `#If`ligne `#Else`unique `#ElseIf`des directives `#End If` ,, et. Aucun autre code ne peut apparaître sur la même ligne que les directives. 

Les instructions contenues dans un bloc de compilation conditionnelle doivent être des instructions logiques complètes. Par exemple, vous ne pouvez pas compiler de façon conditionnelle uniquement les attributs d’une fonction, mais vous pouvez déclarer la fonction de manière conditionnelle avec ses attributs:

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a>Exemples
 Cet exemple utilise la `#If...Then...#Else` construction pour déterminer s’il faut compiler certaines instructions.  
  
 [!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [#Const (directive)](../../../visual-basic/language-reference/directives/const-directive.md)
- [If...Then...Else (instruction)](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
