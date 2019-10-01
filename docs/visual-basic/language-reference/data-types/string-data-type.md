---
title: String, type de données (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 6d2fd226735622de5cd7197060c05b8ac12b69f1
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696845"
---
# <a name="string-data-type-visual-basic"></a>String, type de données (Visual Basic)
Contient des séquences de points de code non signés 16 bits (2 octets) dont la valeur est comprise entre 0 et 65535. Chaque *point de code*, ou code de caractère, représente un caractère Unicode unique. Une chaîne peut contenir de 0 à environ 2 milliards (2 ^ 31) caractères Unicode.  
  
## <a name="remarks"></a>Notes  
 Utilisez le type de données `String` pour contenir plusieurs caractères sans la surcharge de gestion de tableau de `Char()`, un tableau d’éléments `Char`.  
  
 La valeur par défaut de `String` est `Nothing` (une référence null). Notez que ce n’est pas la même chose que la chaîne vide (valeur `""`).  
  
## <a name="unicode-characters"></a>Caractères Unicode  
 Les premiers points de code 128 (0 à 127) d’Unicode correspondent aux lettres et aux symboles sur un clavier américain standard. Ces premiers points de code 128 sont les mêmes que ceux définis par le jeu de caractères ASCII. Le deuxième point de code 128 (128 à 255) représente des caractères spéciaux, tels que des lettres alphabetées latines, des accents, des symboles monétaires et des fractions. Unicode utilise les points de code restants (256-65535) pour un large éventail de symboles. Cela comprend les caractères textuels mondiaux, les signes diacritiques et les symboles mathématiques et techniques.  
  
 Vous pouvez utiliser des méthodes telles que <xref:System.Char.IsDigit%2A> et <xref:System.Char.IsPunctuation%2A> sur un caractère individuel dans une variable `String` pour déterminer sa classification Unicode.  
  
## <a name="format-requirements"></a>Exigences relatives au format  
 Vous devez placer un littéral `String` entre guillemets (`" "`). Si vous devez inclure un guillemet comme l’un des caractères de la chaîne, vous utilisez deux guillemets contigus (`""`). L'exemple suivant illustre ce comportement.  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Notez que les guillemets contigus qui représentent un guillemet dans la chaîne sont indépendants des guillemets qui commencent et terminent le littéral `String`.  
  
## <a name="string-manipulations"></a>Manipulations de chaînes  
 Une fois que vous attribuez une chaîne à une variable `String`, cette chaîne est *immuable*, ce qui signifie que vous ne pouvez pas modifier sa longueur ou son contenu. Lorsque vous modifiez une chaîne de quelque façon que ce soit, Visual Basic crée une chaîne et abandonne celle qui la précède. La variable `String` pointe ensuite vers la nouvelle chaîne.  
  
 Vous pouvez manipuler le contenu d’une variable `String` à l’aide d’une variété de fonctions de chaîne. L’exemple suivant illustre la fonction <xref:Microsoft.VisualBasic.Strings.Left%2A>.  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Une chaîne créée par un autre composant peut être remplie avec des espaces de début ou de fin. Si vous recevez une telle chaîne, vous pouvez utiliser les fonctions <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A> et <xref:Microsoft.VisualBasic.Strings.RTrim%2A> pour supprimer ces espaces.  
  
 Pour plus d’informations sur les manipulations de chaînes, consultez [chaînes](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Conseils de programmation  
  
- **Nombres négatifs.** N’oubliez pas que les caractères détenus par `String` ne sont pas signés et ne peuvent pas représenter des valeurs négatives. Dans tous les cas, vous ne devez pas utiliser `String` pour contenir des valeurs numériques.  
  
- **Considérations relatives à l’interopérabilité.** Si vous utilisez des composants non écrits pour le .NET Framework, par exemple des objets Automation ou COM, n’oubliez pas que les caractères de chaîne ont une largeur de données différente (8 bits) dans d’autres environnements. Si vous transmettez un argument de chaîne de caractères 8 bits à un tel composant, déclarez-le comme `Byte()`, un tableau d’éléments `Byte`, au lieu de `String` dans votre nouveau code Visual Basic.  
  
- **Caractères de type.** L’ajout du caractère de type d’identificateur `$` à n’importe quel identificateur force ce dernier en type de données `String`. `String` n’a pas de caractère de type littéral. Toutefois, le compilateur traite les littéraux entre guillemets (`" "`) en tant que `String`.  
  
- **Type de Framework.** Le type correspondant dans le .NET Framework est la classe <xref:System.String?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.String?displayProperty=nameWithType>
- [Types de données](../../../visual-basic/language-reference/data-types/index.md)
- [Char (type de données)](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Liste des conversions](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Guide pratique pour appeler une fonction Windows qui possède des types non signés](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Utilisation efficace des types de données](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
