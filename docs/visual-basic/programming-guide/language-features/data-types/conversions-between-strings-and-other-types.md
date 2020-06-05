---
title: Conversions entre des chaînes et d’autres types
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: ae8f7c2159191536013fafd8bfd10fb9a93fb785
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394219"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Conversion entre des chaînes et d'autres types (Visual Basic)
Vous pouvez convertir une valeur numérique, `Boolean` ou de date/heure en `String` . Vous pouvez également convertir dans le sens inverse (à partir d’une valeur de chaîne en numeric, `Boolean` ou), à `Date` condition que le contenu de la chaîne puisse être interprété comme une valeur valide du type de données de destination. Si ce n’est pas le cas, une erreur d’exécution se produit.  
  
 Les conversions pour toutes ces assignations, dans les deux sens, sont des conversions restrictives. Vous devez utiliser les mots clés de conversion de type ( `CBool` , `CByte` , `CDate` , `CDbl` , `CDec` , `CInt` , `CLng` , `CSByte` , `CShort` , `CSng` , `CStr` , `CUInt` , `CULng` , `CUShort` et `CType` ). Les <xref:Microsoft.VisualBasic.Strings.Format%2A> <xref:Microsoft.VisualBasic.Conversion.Val%2A> fonctions et vous offrent un contrôle supplémentaire sur les conversions entre les chaînes et les nombres.  
  
 Si vous avez défini une classe ou une structure, vous pouvez définir des opérateurs de conversion de type entre `String` et le type de votre classe ou structure. Pour plus d'informations, consultez [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Conversion de nombres en chaînes  
 Vous pouvez utiliser la `Format` fonction pour convertir un nombre en chaîne mise en forme, qui peut inclure non seulement les chiffres appropriés, mais également mettre en forme les symboles tels que les symboles monétaires (tels que `$` ), les séparateurs de milliers ou les *symboles de groupement de chiffres* (tels que) `,` et un séparateur décimal (tel que `.` ). `Format`utilise automatiquement les symboles appropriés en fonction des paramètres **régionaux** spécifiés dans le **panneau**de configuration Windows.  
  
 Notez que l’opérateur de concaténation ( `&` ) peut convertir un nombre en chaîne implicitement, comme le montre l’exemple suivant.  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Conversion de chaînes en nombres  
 Vous pouvez utiliser la `Val` fonction pour convertir explicitement les chiffres d’une chaîne en nombre. `Val`lit la chaîne jusqu’à ce qu’elle rencontre un caractère autre qu’un chiffre, un espace, une tabulation, un saut de ligne ou un point. Les séquences « &O » et « &H » modifient la base du système de nombres et terminent l’analyse. Jusqu’à ce qu’il arrête de lire, `Val` convertit tous les caractères appropriés en une valeur numérique. Par exemple, l’instruction suivante retourne la valeur `141.825` .  
  
 `Val("   14   1.825 miles")`  
  
 Lorsque Visual Basic convertit une chaîne en une valeur numérique, elle utilise les paramètres **régionaux** spécifiés dans le **panneau de configuration** Windows pour interpréter le séparateur des milliers, le séparateur décimal et le symbole monétaire. Cela signifie qu’une conversion peut échouer sous un seul paramètre, mais pas dans un autre. Par exemple, `"$14.20"` est acceptable dans les paramètres régionaux anglais (États-Unis), mais pas dans les paramètres régionaux français.  
  
## <a name="see-also"></a>Voir aussi

- [Conversions de type en Visual Basic](type-conversions.md)
- [Widening and Narrowing Conversions](widening-and-narrowing-conversions.md)
- [Conversions implicites et explicites](implicit-and-explicit-conversions.md)
- [Comment : convertir un objet en un autre type dans Visual Basic](how-to-convert-an-object-to-another-type.md)
- [Conversions de tableau](array-conversions.md)
- [Types de données](../../../language-reference/data-types/index.md)
- [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md)
- [Développer des applications mondialisées et traduites](/visualstudio/ide/globalizing-and-localizing-applications)
