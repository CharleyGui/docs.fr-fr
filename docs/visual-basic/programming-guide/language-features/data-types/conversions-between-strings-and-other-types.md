---
title: Conversion entre des chaînes et d'autres types
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: ac2e8ce912080c284d8ba0228830dd6b3ddf5f6e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350135"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>Conversion entre des chaînes et d'autres types (Visual Basic)
Vous pouvez convertir une valeur numérique, `Boolean`ou de date/heure en `String`. Vous pouvez également convertir le sens inverse, d’une valeur de chaîne en numeric, `Boolean`ou `Date`, à condition que le contenu de la chaîne puisse être interprété comme une valeur valide du type de données de destination. Si ce n’est pas le cas, une erreur d’exécution se produit.  
  
 Les conversions pour toutes ces assignations, dans les deux sens, sont des conversions restrictives. Vous devez utiliser les mots clés de conversion de type (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`et `CType`). Les fonctions <xref:Microsoft.VisualBasic.Strings.Format%2A> et <xref:Microsoft.VisualBasic.Conversion.Val%2A> vous offrent un contrôle supplémentaire sur les conversions entre les chaînes et les nombres.  
  
 Si vous avez défini une classe ou une structure, vous pouvez définir des opérateurs de conversion de type entre `String` et le type de votre classe ou structure. Pour plus d'informations, consultez [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="conversion-of-numbers-to-strings"></a>Conversion de nombres en chaînes  
 Vous pouvez utiliser la fonction `Format` pour convertir un nombre en une chaîne mise en forme, ce qui peut inclure non seulement les chiffres appropriés, mais également la mise en forme des symboles tels qu’un signe monétaire (comme `$`), des séparateurs de milliers ou des *symboles de groupement de chiffres* (tels que `,`) et un séparateur décimal (par exemple, `.`). `Format` utilise automatiquement les symboles appropriés en fonction des paramètres **régionaux** spécifiés dans le **panneau**de configuration Windows.  
  
 Notez que l’opérateur de concaténation (`&`) peut convertir un nombre en chaîne implicitement, comme le montre l’exemple suivant.  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>Conversion de chaînes en nombres  
 Vous pouvez utiliser la fonction `Val` pour convertir explicitement les chiffres d’une chaîne en nombre. `Val` lit la chaîne jusqu’à ce qu’elle rencontre un caractère autre qu’un chiffre, un espace, une tabulation, un saut de ligne ou un point. Les séquences « & O » et « & H » modifient la base du système de nombres et terminent l’analyse. Jusqu’à ce qu’il arrête de lire, `Val` convertit tous les caractères appropriés en une valeur numérique. Par exemple, l’instruction suivante retourne la valeur `141.825`.  
  
 `Val("   14   1.825 miles")`  
  
 Lorsque Visual Basic convertit une chaîne en une valeur numérique, elle utilise les paramètres **régionaux** spécifiés dans le **panneau de configuration** Windows pour interpréter le séparateur des milliers, le séparateur décimal et le symbole monétaire. Cela signifie qu’une conversion peut échouer sous un seul paramètre, mais pas dans un autre. Par exemple, `"$14.20"` est acceptable dans les paramètres régionaux anglais (États-Unis), mais pas dans les paramètres régionaux français.  
  
## <a name="see-also"></a>Voir aussi

- [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Conversions implicites et explicites](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Comment : convertir un objet en un autre type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Conversions de tableau](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Types de données](../../../../visual-basic/language-reference/data-types/index.md)
- [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Développer des applications mondialisées et localisées](/visualstudio/ide/globalizing-and-localizing-applications)
