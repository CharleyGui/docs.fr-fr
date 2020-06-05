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
ms.openlocfilehash: 977e492c1c8ec5040c22169d91268c9c2241f6c4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404354"
---
# <a name="option-infer-statement"></a>Instruction Option Infer

Permet l'utilisation de l'inférence de type de variable locale dans les variables déclaratives.

## <a name="syntax"></a>Syntaxe

```vb
Option Infer { On | Off }
```

## <a name="parts"></a>Éléments

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

Dans l'illustration suivante, `Option Infer` est désactivé. La variable contenue dans la déclaration `Dim someVar = 2` est déclarée comme `Object` par l'inférence de type. Dans cet exemple, le paramètre **option strict** a la valeur **off** dans la [page compiler, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).

La capture d’écran suivante montre IntelliSense quand Option Infer est désactivé :

![Capture d’écran montrant la vue IntelliSense quand Option Infer est désactivée.](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> Quand une variable est déclarée comme `Object`, le type au moment de l'exécution peut changer pendant que le programme s'exécute. Visual Basic effectue des opérations appelées *boxing* et *unboxing* pour effectuer une conversion entre un `Object` et un type valeur, ce qui ralentit l’exécution. Pour plus d’informations sur le boxing et l’unboxing, consultez la [spécification du langage Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).

L'inférence de type s'applique au niveau de la procédure, mais pas à l'extérieur d'une procédure de classe, de structure, de module ou d'interface.

Pour plus d’informations, consultez [inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md).

## <a name="when-an-option-infer-statement-is-not-present"></a>En l'absence d'instruction Option Infer

Si le code source ne contient pas d' `Option Infer` instruction, le paramètre **Option Infer** sur la [page compiler, concepteur de projets (Visual Basic),](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) est utilisé. Si le compilateur de ligne de commande est utilisé, l’option [de compilateur-optioninfer (](../../reference/command-line-compiler/optioninfer.md) est utilisée.

#### <a name="to-set-option-infer-in-the-ide"></a>Pour définir Option Infer dans l'IDE

1. Dans **Explorateur de solutions**, sélectionnez un projet. Dans le menu **Projet** , cliquez sur **Propriétés**.

2. Cliquez sur l’onglet **Compiler**.

3. Définissez la valeur dans la zone **Option Infer** .

Lorsque vous créez un projet, le paramètre **Option Infer** de l’onglet **compiler** est défini sur le paramètre **Option Infer** dans la boîte de dialogue **valeurs par défaut VB** . Pour accéder à la boîte de dialogue **valeurs par défaut VB** , dans le menu **Outils** , cliquez sur **options**. Dans la boîte de dialogue **Options**, développez **Projets et solutions**, puis cliquez sur **Valeurs par défaut VB**. Le paramètre par défaut initial dans les **valeurs par défaut VB** est `On` .

#### <a name="to-set-option-infer-on-the-command-line"></a>Pour définir Option Infer sur la ligne de commande

Incluez l’option de compilateur [-optioninfer (](../../reference/command-line-compiler/optioninfer.md) dans la commande **vbc** .

## <a name="default-data-types-and-values"></a>Types de données et valeurs par défaut

Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.

|Type de données spécifié ?|Initialiseur spécifié ?| Exemple|Résultats|
|---|---|---|---|
|Non|Non|`Dim qty`|Si `Option Strict` est désactivé (par défaut), la valeur affectée à la variable est `Nothing`.<br /><br /> Si `Option Strict` est activé, une erreur se produit au moment de la compilation.|
|Non|Oui|`Dim qty = 5`|Si `Option Infer` est activée (par défaut), la variable prend le type de données de l'initialiseur. Consultez [inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.<br /><br /> Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.|
|Oui|Non|`Dim qty As Integer`|La variable est initialisée avec la valeur par défaut du type de données. Pour plus d’informations, consultez [Dim, instruction](dim-statement.md).|
|Oui|Oui|`Dim qty  As Integer = 5`|Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.|

## <a name="example"></a>Exemple

Les exemples suivants montrent comment l'instruction `Option Infer` active l'inférence de type de variable locale.

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a>Exemple

L'exemple suivant montre que le type au moment de l'exécution peut être différent quand une variable est identifiée comme `Object`.

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a>Voir aussi

- [Dim (instruction)](dim-statement.md)
- [Inférence de type local](../../programming-guide/language-features/variables/local-type-inference.md)
- [Option Compare, instruction](option-compare-statement.md)
- [Option Explicit (instruction)](option-explicit-statement.md)
- [Option Strict Statement](option-strict-statement.md)
- [Valeurs par défaut VB, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [-optioninfer](../../reference/command-line-compiler/optioninfer.md)
- [Boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
