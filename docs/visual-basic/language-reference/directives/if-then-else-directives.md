---
title: '#If...Then...#Else, directives'
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
ms.openlocfilehash: 7054a6ada4583c5d89e020437eb622a59d3eb17a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410008"
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else, directives

Compile conditionnellement les blocs sélectionnés de Visual Basic code.

## <a name="syntax"></a>Syntaxe

```vb
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

## <a name="parts"></a>Éléments

`expression`  
Requis pour `#If` les `#ElseIf` instructions et, facultatif ailleurs. Toute expression, composée exclusivement d’une ou de plusieurs constantes de compilateur conditionnelles, de littéraux et d’opérateurs, qui prend la valeur `True` ou `False` .

`statements`  
Requis pour le `#If` bloc d’instructions, facultatif ailleurs. Visual Basic des lignes de programme ou des directives de compilateur compilées si l’expression associée prend la valeur `True` .

`#End If`  
Termine le `#If` bloc d’instructions.

## <a name="remarks"></a>Notes

Sur la surface, le comportement des `#If...Then...#Else` directives est le même que celui des `If...Then...Else` instructions. Toutefois, les `#If...Then...#Else` directives évaluent ce qui est compilé par le compilateur, tandis que les `If...Then...Else` instructions évaluent les conditions au moment de l’exécution.

La compilation conditionnelle est généralement utilisée pour compiler le même programme pour différentes plateformes. Il est également utilisé pour empêcher le débogage du code d’apparaître dans un fichier exécutable. Le code exclu pendant la compilation conditionnelle est complètement omis du fichier exécutable final. il n’a donc aucun effet sur la taille ou les performances.

Quel que soit le résultat de l’évaluation, toutes les expressions sont évaluées à l’aide de `Option Compare Binary` . L' `Option Compare` instruction n’affecte pas les expressions dans les `#If` `#ElseIf` instructions et.

> [!NOTE]
> Il n’existe pas de formulaire à ligne unique des directives,, `#If` `#Else` `#ElseIf` et `#End If` . Aucun autre code ne peut apparaître sur la même ligne que les directives.

Les instructions contenues dans un bloc de compilation conditionnelle doivent être des instructions logiques complètes. Par exemple, vous ne pouvez pas compiler de façon conditionnelle uniquement les attributs d’une fonction, mais vous pouvez déclarer la fonction de manière conditionnelle avec ses attributs :

```vb
#If DEBUG Then
<WebMethod()>
Public Function SomeFunction() As String
#Else
<WebMethod(CacheDuration:=86400)>
Public Function SomeFunction() As String
#End If
```

## <a name="example"></a>Exemple

Cet exemple utilise la `#If...Then...#Else` construction pour déterminer s’il faut compiler certaines instructions.

[!code-vb[VbVbalrConditionalComp#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#1)]

## <a name="see-also"></a>Voir aussi

- [#Const directive](const-directive.md)
- [If...Then...Else (instruction)](../statements/if-then-else-statement.md)
- [Compilation conditionnelle](../../programming-guide/program-structure/conditional-compilation.md)
- <xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>
