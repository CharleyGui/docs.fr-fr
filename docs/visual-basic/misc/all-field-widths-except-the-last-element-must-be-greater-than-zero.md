---
title: Toutes les largeurs de champs, à l’exception de celle du dernier élément, doivent être supérieures à zéro
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_FieldWidthsMustPositive
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
ms.openlocfilehash: 0e81652a0f9e97ce40851170ed050bd1f047ba5f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84412934"
---
# <a name="all-field-widths-except-the-last-element-must-be-greater-than-zero"></a>Toutes les largeurs de champs, à l’exception de celle du dernier élément, doivent être supérieures à zéro
Toutes les largeurs de champs, à l’exception de celle du dernier élément, doivent être supérieures à zéro. Une largeur de champ inférieure ou égale à zéro dans le dernier élément indique que le dernier champ a une longueur variable.  
  
 L’opération a échoué car une largeur de champ autre que celle du dernier élément a une valeur inférieure ou égale à zéro. Une largeur de champ inférieure ou égale à zéro peut être utilisée comme dernier élément pour indiquer que le dernier champ est de longueur variable, mais elle ne peut pas être utilisée comme autre élément.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
- Affectez la longueur correcte à la largeur de champ.  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths>
- [Procédure : lire des fichiers texte de largeur fixe](../developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [TextFieldParser Object](../language-reference/objects/textfieldparser-object.md)
