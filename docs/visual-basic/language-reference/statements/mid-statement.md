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
ms.openlocfilehash: 212ce1f06a01c39acbce43d8d069dae3526b1b4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963550"
---
# <a name="mid-statement"></a>Mid, instruction
Remplace un nombre spécifié de caractères dans une `String` variable par des caractères d’une autre chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Composants  
 `Target`  
 Requis. Nom de la `String` variable à modifier.  
  
 `Start`  
 Requis. `Integer`formule. Position du caractère `Target` dans où commence le remplacement de texte. `Start`utilise un index de base un.  
  
 `Length`  
 facultatif. `Integer`formule. Nombre de caractères à remplacer. En cas d' `String` omission, All est utilisé.  
  
 `StringExpression`  
 Requis. `String`expression qui remplace une partie `Target`de.  
  
## <a name="exceptions"></a>Exceptions  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`< = 0 ou `Length` < 0.|  
  
## <a name="remarks"></a>Notes  
 Le nombre de caractères remplacés est toujours inférieur ou égal au nombre de caractères dans `Target`.  
  
 Visual Basic a une <xref:Microsoft.VisualBasic.Strings.Mid%2A> fonction et une `Mid` instruction. Ces éléments agissent tous deux sur un nombre spécifié de caractères dans une chaîne, mais `Mid` la fonction retourne les caractères lorsque `Mid` l’instruction remplace les caractères. Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> L' `MidB` instruction des versions antérieures de Visual Basic remplace une sous-chaîne en octets plutôt que des caractères. Il est principalement utilisé pour convertir des chaînes dans des applications DBCS (Double-Byte Character Set). Toutes les chaînes Visual Basic sont au format Unicode `MidB` et ne sont plus prises en charge.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l' `Mid` instruction pour remplacer un nombre spécifié de caractères dans une variable String par des caractères d’une autre chaîne.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Configuration requise  
 **Espace de noms :** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Module:** `Strings`  
  
 **Chargeur** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Chaînes](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Introduction aux chaînes en Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
