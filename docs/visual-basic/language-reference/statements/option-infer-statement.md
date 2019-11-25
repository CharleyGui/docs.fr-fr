---
title: Instruction Option Infer
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
ms.openlocfilehash: 53bc9d41f28f63061db2012395480aa6be7515dd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346494"
---
# <a name="option-infer-statement"></a>Instruction Option Infer

Permet l'utilisation de l'inférence de type de variable locale dans les variables déclaratives.

## <a name="syntax"></a>Syntaxe

```vb
Option Infer { On | Off }
```

## <a name="parts"></a>Composants

|Terme|Définition|
|---|---|
|`On`|Optionnel. Active l'inférence de type de variable locale.|
|`Off`|Optionnel. Désactive l'inférence de type de variable locale.|

## <a name="remarks"></a>Notes

Pour définir `Option Infer` dans un fichier, tapez `Option Infer On` ou `Option Infer Off` en haut du fichier, avant tout autre code source. Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.

Quand vous affectez à `Option Infer` la valeur `On`, vous pouvez déclarer des variables locales sans déclarer explicitement un type de données. Le compilateur déduit le type de données d'une variable à partir du type de son expression d'initialisation.

Dans l'illustration suivante, `Option Infer` est activé. La variable contenue dans la déclaration `Dim someVar = 2` est déclarée en tant qu'entier par l'inférence de type.

The following screenshot shows IntelliSense when Option Infer is on:

![Screenshot showing IntelliSense view when Option Infer is on.](./media/option-infer-statement/option-infer-as-integer-on.png)

Dans l'illustration suivante, `Option Infer` est désactivé. La variable contenue dans la déclaration `Dim someVar = 2` est déclarée comme `Object` par l'inférence de type. In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

The following screenshot shows IntelliSense when Option Infer is off:

![Screenshot showing IntelliSense view when Option Infer is off.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> Quand une variable est déclarée comme `Object`, le type au moment de l'exécution peut changer pendant que le programme s'exécute. Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower. For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).

L'inférence de type s'applique au niveau de la procédure, mais pas à l'extérieur d'une procédure de classe, de structure, de module ou d'interface.

For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

## <a name="when-an-option-infer-statement-is-not-present"></a>En l'absence d'instruction Option Infer

If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used. If the command-line compiler is used, the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.

#### <a name="to-set-option-infer-in-the-ide"></a>Pour définir Option Infer dans l'IDE

1. Dans l’**Explorateur de solutions**, sélectionnez un projet. Dans le menu **Projet**, cliquez sur **Propriétés**.

2. Cliquez sur l’onglet **Compiler**.

3. Set the value in the **Option infer** box.

When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box. To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. The initial default setting in **VB Defaults** is `On`.

#### <a name="to-set-option-infer-on-the-command-line"></a>Pour définir Option Infer sur la ligne de commande

Include the [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.

## <a name="default-data-types-and-values"></a>Types de données et valeurs par défaut

Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.

|Type de données spécifié ?|Initialiseur spécifié ?|Exemple|Résultat|
|---|---|---|---|
|Non|Non|`Dim qty`|Si `Option Strict` est désactivé (par défaut), la valeur affectée à la variable est `Nothing`.<br /><br /> Si `Option Strict` est activé, une erreur se produit au moment de la compilation.|
|Non|Oui|`Dim qty = 5`|Si `Option Infer` est activée (par défaut), la variable prend le type de données de l'initialiseur. See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.|
|Oui|Non|`Dim qty As Integer`|La variable est initialisée avec la valeur par défaut du type de données. For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).|
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
- [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Conversion boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
