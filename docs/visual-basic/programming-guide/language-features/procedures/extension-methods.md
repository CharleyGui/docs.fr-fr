---
title: Méthodes d'extension (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: b5ad066fe9ec40d715702ed99537f45b21c558cf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701055"
---
# <a name="extension-methods-visual-basic"></a>Méthodes d'extension (Visual Basic)

Les méthodes d’extension permettent aux développeurs d’ajouter des fonctionnalités personnalisées aux types de données qui sont déjà définis sans créer de type dérivé. Les méthodes d’extension permettent d’écrire une méthode qui peut être appelée comme s’il s’agissait d’une méthode d’instance du type existant.
  
## <a name="remarks"></a>Notes

Une méthode d’extension peut être uniquement une procédure `Sub` ou une procédure `Function`. Vous ne pouvez pas définir une propriété, un champ ou un événement d’extension. Toutes les méthodes d’extension doivent être marquées avec l’attribut d’extension `<Extension>` à partir de l’espace de noms <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> et doivent être définies dans un [module](../../../language-reference/statements/module-statement.md). Si une méthode d’extension est définie à l’extérieur d’un module, le compilateur Visual Basic génère l’erreur [BC36551](../../../misc/bc36551.md), « les méthodes d’extension ne peuvent être définies que dans des modules ».

Le premier paramètre d’une définition de méthode d’extension spécifie le type de données que la méthode étend. Lorsque la méthode est exécutée, le premier paramètre est lié à l’instance du type de données qui appelle la méthode.

L’attribut `Extension` ne peut être appliqué qu’à un Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md)ou [`Function`](../../../language-reference/statements/function-statement.md). Si vous l’appliquez à un `Class` ou à `Structure`, le compilateur Visual Basic génère l’erreur [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), l’attribut’extension’ne peut être appliqué qu’aux déclarations’module', 'Sub’ou’Function'.

## <a name="example"></a>Exemple

L’exemple suivant définit une extension `Print` pour le type de données <xref:System.String>. La méthode utilise `Console.WriteLine` pour afficher une chaîne. Le paramètre de la méthode `Print`, `aString`, établit que la méthode étend la classe <xref:System.String>.
  
[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

Notez que la définition de la méthode d’extension est marquée avec l’attribut d’extension `<Extension()>`. Le marquage du module dans lequel la méthode est définie est facultatif, mais chaque méthode d’extension doit être marquée. <xref:System.Runtime.CompilerServices> doit être importé pour accéder à l’attribut d’extension.

Les méthodes d’extension ne peuvent être déclarées que dans des modules. En général, le module dans lequel une méthode d’extension est définie n’est pas le même que celui dans lequel il est appelé. Au lieu de cela, le module qui contient la méthode d’extension est importé, si nécessaire, pour le placer dans la portée. Une fois que le module qui contient `Print` est dans la portée, la méthode peut être appelée comme s’il s’agissait d’une méthode d’instance ordinaire qui ne prend pas d’arguments, comme `ToUpper` :

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

L’exemple suivant, `PrintAndPunctuate`, est également une extension de <xref:System.String>, cette fois définie avec deux paramètres. Le premier paramètre, `aString`, établit que la méthode d’extension étend <xref:System.String>. Le deuxième paramètre, `punc`, est une chaîne de signes de ponctuation qui est transmise en tant qu’argument lorsque la méthode est appelée. La méthode affiche la chaîne suivie des signes de ponctuation.

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

La méthode est appelée en envoyant un argument de chaîne pour `punc` : `example.PrintAndPunctuate(".")`

L’exemple suivant montre `Print` et `PrintAndPunctuate` définis et appelés. <xref:System.Runtime.CompilerServices> est importé dans le module de définition afin d’autoriser l’accès à l’attribut d’extension.


```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

Ensuite, les méthodes d’extension sont mises en portée et appelées :

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

Tout ce qui est nécessaire pour pouvoir exécuter ces méthodes d’extension ou similaires, c’est qu’elles se trouvent dans la portée. Si le module qui contient une méthode d’extension est dans la portée, il est visible dans IntelliSense et peut être appelé comme s’il s’agissait d’une méthode d’instance ordinaire.

Notez que lorsque les méthodes sont appelées, aucun argument n’est envoyé dans pour le premier paramètre. Le paramètre `aString` dans les définitions de méthode précédentes est lié à `example`, l’instance de `String` qui les appelle. Le compilateur utilise `example` comme argument envoyé au premier paramètre.

Si une méthode d’extension est appelée pour un objet qui a la valeur `Nothing`, la méthode d’extension s’exécute. Cela ne s’applique pas aux méthodes d’instance ordinaires. Vous pouvez vérifier explicitement `Nothing` dans la méthode d’extension.

## <a name="types-that-can-be-extended"></a>Types pouvant être étendus

Vous pouvez définir une méthode d’extension sur la plupart des types qui peuvent être représentés dans une liste de paramètres Visual Basic, y compris les éléments suivants :

- Classes (types référence)
- Structures (types valeur)
- Interfaces
- Délégués
- Arguments ByRef et ByVal
- Paramètres de méthode générique
- Tableaux

Étant donné que le premier paramètre spécifie le type de données étendu par la méthode d’extension, il est obligatoire et ne peut pas être facultatif. Pour cette raison, les paramètres `Optional` et les paramètres de `ParamArray` ne peuvent pas être le premier paramètre de la liste de paramètres.

Les méthodes d’extension ne sont pas prises en compte dans la liaison tardive. Dans l’exemple suivant, l’instruction `anObject.PrintMe()` déclenche une exception <xref:System.MissingMemberException>, la même exception que vous pouvez voir si la deuxième définition de méthode d’extension `PrintMe` a été supprimée.

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a>meilleures pratiques recommandées.

Les méthodes d’extension offrent un moyen pratique et puissant d’étendre un type existant. Toutefois, pour les utiliser correctement, il existe des points à prendre en compte. Ces considérations s’appliquent principalement aux auteurs de bibliothèques de classes, mais elles peuvent affecter n’importe quelle application qui utilise des méthodes d’extension.

En règle générale, les méthodes d’extension que vous ajoutez aux types que vous ne possédez pas sont plus vulnérables que les méthodes d’extension ajoutées aux types que vous contrôlez. Un certain nombre de choses peuvent se produire dans les classes dont vous n’êtes pas propriétaire et qui peuvent interférer avec vos méthodes d’extension.

- S’il existe un membre d’instance accessible qui a une signature compatible avec les arguments de l’instruction d’appel, sans conversions restrictives requises d’argument en paramètre, la méthode d’instance est utilisée de préférence à toute méthode d’extension. Par conséquent, si une méthode d’instance appropriée est ajoutée à une classe à un moment donné, un membre d’extension existant sur lequel vous vous fiez peut devenir inaccessible.

- L’auteur d’une méthode d’extension ne peut pas empêcher d’autres programmeurs d’écrire des méthodes d’extension conflictuelles qui peuvent avoir priorité sur l’extension d’origine.

- Vous pouvez améliorer la robustesse en plaçant des méthodes d’extension dans leur propre espace de noms. Les consommateurs de votre bibliothèque peuvent alors inclure un espace de noms ou l’exclure, ou sélectionner parmi les espaces de noms, séparément du reste de la bibliothèque.

- Il peut être plus sûr d’étendre les interfaces que d’étendre les classes, en particulier si vous n’êtes pas propriétaire de l’interface ou de la classe. Une modification dans une interface affecte chaque classe qui l’implémente. Par conséquent, l’auteur peut être moins susceptible d’ajouter ou de modifier des méthodes dans une interface. Toutefois, si une classe implémente deux interfaces qui ont des méthodes d’extension avec la même signature, aucune méthode d’extension n’est visible.

- Étendez le type le plus spécifique que vous pouvez. Dans une hiérarchie de types, si vous sélectionnez un type à partir duquel de nombreux autres types sont dérivés, il existe des couches de possibilités pour l’introduction de méthodes d’instance ou d’autres méthodes d’extension qui peuvent interférer avec les vôtres.

## <a name="extension-methods-instance-methods-and-properties"></a>Méthodes d’extension, méthodes d’instance et propriétés

Quand une méthode d’instance dans la portée a une signature qui est compatible avec les arguments d’une instruction d’appel, la méthode d’instance est choisie de préférence à toute méthode d’extension. La méthode d’instance a la priorité, même si la méthode d’extension est une meilleure correspondance. Dans l’exemple suivant, `ExampleClass` contient une méthode d’instance nommée `ExampleMethod` qui a un paramètre de type `Integer`. La méthode d’extension `ExampleMethod` étend `ExampleClass` et a un paramètre de type `Long`.

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

Le premier appel à `ExampleMethod` dans le code suivant appelle la méthode d’extension, car `arg1` est `Long` et est compatible uniquement avec le paramètre `Long` dans la méthode d’extension. Le deuxième appel à `ExampleMethod` a un argument `Integer`, `arg2`, et il appelle la méthode d’instance.

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

À présent, inversez les types de données des paramètres dans les deux méthodes :

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

Cette fois, le code de `Main` appelle la méthode d’instance à la fois. Cela est dû au fait que `arg1` et `arg2` ont une conversion étendue en `Long`, et que la méthode d’instance est prioritaire sur la méthode d’extension dans les deux cas.

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

Par conséquent, une méthode d’extension ne peut pas remplacer une méthode d’instance existante. Toutefois, lorsqu’une méthode d’extension porte le même nom qu’une méthode d’instance, mais que les signatures ne sont pas en conflit, les deux méthodes sont accessibles. Par exemple, si la classe `ExampleClass` contient une méthode nommée `ExampleMethod` qui n’accepte aucun argument, les méthodes d’extension portant le même nom mais des signatures différentes sont autorisées, comme indiqué dans le code suivant.

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

Le résultat de ce code est le suivant :

```console
Extension method
Instance method
```

La situation est plus simple avec des propriétés : si une méthode d’extension porte le même nom qu’une propriété de la classe qu’elle étend, la méthode d’extension n’est pas visible et n’est pas accessible.

## <a name="extension-method-precedence"></a>Priorité de la méthode d’extension

Lorsque deux méthodes d’extension qui ont des signatures identiques sont dans la portée et sont accessibles, celle avec une priorité plus élevée est appelée. La priorité d’une méthode d’extension est basée sur le mécanisme utilisé pour mettre la méthode dans la portée. La liste suivante affiche la hiérarchie des priorités, du plus élevé au plus bas.

1. Méthodes d’extension définies dans le module en cours.

2. Méthodes d’extension définies dans les types de données de l’espace de noms actuel ou de l’un de ses parents, les espaces de noms enfants ayant une priorité plus élevée que les espaces de noms parents.

3. Méthodes d’extension définies dans les importations de type dans le fichier actuel.

4. Méthodes d’extension définies dans les importations d’espaces de noms dans le fichier actuel.

5. Méthodes d’extension définies dans les importations de type au niveau du projet.

6. Méthodes d’extension définies dans les importations d’espaces de noms au niveau du projet.

Si la précédence ne résout pas l’ambiguïté, vous pouvez utiliser le nom qualifié complet pour spécifier la méthode que vous appelez. Si la méthode `Print` dans l’exemple précédent est définie dans un module nommé `StringExtensions`, le nom qualifié complet est `StringExtensions.Print(example)` au lieu de `example.Print()`.

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Méthodes d’extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Module (instruction)](../../../language-reference/statements/module-statement.md)
- [Paramètres et arguments d’une procédure](procedure-parameters-and-arguments.md)
- [Paramètres facultatifs](optional-parameters.md)
- [tableaux de paramètres](parameter-arrays.md)
- [Vue d’ensemble des attributs](../../concepts/attributes/index.md)
- [Étendue dans Visual Basic](../declared-elements/scope.md)
