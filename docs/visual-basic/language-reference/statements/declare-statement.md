---
title: Declare Statement
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
ms.openlocfilehash: 9895709076634ce156ba9d1009f79ba7ddd2ba56
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646381"
---
# <a name="declare-statement"></a>Declare Statement

Déclare une référence à une procédure mise en œuvre dans un fichier externe.

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

## <a name="parts"></a>Éléments

|Terme|Définition|
|---|---|
|`attributelist`|facultatif. Voir [Liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|facultatif. Il peut s'agir d'une des méthodes suivantes :<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Ami](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Ami protégé](../../language-reference/modifiers/protected-friend.md)<br />- [Privé protégé](../../language-reference/modifiers/private-protected.md)<br /><br /> Voir [les niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|facultatif. Voir [Ombres](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|facultatif. Spécifie les informations de recherche de caractères et de fichiers. Il peut s'agir d'une des méthodes suivantes :<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) (par défaut)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [auto](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|Facultatif, `Sub` `Function` mais l’un ou l’autre ou doit apparaître. Indique que la procédure externe ne retourne pas de valeur.|
|`Function`|Facultatif, `Sub` `Function` mais l’un ou l’autre ou doit apparaître. Indique que la procédure externe retourne une valeur.|
|`name`|Obligatoire. Nom de cette référence externe. Pour plus d’informations, voir [Noms d’élément déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Obligatoire. Introduit une `Lib` clause, qui identifie le fichier externe (DLL ou ressource de code) qui contient une procédure externe.|
|`libname`|Obligatoire. Nom du fichier qui contient la procédure déclarée.|
|`Alias`|facultatif. Indique que la procédure déclarée ne peut pas `name`être identifiée dans son dossier par le nom spécifié dans . Vous spécifiez son identification dans `aliasname`.|
|`aliasname`|Nécessaire si vous `Alias` utilisez le mot clé. Chaîne qui identifie la procédure de deux façons :<br /><br /> Le nom du point d’entrée de`""`la procédure dans son fichier, dans les devis ( )<br /><br /> -ou-<br /><br /> Un signe`#`de numéro ( ) suivi d’un intégrant précisant le numéro ordinaire du point d’entrée de la procédure dans son dossier|
|`parameterlist`|Nécessaire si la procédure prend des paramètres. Voir [La liste des paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|Nécessaire `Function` si elle `Option Strict` `On`est spécifiée et est . Type de données de la valeur retournée par la procédure.|

## <a name="remarks"></a>Notes

Parfois, vous devez appeler une procédure définie dans un fichier (comme une DLL ou une ressource de code) en dehors de votre projet. Lorsque vous faites cela, le compilateur Visual Basic n’a pas accès aux informations dont il a besoin pour appeler la procédure correctement, comme l’endroit où la procédure est située, comment il est identifié, sa séquence d’appel et le type de retour, et le jeu de caractère de chaîne qu’il utilise. La `Declare` déclaration crée une référence à une procédure externe et fournit ces informations nécessaires.

Vous pouvez utiliser `Declare` seulement au niveau du module. Cela signifie que le *contexte de déclaration* d’une référence externe doit être une classe, une structure ou un module, et ne peut pas être un fichier source, un espace de nom, une interface, une procédure ou un bloc. Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Références externes par défaut à l’accès [public.](../../../visual-basic/language-reference/modifiers/public.md) Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.

## <a name="rules"></a>Règles

- **Attributs.** Vous pouvez appliquer des attributs à une référence externe. Tout attribut que vous appliquez n’a d’effet que dans votre projet, et non dans le fichier externe.

- **Modificateurs.** Les procédures externes sont implicitement [partagées](../../../visual-basic/language-reference/modifiers/shared.md). Vous ne `Shared` pouvez pas utiliser le mot clé lors de la déclaration d’une référence externe, et vous ne pouvez pas modifier son statut partagé.

  Une procédure externe ne peut pas participer à la suppression, implémenter les membres de l’interface ou gérer des événements. En conséquence, vous `Overrides` `Overridable`ne `NotOverridable` `MustOverride`pouvez `Implements`pas `Handles` utiliser `Declare` le , , , , ou mot clé dans une déclaration.

- **Nom de procédure externe.** Vous n’avez pas à donner à `name`cette référence externe le même nom (dans`aliasname`) que le nom d’entrée de la procédure dans son fichier externe ( ). Vous pouvez `Alias` utiliser une clause pour spécifier le nom du point d’entrée. Cela peut être utile si la procédure externe porte le même nom qu’un modificateur réservé Visual Basic ou une variable, une procédure ou tout autre élément de programmation dans la même portée.

  > [!NOTE]
  > Les noms de points d’entrée dans la plupart des DLL sont sensibles aux cas.

- **Numéro de procédure externe.** Vous pouvez également utiliser `Alias` une clause pour spécifier le numéro ordinaire du point d’entrée dans le tableau d’exportation du fichier externe. Pour ce faire, `aliasname` vous commencez`#`par un signe de nombre ( ). Cela peut être utile si un personnage dans le nom de la procédure externe n’est pas autorisé dans Visual Basic, ou si le fichier externe exporte la procédure sans nom.

## <a name="data-type-rules"></a>Règles de type de données

- **Types de données paramètres.** Si `Option Strict` `On`c’est le cas, vous `parameterlist`devez spécifier le type de données de chaque paramètre dans . Il peut s’agir de n’importe quel type de données ou le nom d’un recensement, d’une structure, d’une classe ou d’une interface. Dans `parameterlist`le cadre, vous utilisez une `As` clause pour spécifier le type de données de l’argument à transmettre à chaque paramètre.

  > [!NOTE]
  > Si la procédure externe n’a pas été écrite pour le cadre .NET, vous devez prendre soin que les types de données correspondent. Par exemple, si vous déclarez une référence externe à une `Integer` procédure Visual Basic 6.0 avec un paramètre (16 `Declare` bits dans Visual Basic 6.0), vous devez identifier l’argument correspondant comme dans l’énoncé, `Short` parce que c’est le type d’intégré 16 bits dans Visual Basic. De `Long` même, a une largeur de données différente `Date` dans Visual Basic 6.0, et est mis en œuvre différemment.

- **Type de données de retour.** Si la procédure `Function` externe `Option Strict` `On`est un et est, vous devez spécifier le type de données de la valeur retournée au code d’appel. Il peut s’agir de n’importe quel type de données ou le nom d’un recensement, d’une structure, d’une classe ou d’une interface.

  > [!NOTE]
  > Le compilateur Visual Basic ne vérifie pas que vos types de données sont compatibles avec ceux de la procédure externe. S’il y a un décalage, le temps <xref:System.Runtime.InteropServices.MarshalDirectiveException> de course de langue commun génère une exception au moment de l’exécution.

- **Types de données par défaut.** Si `Option Strict` `Off` est et vous ne spécifiez pas le type de données d’un paramètre dans `parameterlist`, le compilateur de base visuelle convertit l’argument correspondant au type de données [d’objet](../../../visual-basic/language-reference/data-types/object-data-type.md). De même, si `returntype`vous ne spécifiez pas `Object`, le compilateur prend le type de données de retour pour être .

  > [!NOTE]
  > Étant donné que vous avez affaire à une procédure externe qui aurait pu être écrite sur une plate-forme différente, il est dangereux de faire des hypothèses sur les types de données ou de leur permettre de faire défaut. Il est beaucoup plus sûr de spécifier le type de données de chaque paramètre et de la valeur de retour, le cas échéant. Cela améliore également la lisibilité de votre code.

## <a name="behavior"></a>Comportement

- **Portée.** Une référence externe est de portée dans toute sa classe, sa structure ou son module.

- **Vie.** Une référence externe a la même durée de vie que la classe, la structure ou le module dans lequel elle est déclarée.

- **Appel à une procédure externe.** Vous appelez une procédure externe de `Function` `Sub` la même façon que vous appelez une procédure ou une procédure, en l’utilisant dans une expression si elle retourne une valeur, ou en la spécifiant dans une [déclaration d’appel](../../../visual-basic/language-reference/statements/call-statement.md) si elle ne retourne pas une valeur.

  Vous transmettez des arguments à la `parameterlist` procédure `Declare` externe exactement comme spécifié dans la déclaration. Ne prenez pas en compte la façon dont les paramètres ont été initialement déclarés dans le fichier externe. De même, s’il y a une `returntype` valeur `Declare` de retour, utilisez-la exactement comme spécifié dans l’énoncé.

- **Ensembles de personnages.** Vous pouvez `charsetmodifier` spécifier dans la façon dont Visual Basic devrait marshal cordes quand il appelle la procédure externe. Le `Ansi` modificateur dirige Visual Basic pour rassembler toutes `Unicode` les chaînes vers les valeurs DE l’ANSI, et le modificateur l’oriente vers le maréchal toutes les cordes vers les valeurs Unicode. Le `Auto` modificateur dirige Visual Basic pour marshal strings selon `name`les `aliasname` règles du cadre .NET basées sur la référence externe , ou si spécifié. La valeur par défaut est `Ansi`.

  `charsetmodifier`précise également comment Visual Basic devrait rechercher la procédure externe dans son fichier externe. `Ansi`et `Unicode` les deux directes Visual Basic pour le chercher sans modifier son nom lors de la recherche. `Auto`dirige Visual Basic pour déterminer l’ensemble de caractère de base de la plate-forme de temps d’exécution et éventuellement modifier le nom de la procédure externe, comme suit :

  - Sur une plate-forme ANSI, comme Windows 95, Windows 98 ou Windows Millennium Edition, recherchez d’abord la procédure externe sans modification de nom. Si cela échoue, ajouter "A" à la fin du nom de la procédure externe et le chercher à nouveau.

  - Sur une plate-forme Unicode, comme Windows NT, Windows 2000 ou Windows XP, recherchez d’abord la procédure externe sans modification de nom. Si cela échoue, ajouter "W" à la fin du nom de procédure externe et le chercher à nouveau.

- **Mécanisme.** Visual Basic utilise le mécanisme de plate-forme cadre .NET *invoquer* (PInvoke) pour résoudre et accéder aux procédures externes. L’instruction `Declare` <xref:System.Runtime.InteropServices.DllImportAttribute> et la classe utilisent ce mécanisme automatiquement, et vous n’avez pas besoin de connaissance de PInvoke. Pour plus d’informations, voir [Procédure pas à pas : Appeler les API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Si la procédure externe s’exécute en dehors de l’heure courante (CLR), c’est *du code non géré*. Lorsque vous appelez une telle procédure, par exemple une fonction aPI Windows ou une méthode COM, vous pouvez exposer votre application à des risques de sécurité. Pour plus d’informations, voir [Secure Coding Guidelines for Unmanaged Code](https://docs.microsoft.com/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code).

## <a name="example"></a>Exemple

L’exemple suivant déclare une `Function` référence externe à une procédure qui renvoie le nom d’utilisateur actuel. Il appelle ensuite `GetUserNameA` la procédure `getUser` externe dans le cadre de la procédure.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Exemple

Le <xref:System.Runtime.InteropServices.DllImportAttribute> fournit une autre façon d’utiliser les fonctions dans le code non gestion. L’exemple suivant déclare une fonction `Declare` importée sans utiliser de relevé.

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
- [Procédure pas à pas : appel des API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
