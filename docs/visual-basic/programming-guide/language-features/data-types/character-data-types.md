---
title: Types de données caractères (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: d29e8771d61c04cf35aa71b5ba7fbba0d308c730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965675"
---
# <a name="character-data-types-visual-basic"></a>Types de données caractères (Visual Basic)
Visual Basic fournit des *types de données caractères* pour gérer les caractères imprimables et affichables. Bien qu’ils traitent tous deux des `Char` caractères Unicode, contient un `String` caractère unique, tandis que contient un nombre indéfini de caractères.  
  
 Pour obtenir une table qui affiche une comparaison côte à côte des types de données Visual Basic, consultez [types de données](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Char, type  
 Le `Char` type de données est un caractère Unicode codé sur deux octets (16 bits). Si une variable stocke toujours un caractère exactement, déclarez `Char`-la comme. Par exemple :  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Chaque valeur possible dans une `Char` variable `String` ou est un *point de code*, ou code de caractère, dans le jeu de caractères Unicode. Les caractères Unicode incluent le jeu de caractères ASCII de base, les autres lettres de l’alphabet, les accents, les symboles monétaires, les fractions, les signes diacritiques et les symboles mathématiques et techniques.  
  
> [!NOTE]
> Le jeu de caractères Unicode réserve les points de code D800 à DFFF (55296 à 55551 décimal) pour les *paires de substitution*, qui requièrent des valeurs de 2 16 bits pour représenter un point de code unique. Une `Char` variable ne peut pas contenir une paire de substitution `String` et un utilise deux positions pour contenir une telle paire.  
  
 Pour plus d’informations, consultez [type de données char](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Type de chaîne  
 Le `String` type de données est une séquence de zéro, un ou plusieurs caractères Unicode (16 bits) de 2 octets. Si une variable peut contenir un nombre indéfini de caractères, déclarez- `String`la comme. Par exemple :  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Pour plus d’informations, consultez [type de données String](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Voir aussi

- [Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Conversions de type dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
