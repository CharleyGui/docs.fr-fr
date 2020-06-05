---
title: Concepts de base des chaînes
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 935926b8b83afa47c20ea68aecd6bc8c40bd0234
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363694"
---
# <a name="string-basics-in-visual-basic"></a>Concepts de base des chaînes en Visual Basic
Le type de données `String` représente une série de caractères (chacun représentant à son tour une instance du type de données `Char`). Cette rubrique présente les concepts de base des chaînes dans Visual Basic.  
  
## <a name="string-variables"></a>Variables de chaîne  
 Il est possible d'assigner à une instance de chaîne une valeur littérale représentant une série de caractères. Par exemple :  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 Une variable `String` peut également accepter une expression quelconque qui prend la valeur d'une chaîne. En voici quelques exemples :  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Tout littéral assigné à une variable `String` doit être placé entre guillemets (""). Cela signifie que des guillemets dans une chaîne ne peuvent pas être représentés par des guillemets. Par exemple, le code suivant génère une erreur du compilateur :  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 Ce code entraîne une erreur car le compilateur arrête la chaîne après les deuxièmes guillemets, et le reste de la chaîne est interprété comme du code. Pour résoudre ce problème, Visual Basic interprète deux guillemets dans un littéral de chaîne comme un guillemet dans la chaîne. L'exemple suivant illustre comment inclure correctement des guillemets dans une chaîne :  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 Dans l'exemple précédent, les deux guillemets qui précèdent le mot `Look` deviennent des guillemets simples dans la chaîne. Les trois guillemets à la fin de la ligne correspondent aux guillemets simples dans la chaîne et au caractère de fin de chaîne.  
  
 Les littéraux de chaîne peuvent contenir plusieurs lignes :  
  
```vb  
Dim x = "hello  
world"  
```  
  
 La chaîne obtenue contient les séquences de saut de ligne que vous utilisiez dans votre littéral de chaîne (vbcr, vbcrlf, etc.).  Vous n'avez plus besoin d'utiliser l'ancienne solution de contournement :  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Caractères dans des chaînes  
 Une chaîne peut être considérée comme une série de valeurs `Char` et le type `String` possède des fonctions intégrées qui vous permettent d'exécuter de nombreuses manipulations sur une chaîne qui ressemblent aux manipulations autorisées par les tableaux. Comme tous les tableaux dans .NET Framework, il s’agit de tableaux de base zéro. Vous pouvez vous référer à un caractère spécifique dans une chaîne via la propriété `Chars`, ce qui permet d'accéder à un caractère à la position où il apparaît dans la chaîne. Par exemple :  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 Dans l'exemple ci-dessus, la propriété `Chars` de la chaîne retourne le quatrième caractère de la chaîne, qui est `D`, et l'assigne à `myChar`. Vous pouvez également obtenir la longueur d'une chaîne particulière via la propriété `Length`. Si vous devez exécuter plusieurs manipulations de type tableau sur une chaîne, vous pouvez la convertir en tableau d'instances `Char` à l'aide de la fonction `ToCharArray` de la chaîne. Par exemple :  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 La variable `myArray` contient à présent un tableau de valeurs `Char`, dont chacune représente un caractère issu de `myString`.  
  
## <a name="the-immutability-of-strings"></a>Immuabilité des chaînes  
 Une chaîne est *immuable*, ce qui signifie que sa valeur ne peut pas être modifiée une fois qu’elle a été créée. Toutefois, cela ne vous empêche pas d'assigner plusieurs valeurs à une variable de chaîne. Prenons l’exemple suivant :  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 Ici, une variable de chaîne est créée, une valeur lui est attribuée, puis sa valeur est modifiée.  
  
 Plus spécifiquement, dans la première ligne, une instance de type `String` est créée et la valeur `This string is immutable` lui est attribuée. Dans la seconde ligne de l'exemple, une nouvelle instance est créée et la valeur `Or is it?` lui est attribuée. La variable de chaîne ignore sa référence à la première instance et stocke une référence à la nouvelle instance.  
  
 Contrairement à d'autres types de données intrinsèques, `String` est un type référence. Quand une variable de type référence est passée en tant qu'argument à une fonction ou à une sous-routine, une référence à l'adresse mémoire où sont stockées les données est passée à la place de la valeur réelle de la chaîne. Ainsi, dans l'exemple précédent, le nom de la variable reste le même, mais il pointe vers une instance nouvelle et différente de la classe `String`, qui contient la nouvelle valeur.  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux chaînes en Visual Basic](introduction-to-strings.md)
- [String, type de données](../../../language-reference/data-types/string-data-type.md)
- [Caractères (type de données)](../../../language-reference/data-types/char-data-type.md)
- [Opérations de chaînes de base](../../../../standard/base-types/basic-string-operations.md)
