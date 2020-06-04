---
title: Option Compare, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 1ffe3e45a296d02364f488540d987d85133013bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404380"
---
# <a name="option-compare-statement"></a>Option Compare, instruction
Déclare la méthode de comparaison par défaut à utiliser lors de la comparaison de données de type chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a>Éléments  
  
|Terme|Définition|  
|---|---|  
|`Binary`|Facultatif. Se traduit par des comparaisons de chaînes basées sur un ordre de tri dérivé des représentations binaires internes des caractères.<br /><br /> Ce type de comparaison est utile surtout si les chaînes peuvent contenir des caractères qui ne doivent ne pas être interprétées comme du texte. Dans ce cas, il convient de ne pas fausser les comparaisons avec des équivalences alphabétiques comme, par exemple, quand la casse n'est pas respectée.|  
|`Text`|Facultatif. Se traduit par des comparaisons de chaînes basées sur un ordre de tri de texte sans respect de la casse déterminé par les paramètres régionaux de votre système.<br /><br /> Ce type de comparaison est utile si vos chaînes contiennent toutes des caractères de texte et si vous voulez les comparer en prenant en compte les équivalences alphabétiques, c'est-à-dire des lettres très proches ou de casse différente. Par exemple, vous pouvez faire en sorte que les caractères `A` et `a` soient considérés comme identiques et que les caractères `Ä` et `ä` précèdent `B` et `b`.|  
  
## <a name="remarks"></a>Notes  
 Si elle est utilisée, l'instruction `Option Compare` doit apparaître dans un fichier avant toute autre instruction de code source.  
  
 L'instruction `Option Compare` permet de spécifier la méthode de comparaison de chaînes (`Binary` ou `Text`).  La méthode de comparaison de texte par défaut est `Binary`.  
  
 Une comparaison de type `Binary` permet de comparer la valeur Unicode numérique de chaque caractère dans chaque chaîne. Une comparaison de type `Text` permet de comparer chaque caractère Unicode selon sa signification lexicale dans la culture actuelle.  
  
 Dans Microsoft Windows, l'ordre de tri est déterminé par la page de code. Pour plus d’informations, consultez [Pages de codes](/cpp/c-runtime-library/code-pages).  
  
 Dans l'exemple suivant, les caractères de la page de codes Anglais/Européen (ANSI 1252) sont triés à l'aide de `Option Compare Binary`, qui génère un ordre de tri binaire standard.  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 Quand les mêmes caractères d'une même page de codes sont triés à l'aide de `Option Compare Text`, l'ordre de tri de texte suivant est généré.  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a>En l'absence d'instruction Option Compare  
 Si le code source ne contient pas d' `Option Compare` instruction, le paramètre **option compare** sur la [page compiler, concepteur de projets (Visual Basic),](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé. Si vous utilisez le compilateur de ligne de commande, le paramètre spécifié par l’option [de compilateur-optioncompare](../../reference/command-line-compiler/optioncompare.md) est utilisé.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a>Pour définir Option Compare dans l'IDE  
  
1. Dans **Explorateur de solutions**, sélectionnez un projet. Dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l’onglet **Compiler**.  
  
3. Définissez la valeur dans la zone **option compare** .  
  
 Lorsque vous créez un projet, le paramètre **option compare** de l’onglet **compiler** est défini sur le paramètre **option compare** dans la boîte de dialogue **options** . Pour modifier ce paramètre, dans le menu **Outils** , cliquez sur **options**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial dans les **valeurs par défaut VB** est **binaire**.  
  
#### <a name="to-set-option-compare-on-the-command-line"></a>Pour définir Option Compare sur la ligne de commande  
  
- Incluez l’option de compilateur [-optioncompare](../../reference/command-line-compiler/optioncompare.md) dans la commande **vbc** .  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise l'instruction `Option Compare` pour définir la comparaison binaire comme méthode de comparaison de chaînes par défaut. Pour utiliser ce code, supprimez les commentaires de l'instruction `Option Compare Binary` et placez-la en haut du fichier source.  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise l'instruction `Option Compare` pour définir l'ordre de tri de texte sans respect de la casse comme méthode de comparaison de chaînes par défaut. Pour utiliser ce code, supprimez les commentaires de l'instruction `Option Compare Text` et placez-la en haut du fichier source.  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [-optioncompare](../../reference/command-line-compiler/optioncompare.md)
- [Opérateurs de comparaison](../operators/comparison-operators.md)
- [Comparison Operators in Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Like, opérateur](../operators/like-operator.md)
- [Fonctions de chaîne](../functions/string-functions.md)
- [Option Explicit (instruction)](option-explicit-statement.md)
- [Option Strict Statement](option-strict-statement.md)
