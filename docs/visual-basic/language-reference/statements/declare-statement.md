---
title: Instruction DECLARE (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
ms.openlocfilehash: e839fe14c360229fbe0350fd7878c7a844056e8b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005093"
---
# <a name="declare-statement"></a>Declare Statement

Déclare une référence à une procédure implémentée dans un fichier externe.

## <a name="syntax"></a>Syntaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ]
' -or-
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]
```

## <a name="parts"></a>Composants

|Terme|Définition|
|---|---|
|`attributelist`|facultatif. Consultez la [liste des attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|facultatif. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privé](../../../visual-basic/language-reference/modifiers/private.md)<br />- [ami protégé](../../language-reference/modifiers/protected-friend.md)<br />- [protection privée](../../language-reference/modifiers/private-protected.md)<br /><br /> Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|facultatif. Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|facultatif. Spécifie le jeu de caractères et les informations de recherche de fichier. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (par défaut)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [auto](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|Facultatif, mais `Sub` ou `Function` doit apparaître. Indique que la procédure externe ne retourne pas de valeur.|
|`Function`|Facultatif, mais `Sub` ou `Function` doit apparaître. Indique que la procédure externe retourne une valeur.|
|`name`|Obligatoire. Nom de cette référence externe. Pour plus d’informations, consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Obligatoire. Introduit une clause `Lib`, qui identifie le fichier externe (DLL ou ressource de code) qui contient une procédure externe.|
|`libname`|Obligatoire. Nom du fichier qui contient la procédure déclarée.|
|`Alias`|facultatif. Indique que la procédure déclarée ne peut pas être identifiée dans son fichier par le nom spécifié dans `name`. Vous spécifiez son identification dans `aliasname`.|
|`aliasname`|Obligatoire si vous utilisez le mot clé `Alias`. Chaîne qui identifie la procédure de l’une des deux manières suivantes :<br /><br /> Nom du point d’entrée de la procédure dans son fichier, entre guillemets (`""`)<br /><br /> \- ou -<br /><br /> Signe dièse (`#`) suivi d’un entier spécifiant le numéro ordinal du point d’entrée de la procédure dans son fichier.|
|`parameterlist`|Obligatoire si la procédure accepte des paramètres. Consultez la [liste des paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|Obligatoire si `Function` est spécifié et que `Option Strict` est `On`. Type de données de la valeur retournée par la procédure.|

## <a name="remarks"></a>Notes

Parfois, vous devez appeler une procédure définie dans un fichier (par exemple, une DLL ou une ressource de code) en dehors de votre projet. Dans ce cas, le compilateur Visual Basic n’a pas accès aux informations dont il a besoin pour appeler la procédure correctement, par exemple où se trouve la procédure, comment elle est identifiée, sa séquence d’appel et son type de retour, ainsi que le jeu de caractères de chaîne qu’elle utilise. L’instruction `Declare` crée une référence à une procédure externe et fournit ces informations nécessaires.

Vous pouvez utiliser `Declare` seulement au niveau du module. Cela signifie que le *contexte de déclaration* pour une référence externe doit être une classe, une structure ou un module, et ne peut pas être un fichier source, un espace de noms, une interface, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

La valeur par défaut des références externes est accès [public](../../../visual-basic/language-reference/modifiers/public.md) . Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.

## <a name="rules"></a>Règles

- **Attributs.** Vous pouvez appliquer des attributs à une référence externe. Tout attribut que vous appliquez n’a d’effet que dans votre projet, et non dans le fichier externe.

- **Modificateurs.** Les procédures externes sont [partagées](../../../visual-basic/language-reference/modifiers/shared.md)implicitement. Vous ne pouvez pas utiliser le mot clé `Shared` lors de la déclaration d’une référence externe, et vous ne pouvez pas modifier son état partagé.

  Une procédure externe ne peut pas participer à la substitution, à l’implémentation des membres d’interface ou à la gestion des événements. En conséquence, vous ne pouvez pas utiliser le mot clé `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements` ou `Handles` dans une instruction `Declare`.

- **Nom de la procédure externe.** Vous n’avez pas besoin de fournir à cette référence externe le même nom (dans `name`) que le nom du point d’entrée de la procédure dans son fichier externe (`aliasname`). Vous pouvez utiliser une clause `Alias` pour spécifier le nom du point d’entrée. Cela peut être utile si la procédure externe a le même nom qu’un modificateur réservé Visual Basic ou une variable, une procédure ou tout autre élément de programmation dans la même portée.

  > [!NOTE]
  > Les noms de point d’entrée dans la plupart des dll respectent la casse.

- **Numéro de la procédure externe.** Vous pouvez également utiliser une clause `Alias` pour spécifier le numéro ordinal du point d’entrée dans la table d’exportation du fichier externe. Pour ce faire, vous devez commencer `aliasname` par un signe dièse (`#`). Cela peut être utile si un caractère du nom de la procédure externe n’est pas autorisé dans Visual Basic, ou si le fichier externe exporte la procédure sans nom.

## <a name="data-type-rules"></a>Règles de type de données

- **Types de données de paramètre.** Si `Option Strict` est `On`, vous devez spécifier le type de données de chaque paramètre dans `parameterlist`. Il peut s’agir de n’importe quel type de données ou du nom d’une énumération, d’une structure, d’une classe ou d’une interface. Dans `parameterlist`, vous utilisez une clause `As` pour spécifier le type de données de l’argument à passer à chaque paramètre.

  > [!NOTE]
  > Si la procédure externe n’a pas été écrite pour la .NET Framework, vous devez veiller à ce que les types de données correspondent. Par exemple, si vous déclarez une référence externe à une procédure Visual Basic 6,0 avec un paramètre `Integer` (16 bits dans Visual Basic 6,0), vous devez identifier l’argument correspondant comme `Short` dans l’instruction `Declare`, car il s’agit du type entier 16 bits dans Visual Basic. De même, `Long` a une largeur de données différente dans Visual Basic 6,0 et `Date` est implémenté différemment.

- **Retourne le type de données.** Si la procédure externe est un `Function` et que `Option Strict` est `On`, vous devez spécifier le type de données de la valeur retournée au code appelant. Il peut s’agir de n’importe quel type de données ou du nom d’une énumération, d’une structure, d’une classe ou d’une interface.

  > [!NOTE]
  > Le compilateur Visual Basic ne vérifie pas si vos types de données sont compatibles avec ceux de la procédure externe. En cas d’incompatibilité, le common language runtime génère une exception <xref:System.Runtime.InteropServices.MarshalDirectiveException> au moment de l’exécution.

- **Types de données par défaut.** Si `Option Strict` est `Off` et que vous ne spécifiez pas le type de données d’un paramètre dans `parameterlist`, le compilateur de Visual Basic convertit l’argument correspondant en [type de données](../../../visual-basic/language-reference/data-types/object-data-type.md)de l’objet. De même, si vous ne spécifiez pas `returntype`, le compilateur prend le type de données de retour à `Object`.

  > [!NOTE]
  > Étant donné que vous travaillez avec une procédure externe qui a pu être écrite sur une autre plateforme, il est dangereux de faire des hypothèses sur les types de données ou de les autoriser par défaut. Il est plus sûr de spécifier le type de données de chaque paramètre et de la valeur de retour, le cas échéant. Cela améliore également la lisibilité de votre code.

## <a name="behavior"></a>Comportement

- **Étendue.** Une référence externe est dans la portée de la classe, de la structure ou du module.

- **Cycle.** Une référence externe a la même durée de vie que la classe, la structure ou le module dans lequel elle est déclarée.

- **Appel d’une procédure externe.** Vous appelez une procédure externe de la même façon que vous appelez une procédure `Function` ou `Sub`, en l’utilisant dans une expression si elle retourne une valeur, ou en la spécifiant dans une [instruction call](../../../visual-basic/language-reference/statements/call-statement.md) si elle ne retourne pas de valeur.

  Vous transmettez des arguments à la procédure externe exactement comme spécifié par `parameterlist` dans l’instruction `Declare`. Ne prenez pas en compte la façon dont les paramètres ont été initialement déclarés dans le fichier externe. De même, s’il existe une valeur de retour, utilisez-la exactement comme spécifié par `returntype` dans l’instruction `Declare`.

- **Jeux de caractères.** Vous pouvez spécifier dans `charsetmodifier` comment Visual Basic doit marshaler des chaînes lorsqu’il appelle la procédure externe. Le modificateur `Ansi` ordonne à Visual Basic de marshaler toutes les chaînes en valeurs ANSI, et le modificateur `Unicode` lui demande de marshaler toutes les chaînes en valeurs Unicode. Le modificateur `Auto` dirige Visual Basic pour marshaler les chaînes en fonction des règles de .NET Framework en fonction de la référence externe `name` ou `aliasname` si elle est spécifiée. La valeur par défaut est `Ansi`.

  `charsetmodifier` spécifie également comment Visual Basic doit rechercher la procédure externe dans son fichier externe. `Ansi` et `Unicode` Visual Basic directe pour le Rechercher sans modifier son nom au cours de la recherche. `Auto` dirige Visual Basic pour déterminer le jeu de caractères de base de la plateforme Runtime et éventuellement modifier le nom de la procédure externe, comme suit :

  - Sur une plateforme ANSI, telle que Windows 95, Windows 98 ou Windows Millennium Edition, recherchez d’abord la procédure externe sans modification de nom. En cas d’échec, ajoutez « A » à la fin du nom de la procédure externe et recommencez la recherche.

  - Sur une plateforme Unicode, telle que Windows NT, Windows 2000 ou Windows XP, recherchez d’abord la procédure externe sans modification de nom. En cas d’échec, ajoutez « W » à la fin du nom de la procédure externe et recommencez la recherche.

- **Procédé.** Visual Basic utilise le mécanisme d’appel de code non *managé* .NET Framework (PInvoke) pour résoudre des procédures externes et y accéder. L’instruction `Declare` et la classe <xref:System.Runtime.InteropServices.DllImportAttribute> utilisent tous deux automatiquement ce mécanisme, et vous n’avez pas besoin de connaître PInvoke. Pour plus d’informations, consultez [Procédure pas à pas : Appel des API Windows @ no__t-0.

> [!IMPORTANT]
> Si la procédure externe s’exécute en dehors du common language runtime (CLR), il s’agit d’un *code non managé*. Lorsque vous appelez une telle procédure, par exemple une fonction d’API Windows ou une méthode COM, vous pouvez exposer votre application à des risques de sécurité. Pour plus d’informations, consultez [recommandations en matière de codage sécurisé pour le code non managé](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).

## <a name="example"></a>Exemple

L’exemple suivant déclare une référence externe à une procédure `Function` qui retourne le nom d’utilisateur actuel. Il appelle ensuite la procédure externe `GetUserNameA` dans le cadre de la procédure `getUser`.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Exemple

La <xref:System.Runtime.InteropServices.DllImportAttribute> fournit une autre façon d’utiliser des fonctions dans du code non managé. L’exemple suivant déclare une fonction importée sans utiliser d’instruction `Declare`.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Imports (instruction) (espace de noms et type .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Call (instruction)](../../../visual-basic/language-reference/statements/call-statement.md)
- [Procédure pas à pas : Appel des API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
