---
title: Option Infer, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: a85d8012eea14abe4ddcdb35fa154245894a7f97
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64582940"
---
# <a name="option-infer-statement"></a>Instruction Option Infer
Permet l'utilisation de l'inférence de type de variable locale dans les variables déclaratives.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`On`|Facultatif. Active l'inférence de type de variable locale.|  
|`Off`|Facultatif. Désactive l'inférence de type de variable locale.|  
  
## <a name="remarks"></a>Notes  
 Pour définir `Option Infer` dans un fichier, tapez `Option Infer On` ou `Option Infer Off` en haut du fichier, avant tout autre code source. Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.  
  
 Quand vous affectez à `Option Infer` la valeur `On`, vous pouvez déclarer des variables locales sans déclarer explicitement un type de données. Le compilateur déduit le type de données d'une variable à partir du type de son expression d'initialisation.  
  
 Dans l'illustration suivante, `Option Infer` est activé. La variable contenue dans la déclaration `Dim someVar = 2` est déclarée en tant qu'entier par l'inférence de type.

 La capture d’écran suivante montre IntelliSense quand Option Infer est activé : 
  
 ![Capture d’écran montrant la vue IntelliSense quand Option Infer est activé.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 Dans l'illustration suivante, `Option Infer` est désactivé. La variable contenue dans la déclaration `Dim someVar = 2` est déclarée comme `Object` par l'inférence de type. Dans cet exemple, le **Option Strict** est défini sur **hors** sur le [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
 La capture d’écran suivante montre IntelliSense quand Option Infer est désactivé :
 
 ![Capture d’écran montrant la vue IntelliSense quand Option Infer est désactivé.](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
>  Quand une variable est déclarée comme `Object`, le type au moment de l'exécution peut changer pendant que le programme s'exécute. Visual Basic exécute des opérations appelées *boxing* et *unboxing* effectuer une conversion entre un `Object` et un type valeur, ce qui ralentit l’exécution. Pour plus d’informations sur les conversions boxing et unboxing, consultez le [spécification du langage Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).
  
 L'inférence de type s'applique au niveau de la procédure, mais pas à l'extérieur d'une procédure de classe, de structure, de module ou d'interface.  
  
 Pour plus d’informations, consultez [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="when-an-option-infer-statement-is-not-present"></a>En l'absence d'instruction Option Infer  
 Si le code source ne contient-elle pas une `Option Infer` instruction, le **Option Infer** définition sur le [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé. Si le compilateur de ligne de commande est utilisé, le [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) option du compilateur est utilisée.  
  
#### <a name="to-set-option-infer-in-the-ide"></a>Pour définir Option Infer dans l'IDE  
  
1. Dans l’**Explorateur de solutions**, sélectionnez un projet. Dans le menu **Projet**, cliquez sur **Propriétés**.  
  
2. Cliquez sur l’onglet **Compiler**.  
  
3. Définissez la valeur dans le **Option infer** boîte.  
  
 Lorsque vous créez un nouveau projet, le **Option Infer** définition sur le **compiler** onglet est définie sur le **Option Infer** définition dans le **valeurs par défaut VB** boîte de dialogue. Pour accéder à la **valeurs par défaut VB** boîte de dialogue le **outils** menu, cliquez sur **Options**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial dans **valeurs par défaut VB** est `On`.  
  
#### <a name="to-set-option-infer-on-the-command-line"></a>Pour définir Option Infer sur la ligne de commande  
  
- Inclure le [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) option du compilateur dans le **vbc** commande.  
  
## <a name="default-data-types-and-values"></a>Types de données et valeurs par défaut  
 Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.  
  
|Type de données spécifié ?|Initialiseur spécifié ?|Exemple|Résultat|  
|---|---|---|---|  
|Non|Non|`Dim qty`|Si `Option Strict` est désactivé (par défaut), la valeur affectée à la variable est `Nothing`.<br /><br /> Si `Option Strict` est activé, une erreur se produit au moment de la compilation.|  
|Non|Oui|`Dim qty = 5`|Si `Option Infer` est activée (par défaut), la variable prend le type de données de l'initialiseur. Consultez [inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.|  
|Oui|Non|`Dim qty As Integer`|La variable est initialisée avec la valeur par défaut du type de données. Pour plus d’informations, consultez [instruction Dim](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Oui|Oui|`Dim qty  As Integer = 5`|Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.|  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent comment l'instruction `Option Infer` active l'inférence de type de variable locale.  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre que le type au moment de l'exécution peut être différent quand une variable est identifiée comme `Object`.  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Voir aussi

- [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare (instruction)](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Option Explicit (instruction)](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Option Strict (instruction)](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Conversion boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
