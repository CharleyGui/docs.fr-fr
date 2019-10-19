---
title: Instruction Mid (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: ea22af2eb896542bfc329e087101608e08c45107
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581478"
---
# <a name="mid-statement"></a>Mid, instruction
Remplace un nombre spécifié de caractères dans une variable `String` par des caractères d’une autre chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Composants  
 `Target`  
 Requis. Nom de la variable `String` à modifier.  
  
 `Start`  
 Requis. expression `Integer`. Position du caractère dans `Target` où commence le remplacement de texte. `Start` utilise un index de base un.  
  
 `Length`  
 Optionnel. expression `Integer`. Nombre de caractères à remplacer. En cas d’omission, tous les `String` sont utilisés.  
  
 `StringExpression`  
 Requis. expression `String` qui remplace une partie de `Target`.  
  
## <a name="exceptions"></a>Exceptions  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 ou `Length` < 0.|  
  
## <a name="remarks"></a>Notes  
 Le nombre de caractères remplacés est toujours inférieur ou égal au nombre de caractères dans `Target`.  
  
 Visual Basic a une fonction <xref:Microsoft.VisualBasic.Strings.Mid%2A> et une instruction `Mid`. Ces éléments agissent tous deux sur un nombre spécifié de caractères dans une chaîne, mais la fonction `Mid` retourne les caractères lorsque l’instruction `Mid` remplace les caractères. Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> L’instruction `MidB` des versions antérieures de Visual Basic remplace une sous-chaîne en octets plutôt que des caractères. Il est principalement utilisé pour convertir des chaînes dans des applications DBCS (Double-Byte Character Set). Toutes les chaînes Visual Basic sont au format Unicode et `MidB` ne sont plus prises en charge.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l’instruction `Mid` pour remplacer un nombre spécifié de caractères dans une variable String par des caractères d’une autre chaîne.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>spécifications  
 **Espace de noms :** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Module :** `Strings`  
  
 **Assembly :** Visual Basic bibliothèque Runtime (dans Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Chaînes](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Introduction aux chaînes en Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
