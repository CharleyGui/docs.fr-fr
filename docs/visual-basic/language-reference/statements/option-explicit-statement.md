---
title: Option Explicit, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
ms.openlocfilehash: 19ff8cf1dbcdb941e38f23be4cb68d3a5e5b83a8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582581"
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit, instruction (Visual Basic)
Force la déclaration explicite de toutes les variables dans un fichier ou autorise les déclarations implicites de variables.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>Composants  
 `On`  
 Optionnel. Active la vérification de `Option Explicit`. Si `On` ou `Off` n’est pas spécifié, la valeur par défaut est `On`.  
  
 `Off`  
 Optionnel. Désactive la vérification de la `Option Explicit`.  
  
## <a name="remarks"></a>Notes  
 Lorsque `Option Explicit On` ou `Option Explicit` apparaît dans un fichier, vous devez déclarer explicitement toutes les variables à l’aide des instructions `Dim` ou `ReDim`. Si vous essayez d’utiliser un nom de variable non déclaré, une erreur se produit au moment de la compilation. L’instruction `Option Explicit Off` autorise la déclaration implicite de variables.  
  
 Si elle est utilisée, l'instruction `Option Explicit` doit apparaître dans un fichier avant toute autre instruction de code source.  
  
> [!NOTE]
> La définition de `Option Explicit` sur `Off` n’est généralement pas une bonne pratique. Vous risquez de mal orthographier un nom de variable dans un ou plusieurs emplacements, ce qui peut provoquer des résultats inattendus lors de l’exécution du programme.  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Lorsqu’une instruction Option Explicit n’est pas présente  
 Si le code source ne contient pas d’instruction `Option Explicit`, le paramètre **Option Explicit** sur la [page compiler, concepteur de projets (Visual Basic),](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé. Si le compilateur de ligne de commande est utilisé, l’option du compilateur [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) est utilisée.  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>Pour définir l’option Explicit dans l’IDE  
  
1. Dans l’**Explorateur de solutions**, sélectionnez un projet. Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
2. Cliquez sur l’onglet **Compiler**.  
  
3. Définissez la valeur dans la zone **Option Explicit** .  
  
 Lorsque vous créez un projet, le paramètre **Option Explicit** de l’onglet **compiler** est défini sur le paramètre **Option Explicit** dans la boîte de dialogue **valeurs par défaut VB** . Pour accéder à la boîte de dialogue **valeurs par défaut VB** , dans le menu **Outils** , cliquez sur **options**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial dans les **valeurs par défaut VB** est `On`.  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>Pour définir l’option Explicit sur la ligne de commande  
  
- Incluez l’option du compilateur [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) dans la commande **vbc** .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `Option Explicit` pour forcer la déclaration explicite de toutes les variables. Toute tentative d’utilisation d’une variable non déclarée génère une erreur au moment de la compilation.  
  
 [!code-vb[VbVbalrStatements#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#47)]  
  
 [!code-vb[VbVbalrStatements#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#48)]  
  
## <a name="see-also"></a>Voir aussi

- [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
