---
title: Procédures de propriété
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: a4b8ac3e27348764f537ee9502ce1fbb165bb3ef
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352562"
---
# <a name="property-procedures-visual-basic"></a>Procédures de propriété (Visual Basic)

Une procédure de propriété est une série d’instructions Visual Basic qui manipulent une propriété personnalisée sur un module, une classe ou une structure. Les procédures de propriété sont également appelées *accesseurs de propriété*.

Visual Basic fournit les procédures de propriété suivantes :

- Une procédure `Get` retourne la valeur d’une propriété. Elle est appelée lorsque vous accédez à la propriété dans une expression.
- Une procédure `Set` affecte une valeur à une propriété, y compris une référence d’objet. Elle est appelée lorsque vous assignez une valeur à la propriété.

Vous définissez généralement des procédures de propriété par paires, à l’aide des instructions `Get` et `Set`, mais vous pouvez définir l’une ou l’autre procédure uniquement si la propriété est en lecture seule ([instruction d’extraction](../../../../visual-basic/language-reference/statements/get-statement.md)) ou en écriture seule ([instruction Set](../../../../visual-basic/language-reference/statements/set-statement.md)).

Vous pouvez omettre les `Get` et `Set` procédure lors de l’utilisation d’une propriété implémentée automatiquement. Pour plus d’informations, consultez [Propriétés implémentées automatiquement](./auto-implemented-properties.md).

Vous pouvez définir des propriétés dans des classes, des structures et des modules. Les propriétés sont `Public` par défaut, ce qui signifie que vous pouvez les appeler à partir de n’importe où dans votre application qui peut accéder au conteneur de la propriété.

Pour une comparaison des propriétés et des variables, consultez [différences entre les propriétés et les variables dans Visual Basic](differences-between-properties-and-variables.md).

## <a name="declaration-syntax"></a>Syntaxe de déclaration

Une propriété elle-même est définie par un bloc de code placé entre l' [instruction Property](../../../../visual-basic/language-reference/statements/property-statement.md) et l’instruction `End Property`. À l’intérieur de ce bloc, chaque procédure de propriété apparaît sous la forme d’un bloc interne délimité par une instruction de déclaration (`Get` ou `Set`) et de la déclaration de `End` correspondante.

La syntaxe de déclaration d’une propriété et de ses procédures est la suivante :

```vb
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]
    [AccessLevel] Get
        ' Statements of the Get procedure.
        ' The following statement returns an expression as the property's value.
        Return Expression
    End Get
    [AccessLevel] Set[(ByVal NewValue As DataType)]
        ' Statements of the Set procedure.
        ' The following statement assigns newvalue as the property's value.
        LValue = NewValue
    End Set
End Property
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

La `Modifiers` peut spécifier le niveau d’accès et les informations relatives à la surcharge, à la substitution, au partage et à l’occultation, ainsi que la propriété en lecture seule ou en écriture seule. La `AccessLevel` sur la procédure `Get` ou `Set` peut être n’importe quel niveau qui est plus restrictif que le niveau d’accès spécifié pour la propriété elle-même. Pour plus d’informations, consultez [Property, instruction](../../../../visual-basic/language-reference/statements/property-statement.md).

### <a name="data-type"></a>Type de données

Le type de données et le niveau d’accès principal d’une propriété sont définis dans l’instruction `Property`, pas dans les procédures de propriété. Une propriété ne peut avoir qu’un seul type de données. Par exemple, vous ne pouvez pas définir une propriété pour stocker une valeur de `Decimal`, mais récupérer une valeur de `Double`.

### <a name="access-level"></a>Niveau d’accès

Toutefois, vous pouvez définir un niveau d’accès principal pour une propriété et restreindre davantage le niveau d’accès dans l’une de ses procédures de propriété. Par exemple, vous pouvez définir une propriété `Public`, puis définir une procédure `Private Set`. La procédure `Get` reste `Public`. Vous pouvez modifier le niveau d’accès dans une seule des procédures d’une propriété, et vous pouvez le rendre plus restrictif que le niveau d’accès du principal. Pour plus d’informations, consultez [Comment : déclarer une propriété avec des niveaux d’accès mixtes](how-to-declare-a-property-with-mixed-access-levels.md).

## <a name="parameter-declaration"></a>Déclaration de paramètre

Vous déclarez chaque paramètre de la même façon que pour les [procédures Sub](sub-procedures.md), à ceci près que le mécanisme de passage doit être `ByVal`.

La syntaxe de chaque paramètre dans la liste de paramètres est la suivante :

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration. La syntaxe permettant de spécifier une valeur par défaut est la suivante :

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a>Valeur de la propriété

Dans une procédure `Get`, la valeur de retour est fournie à l’expression appelante comme valeur de la propriété.

Dans une procédure `Set`, la nouvelle valeur de propriété est passée au paramètre de l’instruction `Set`. Si vous déclarez explicitement un paramètre, vous devez le déclarer avec le même type de données que la propriété. Si vous ne déclarez pas de paramètre, le compilateur utilise le paramètre implicite `Value` pour représenter la nouvelle valeur à assigner à la propriété.

## <a name="calling-syntax"></a>Syntaxe d’appel

Vous appelez une procédure de propriété implicitement en faisant référence à la propriété. Vous utilisez le nom de la propriété de la même façon que vous utilisez le nom d’une variable, mais vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses. Si aucun argument n’est fourni, vous pouvez éventuellement omettre les parenthèses.

La syntaxe d’un appel implicite à une procédure `Set` se présente comme suit :

```vb
propertyname[(argumentlist)] = expression
```

La syntaxe d’un appel implicite à une procédure `Get` se présente comme suit :

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a>Illustration de la déclaration et de l’appel

La propriété suivante stocke un nom complet sous la forme de deux noms constitutifs, le prénom et le nom. Lorsque le code appelant lit `fullName`, la procédure `Get` combine les deux noms constitutifs et retourne le nom complet. Lorsque le code appelant assigne un nouveau nom complet, la procédure `Set` tente de la décomposer en deux noms constitutifs. S’il ne trouve pas d’espace, il le stocke comme premier nom.

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

L’exemple suivant montre des appels classiques aux procédures de propriété de `fullName`:

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a>Voir aussi

- [Procédures](index.md)
- [Procédures Function](function-procedures.md)
- [Procédures d’opérateur](operator-procedures.md)
- [Paramètres et arguments d’une procédure](procedure-parameters-and-arguments.md)
- [Différences entre les propriétés et les variables dans Visual Basic](differences-between-properties-and-variables.md)
- [Guide pratique : créer une propriété](how-to-create-a-property.md)
- [Guide pratique : appeler une procédure de propriété](how-to-call-a-property-procedure.md)
- [Comment : déclarer et appeler une propriété par défaut dans Visual Basic](how-to-declare-and-call-a-default-property.md)
- [Guide pratique : placer une valeur dans une propriété](how-to-put-a-value-in-a-property.md)
- [Guide pratique : obtenir une valeur d’une propriété](how-to-get-a-value-from-a-property.md)
