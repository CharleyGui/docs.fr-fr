---
title: Char, type de données (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: ca40e6c8dcba3da29bdb68b29c91c852e477f8f7
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512788"
---
# <a name="char-data-type-visual-basic"></a>Char, type de données (Visual Basic)

Contient des points de code non signés de 16 bits (2 octets) dont la valeur est comprise entre 0 et 65535. Chaque *point de code*, ou code de caractère, représente un caractère Unicode unique.

## <a name="remarks"></a>Notes

Utilisez le `Char` type de données lorsque vous ne devez contenir qu’un seul caractère et que vous n’avez pas `String`besoin de la surcharge de. Dans certains cas, vous pouvez `Char()`utiliser, un tableau `Char` d’éléments, pour contenir plusieurs caractères.

La valeur par défaut `Char` de est le caractère avec un point de code de 0.

## <a name="unicode-characters"></a>Caractères Unicode

Les premiers points de code 128 (0 à 127) d’Unicode correspondent aux lettres et aux symboles sur un clavier américain standard. Ces premiers points de code 128 sont les mêmes que ceux définis par le jeu de caractères ASCII. Le deuxième point de code 128 (128 à 255) représente des caractères spéciaux, tels que des lettres alphabetées latines, des accents, des symboles monétaires et des fractions. Unicode utilise les points de code restants (256-65535) pour un large éventail de symboles, y compris les caractères textuels mondiaux, les signes diacritiques et les symboles mathématiques et techniques.

Vous pouvez utiliser des méthodes <xref:System.Char.IsDigit%2A> telles <xref:System.Char.IsPunctuation%2A> que et `Char` sur une variable pour déterminer sa classification Unicode.

## <a name="type-conversions"></a>Conversions de type

Visual Basic n’effectue pas de conversion `Char` directe entre et les types numériques. Vous pouvez utiliser la <xref:Microsoft.VisualBasic.Strings.Asc%2A> fonction <xref:Microsoft.VisualBasic.Strings.AscW%2A> ou pour `Integer` convertir une `Char` valeur en qui représente son point de code. Vous pouvez utiliser la <xref:Microsoft.VisualBasic.Strings.Chr%2A> fonction <xref:Microsoft.VisualBasic.Strings.ChrW%2A> ou pour `Char` convertir une `Integer` valeur en qui a ce point de code.

Si le commutateur de vérification de type ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) est activé, vous devez ajouter le caractère de type littéral à un littéral de chaîne à un seul caractère `Char` pour l’identifier comme type de données. L'exemple suivant illustre ce comportement.

```vb
Option Strict On
Dim charVar As Char
' The following statement attempts to convert a String literal to Char.
' Because Option Strict is On, it generates a compiler error.
charVar = "Z"
' The following statement succeeds because it specifies a Char literal.
charVar = "Z"C
```

## <a name="programming-tips"></a>Conseils de programmation

- **Nombres négatifs.** `Char`est un type non signé et ne peut pas représenter une valeur négative. Dans tous les cas, vous ne devez `Char` pas utiliser pour contenir des valeurs numériques.

- **Considérations relatives à l’interopérabilité.** Si vous interface avec des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les types de caractères ont une largeur de données différente (8 bits) dans d’autres environnements. Si vous transmettez un argument de 8 bits à un tel composant, déclarez `Byte` -le `Char` comme au lieu de dans votre nouveau Visual Basic code.

- **Étendue.** Le `Char` type de données s’étend `String`à. Cela signifie que vous pouvez `Char` convertir `String` en <xref:System.OverflowException?displayProperty=nameWithType> et ne rencontrera pas d’erreur.

- **Caractères de type.** L’ajout du caractère `C` de type littéral à un littéral de chaîne à un seul caractère force ce dernier `Char` en type de données. `Char`n’a pas de caractère de type d’identificateur.

- **Type de Framework.** Le type correspondant dans le .NET Framework est la structure <xref:System.Char?displayProperty=nameWithType>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [String (type de données)](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Guide pratique pour appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
