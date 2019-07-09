---
title: Declare (instruction) (Visual Basic)
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
ms.openlocfilehash: 6ff20af1ef439e27cffaf306c7917dbc98a419ce
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662910"
---
# <a name="declare-statement"></a>Declare Statement

Déclare une référence à une procédure implémentée dans un fichier externe.

## <a name="syntax"></a>Syntaxe

```
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
|`attributelist`|Facultatif. Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|Facultatif. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Protected Friend](../../language-reference/modifiers/protected-friend.md)<br />- [Private protégé](../../language-reference/modifiers/private-protected.md)<br /><br /> Consultez [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Facultatif. Consultez [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|Facultatif. Spécifie le jeu de caractères et le fichier d’informations de recherche. Il peut s'agir d'une des valeurs suivantes :<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (valeur par défaut)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Auto](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|Facultatif, mais `Sub` ou `Function` doit apparaître. Indique que la procédure externe ne retourne pas de valeur.|
|`Function`|Facultatif, mais `Sub` ou `Function` doit apparaître. Indique que la procédure externe retourne une valeur.|
|`name`|Obligatoire. Nom de cette référence externe. Pour plus d’informations, consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Obligatoire. Introduit un `Lib` clause qui identifie le fichier externe (DLL ou ressource de code) qui contient une procédure externe.|
|`libname`|Obligatoire. Nom du fichier qui contient la procédure déclarée.|
|`Alias`|Facultatif. Indique que la procédure déclarée ne peut pas être identifiée dans son fichier par le nom spécifié dans `name`. Vous spécifiez son identification dans `aliasname`.|
|`aliasname`|Requis si vous utilisez le `Alias` mot clé. Chaîne qui identifie la procédure de deux manières :<br /><br /> Le nom de point d’entrée de la procédure dans son fichier, entre guillemets (`""`)<br /><br /> ou<br /><br /> Un signe dièse (`#`) suivie d’un entier spécifiant le nombre ordinal du point d’entrée de la procédure dans son fichier|
|`parameterlist`|Obligatoire si la procédure accepte des paramètres. Consultez [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|Obligatoire si `Function` est spécifié et `Option Strict` est `On`. Type de données de la valeur retournée par la procédure.|

## <a name="remarks"></a>Notes

Parfois, vous devez appeler une procédure définie dans un fichier (par exemple, une DLL ou ressource de code) en dehors de votre projet. Lorsque vous effectuez cette opération, le compilateur Visual Basic n’a pas accès aux informations requises pour appeler la procédure correctement, tels qu’où se trouve la procédure, comment il est identifié, sa séquence d’appel et type de retour et le jeu de caractères de chaîne qu’il utilise. La `Declare` instruction crée une référence à une procédure externe et fournit ces informations nécessaires.

Vous pouvez utiliser `Declare` seulement au niveau du module. Cela signifie que le *contexte de déclaration* pour une référence externe doit être une classe, une structure ou un module et ne peut pas être un fichier source, un espace de noms, une interface, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Par défaut pour des références externes [Public](../../../visual-basic/language-reference/modifiers/public.md) accès. Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.

## <a name="rules"></a>Règles

- **Attributs.** Vous pouvez appliquer des attributs à une référence externe. N’importe quel attribut que vous appliquez a effet uniquement dans votre projet, et non dans le fichier externe.

- **Modificateurs.** Procédures externes sont implicitement [partagé](../../../visual-basic/language-reference/modifiers/shared.md). Vous ne pouvez pas utiliser le `Shared` mot clé lors de la déclaration d’une référence externe et vous ne pouvez pas modifier son état partagé.

  Une procédure externe ne peut pas participer à la substitution, implémenter des membres d’interface ou gérer des événements. En conséquence, vous ne pouvez pas utiliser le `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`, ou `Handles` mot clé dans un `Declare` instruction.

- **Nom de la procédure externe.** Vous n’êtes pas obligé de donner à cette référence externe le même nom (dans `name`) en tant que nom de point d’entrée de la procédure dans son fichier externe (`aliasname`). Vous pouvez utiliser un `Alias` clause pour spécifier le nom de point d’entrée. Cela peut être utile si la procédure externe a le même nom qu’un modificateur réservé Visual Basic ou une variable, procédure ou tout autre élément de programmation dans la même portée.

  > [!NOTE]
  > Les noms de point d’entrée dans la plupart des DLL respectent la casse.

- **Numéro de procédure externe.** Vous pouvez également utiliser un `Alias` clause pour spécifier le nombre ordinal du point d’entrée dans la table d’exportation du fichier externe. Pour ce faire, vous commencez `aliasname` par un signe dièse (`#`). Cela peut être utile si n’importe quel caractère dans le nom de la procédure externe n’est pas autorisée en Visual Basic, ou si le fichier externe exporte la procédure sans nom.

## <a name="data-type-rules"></a>Règles de Type de données

- **Types de données de paramètre.** Si `Option Strict` est `On`, vous devez spécifier le type de données de chaque paramètre dans `parameterlist`. Cela peut être n’importe quel type de données ou le nom d’une énumération, une structure, une classe ou une interface. Dans `parameterlist`, vous utilisez un `As` clause pour spécifier le type de données de l’argument à passer à chaque paramètre.

  > [!NOTE]
  > Si la procédure externe a été pas écrit pour le .NET Framework, vous devez veiller les types de données correspondant. Par exemple, si vous déclarez une référence à une procédure Visual Basic 6.0 avec un `Integer` paramètre (16 bits dans Visual Basic 6.0), vous devez identifier l’argument correspondant en tant que `Short` dans le `Declare` instruction, car il s’agit du 16 - type d’entier de bit en Visual Basic. De même, `Long` a une largeur de données différente dans Visual Basic 6.0, et `Date` est implémenté différemment.

- **Retourner le Type de données.** Si la procédure externe est un `Function` et `Option Strict` est `On`, vous devez spécifier le type de données de la valeur retournée au code appelant. Cela peut être n’importe quel type de données ou le nom d’une énumération, une structure, une classe ou une interface.

  > [!NOTE]
  > Le compilateur Visual Basic ne vérifie pas que vos types de données sont compatibles avec ceux de la procédure externe. S’il existe une incompatibilité, le common language runtime génère un <xref:System.Runtime.InteropServices.MarshalDirectiveException> exception au moment de l’exécution.

- **Types de données par défaut.** Si `Option Strict` est `Off` et vous ne spécifiez pas le type de données d’un paramètre dans `parameterlist`, le compilateur Visual Basic convertit l’argument correspondant à la [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md). De même, si vous ne spécifiez pas `returntype`, le compilateur prend le type de données de retour soit `Object`.

  > [!NOTE]
  > Étant donné que vous êtes confronté à une procédure externe a pu être écrite sur une plateforme différente, il est dangereux de faire des hypothèses sur les types de données ou pour leur permettre de par défaut. Il est beaucoup plus sûre spécifier le type de données de chaque paramètre et la valeur de retour, le cas échéant. Cela améliore également la lisibilité de votre code.

## <a name="behavior"></a>Comportement

- **Étendue.** Une référence externe est dans l’étendue tout au long de sa classe, une structure ou un module.

- **Lifetime.** Une référence externe a la même durée de vie que la classe, une structure ou un module dans lequel elle est déclarée.

- **Appel d’une procédure externe.** Vous appelez une procédure externe de la même façon que vous appelez un `Function` ou `Sub` procédure — à l’aide dans une expression si elle retourne une valeur, ou en le spécifiant dans un [instruction Call](../../../visual-basic/language-reference/statements/call-statement.md) si elle ne retourne pas une valeur.

  Passer des arguments à la procédure externe exactement comme spécifié par `parameterlist` dans le `Declare` instruction. Ne prennent pas en compte comment les paramètres ont été déclarés à l’origine dans le fichier externe. De même, s’il existe une valeur de retour, utilisez-la exactement comme spécifié par `returntype` dans le `Declare` instruction.

- **Jeux de caractères.** Vous pouvez spécifier dans `charsetmodifier` comment Visual Basic doit marshaler les chaînes lorsqu’il appelle la procédure externe. Le `Ansi` modificateur dirige Visual Basic de marshaler toutes les chaînes en valeurs ANSI et le `Unicode` modificateur lui indique de marshaler toutes les chaînes en valeurs Unicode. Le `Auto` modificateur dirige Visual Basic pour marshaler des chaînes en fonction de .NET Framework des règles en fonction de la référence externe `name`, ou `aliasname` si spécifié. La valeur par défaut est `Ansi`.

  `charsetmodifier` Spécifie également comment Visual Basic doit rechercher la procédure externe dans son fichier externe. `Ansi` et `Unicode` à la fois diriger Visual Basic à rechercher sans modifier son nom lors de la recherche. `Auto` Indique à Visual Basic pour déterminer le jeu de caractères de base de la plateforme d’exécution et éventuellement modifier le nom de la procédure externe, comme suit :

  - Sur une plateforme ANSI, tels que Windows 95, Windows 98 ou Windows Millennium Edition, recherchez d’abord la procédure externe sans modifier son nom. En cas d’échec, ajoutez « A » à la fin du nom de procédure externe et recherchez-la à nouveau.

  - Sur une plateforme Unicode, tels que Windows NT, Windows 2000 ou Windows XP, recherchez d’abord la procédure externe sans modifier son nom. Si cette tentative échoue, ajoutez « W » à la fin de la procédure externe nommer et rechercher à nouveau.

- **Mécanisme.** Visual Basic utilise le .NET Framework *non managé* mécanisme (PInvoke) pour résoudre et accéder aux procédures externes. Le `Declare` instruction et la <xref:System.Runtime.InteropServices.DllImportAttribute> classe les deux utilisent ce mécanisme automatiquement et vous n’avez pas besoin d’aucune connaissance de PInvoke. Pour plus d’informations, consultez [Procédure pas à pas : Appel d’API de Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Si la procédure externe s’exécute en dehors du common language runtime (CLR), il est *du code non managé*. Lorsque vous appelez une telle procédure, par exemple une fonction API de Windows ou une méthode COM, vous pouvez exposer votre application à des risques de sécurité. Pour plus d’informations, consultez [instructions de codage sécurisé pour le Code non managé](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).

## <a name="example"></a>Exemple

L’exemple suivant déclare une référence externe à un `Function` procédure qui retourne le nom d’utilisateur actuel. Il appelle ensuite la procédure externe `GetUserNameA` dans le cadre de la `getUser` procédure.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Exemple

Le <xref:System.Runtime.InteropServices.DllImportAttribute> offre un autre moyen de l’utilisation de fonctions dans le code non managé. L’exemple suivant déclare une fonction importée sans utiliser un `Declare` instruction.

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
