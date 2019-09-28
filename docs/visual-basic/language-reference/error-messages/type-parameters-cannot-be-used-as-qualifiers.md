---
title: Les paramètres de type ne peuvent pas être utilisés comme qualificateurs
ms.date: 07/20/2015
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords:
- BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
ms.openlocfilehash: 88b5f365c47b98964d9f5a0d22a941d85dcfb95f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592133"
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a>Les paramètres de type ne peuvent pas être utilisés comme qualificateurs
Un élément de programmation est qualifié avec une chaîne de qualification qui comprend un paramètre de type.  
  
 Un paramètre de type représente une spécification pour un type qui doit être fourni lorsque le type générique est construit. Il ne représente pas un type défini spécifique. Une chaîne de qualification doit inclure uniquement les éléments définis au moment de la compilation.  
  
 Les instructions suivantes peuvent générer cette erreur.  
  
```vb  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **ID d’erreur :** BC32098  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Supprimez le paramètre de type de la chaîne de qualification ou remplacez-le par un type défini.  
  
2. Si vous devez utiliser un type construit pour localiser l’élément de programmation qualifié, vous devez utiliser une logique de programme supplémentaire.  
  
## <a name="see-also"></a>Voir aussi

- [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Liste de types](../../../visual-basic/language-reference/statements/type-list.md)
