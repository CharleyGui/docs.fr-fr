---
title: Arguments nommés et facultatifs - Guide de programmation C#
description: Les arguments nommés en C# spécifient des arguments par nom, et non par position. Les arguments facultatifs peuvent être omis.
ms.date: 09/25/2020
ms.custom: contperf-fy21q1
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
ms.openlocfilehash: bb79d956124a610bac0de6825c1f42655789e98d
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513105"
---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Arguments nommés et facultatifs (Guide de programmation C#)

C# 4 introduit des arguments nommés et facultatifs. Les *arguments nommés* vous permettent de spécifier un argument pour un paramètre en faisant correspondre l’argument avec son nom plutôt qu’avec sa position dans la liste de paramètres. Les *arguments facultatifs* vous permettent d’omettre des arguments pour certains paramètres. Les deux techniques peuvent être utilisées avec les méthodes, les indexeurs, les constructeurs et les délégués.

Quand vous utilisez des arguments nommés et facultatifs, ils sont évalués selon leur ordre d’affichage dans la liste d’arguments, et non dans la liste de paramètres.

Les paramètres nommés et facultatifs vous permettent de fournir des arguments pour les paramètres sélectionnés. Cette fonctionnalité simplifie les appels aux interfaces COM, telles que les API Microsoft Office Automation.

## <a name="named-arguments"></a>Arguments nommés

Les arguments nommés vous libèrent de l’ordre des paramètres dans les listes de paramètres des méthodes appelées. Vous pouvez spécifier le paramètre de chaque argument par son nom. Par exemple, une fonction qui imprime les détails d’une commande (par exemple, le nom du vendeur, le numéro de commande & nom du produit) peut être appelée en envoyant des arguments par position, dans l’ordre défini par la fonction.

```csharp
PrintOrderDetails("Gift Shop", 31, "Red Mug");
```

Si vous ne vous souvenez pas de l’ordre des paramètres, mais que vous connaissez leur nom, vous pouvez envoyer les arguments dans n’importe quel ordre.

```csharp
PrintOrderDetails(orderNum: 31, productName: "Red Mug", sellerName: "Gift Shop");
PrintOrderDetails(productName: "Red Mug", sellerName: "Gift Shop", orderNum: 31);
```

Les arguments nommés améliorent également la lisibilité de votre code en identifiant ce que chaque argument représente. Dans l’exemple de méthode ci-dessous, l' `sellerName` ne peut pas être null ou un espace blanc. `sellerName` et `productName` étant tous deux des types de chaînes, au lieu d’envoyer les arguments par position, il est plus logique d’utiliser des arguments nommés pour lever l’ambiguïté entre les deux et réduire les risques de confusion pour toute personne lisant le code.
  
Les arguments nommés, quand ils sont utilisés avec des arguments de position, sont valides tant que :

- Ils ne sont pas suivis d’arguments de position, ou

    ```csharp
    PrintOrderDetails("Gift Shop", 31, productName: "Red Mug");
    ```

- _À compter de C# 7.2_, ils sont utilisés dans la position correcte Dans l’exemple ci-dessous, le paramètre `orderNum` est à la position correcte, mais il n’est pas explicitement nommé.

    ```csharp
    PrintOrderDetails(sellerName: "Gift Shop", 31, productName: "Red Mug");
    ```

Les arguments positionnels qui suivent les arguments nommés non ordonnés ne sont pas valides.

```csharp
// This generates CS1738: Named argument specifications must appear after all fixed arguments have been specified.
PrintOrderDetails(productName: "Red Mug", 31, "Gift Shop");
```

## <a name="example"></a>Exemple

Le code suivant implémente les exemples de cette section, ainsi que d’autres exemples.  

[!code-csharp[csProgGuideNamedAndOptional#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/program.cs#1)]

## <a name="optional-arguments"></a>Arguments facultatifs

La définition d’une méthode, d’un constructeur, d’un indexeur ou d’un délégué peut spécifier que ses paramètres sont obligatoires ou facultatifs. Chaque appel doit fournir des arguments pour tous les paramètres obligatoires, mais peut omettre les arguments des paramètres facultatifs.

Dans sa définition, chaque paramètre facultatif a une valeur par défaut. Si aucun argument n’est envoyé pour ce paramètre, la valeur par défaut est utilisée. Une valeur par défaut doit être l’un des types d’expressions suivants :
  
- une expression constante ;  
- une expression de la forme `new ValType()`, où `ValType` est un type valeur (par exemple, [enum](../../language-reference/builtin-types/enum.md) ou [struct](../../language-reference/builtin-types/struct.md)) ;
- une expression de la forme [default(ValType)](../../language-reference/operators/default.md), où `ValType` est un type valeur.

Les paramètres facultatifs sont définis à la fin de la liste de paramètres, après tous les paramètres obligatoires. Si l’appelant fournit un argument pour l’un des paramètres d’une série de paramètres facultatifs, il doit fournir des arguments pour tous les paramètres facultatifs précédents. Les écarts séparés par des virgules dans la liste d’arguments ne sont pas pris en charge. Par exemple, dans le code suivant, la méthode d’instance `ExampleMethod` est définie avec un paramètre obligatoire et deux paramètres facultatifs.

[!code-csharp[csProgGuideNamedAndOptional#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#15)]

L’appel suivant à `ExampleMethod` provoque une erreur du compilateur, car un argument est fourni pour le troisième paramètre, mais pas pour le deuxième.

```csharp
//anExample.ExampleMethod(3, ,4);
```

Toutefois, si vous connaissez le nom du troisième paramètre, vous pouvez utiliser un argument nommé pour effectuer la tâche.

```csharp
anExample.ExampleMethod(3, optionalint: 4);
```

IntelliSense indique les paramètres facultatifs par des crochets, comme illustré dans l’exemple suivant :

![Capture d’écran montrant l’info express IntelliSense pour la méthode ExampleMethod.](./media/named-and-optional-arguments/optional-examplemethod-parameters.png)

> [!NOTE]
> Vous pouvez aussi déclarer des paramètres facultatifs à l’aide de la classe <xref:System.Runtime.InteropServices.OptionalAttribute> .NET. Les paramètres `OptionalAttribute` ne nécessitent pas de valeur par défaut.

## <a name="example"></a>Exemple

Dans l’exemple suivant, le constructeur associé à `ExampleClass` a un seul paramètre, qui est facultatif. La méthode d’instance `ExampleMethod` a un paramètre obligatoire (`required`) et deux paramètres facultatifs (`optionalstr` et `optionalint`). Le code dans `Main` montre les différentes façons dont le constructeur et la méthode peuvent être appelés.

[!code-csharp[csProgGuideNamedAndOptional#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/optional.cs#2)]

Le code précédent illustre un certain nombre d’exemples où les paramètres facultatifs ne sont pas appliqués correctement. Le premier illustre qu’un argument doit être fourni pour le premier paramètre, ce qui est obligatoire.
  
## <a name="com-interfaces"></a>Interfaces COM

Les arguments nommés et facultatifs, ainsi que la prise en charge des objets dynamiques, améliorent beaucoup l’interopérabilité avec les API COM, telles que les API d’automatisation d’Office.

Par exemple, la méthode <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> de l’interface <xref:Microsoft.Office.Interop.Excel.Range> de Microsoft Office Excel comporte sept paramètres, tous facultatifs. Ces paramètres sont indiqués dans l’illustration suivante :

![Capture d’écran montrant l’info express IntelliSense pour la méthode AutoFormat.](./media/named-and-optional-arguments/autoformat-method-parameters.png)

Dans C# 3.0 et les versions antérieures, un argument est obligatoire pour chaque paramètre, comme indiqué dans l’exemple suivant.

[!code-csharp[csProgGuideNamedAndOptional#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#3)]

Toutefois, vous pouvez considérablement simplifier l’appel à `AutoFormat` en utilisant les arguments nommés et facultatifs introduits dans C# 4.0. Les arguments nommés et facultatifs vous permettent d’omettre l’argument d’un paramètre facultatif si vous ne souhaitez pas modifier la valeur par défaut du paramètre. Dans l’appel suivant, une valeur est spécifiée pour un seul des sept paramètres.

[!code-csharp[csProgGuideNamedAndOptional#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/namedandoptcom.cs#13)]

Pour plus d’informations et d’exemples, consultez [comment utiliser des arguments nommés et facultatifs dans la programmation Office](./how-to-use-named-and-optional-arguments-in-office-programming.md) et [Comment accéder aux objets Office Interop à l’aide des fonctionnalités C#](../interop/how-to-access-office-onterop-objects.md).
  
## <a name="overload-resolution"></a>Résolution de surcharge

L’utilisation d’arguments nommés et facultatifs affecte la résolution de surcharge des manières suivantes :

- Une méthode, un indexeur ou un constructeur est un candidat pour l’exécution si chacun de ses paramètres est facultatif ou correspond, par nom ou par position, à un seul argument dans l’instruction appelante, et que cet argument peut être converti vers le type du paramètre.  
- Si plusieurs candidats sont trouvés, les règles de résolution de surcharge des conversions préférées sont appliquées aux arguments qui sont explicitement spécifiés. Les arguments omis pour les paramètres facultatifs sont ignorés.
- Si deux candidats sont jugés corrects, la préférence passe à un candidat qui n’a pas de paramètres facultatifs pour lesquels des arguments ont été omis dans l’appel. La résolution de surcharge préfère généralement les candidats qui ont moins de paramètres.
  
## <a name="c-language-specification"></a>Spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
