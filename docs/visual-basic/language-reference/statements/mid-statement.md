---
title: Mid, instruction
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
ms.openlocfilehash: 90408fd8a8cfc9b74c8422d0571d61f8534403f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404449"
---
# <a name="mid-statement"></a>Mid, instruction
Remplace un nombre spécifié de caractères dans une `String` variable par des caractères d’une autre chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>Éléments  
 `Target`  
 Obligatoire. Nom de la `String` variable à modifier.  
  
 `Start`  
 Obligatoire. Expression `Integer`. Position du caractère dans `Target` où commence le remplacement de texte. `Start`utilise un index de base un.  
  
 `Length`  
 Facultatif. Expression `Integer`. Nombre de caractères à remplacer. En cas d’omission, All `String` est utilisé.  
  
 `StringExpression`  
 Obligatoire. `String`expression qui remplace une partie de `Target` .  
  
## <a name="exceptions"></a>Exceptions  
  
|Type d'exception|Condition|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start`<= 0 ou `Length` < 0.|  
  
## <a name="remarks"></a>Notes  
 Le nombre de caractères remplacés est toujours inférieur ou égal au nombre de caractères dans `Target` .  
  
 Visual Basic a une <xref:Microsoft.VisualBasic.Strings.Mid%2A> fonction et une `Mid` instruction. Ces éléments agissent tous deux sur un nombre spécifié de caractères dans une chaîne, mais la `Mid` fonction retourne les caractères lorsque l' `Mid` instruction remplace les caractères. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Strings.Mid%2A>.  
  
> [!NOTE]
> L' `MidB` instruction des versions antérieures de Visual Basic remplace une sous-chaîne en octets plutôt que des caractères. Il est principalement utilisé pour convertir des chaînes dans des applications DBCS (Double-Byte Character Set). Toutes les chaînes Visual Basic sont au format Unicode et ne `MidB` sont plus prises en charge.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise l' `Mid` instruction pour remplacer un nombre spécifié de caractères dans une variable String par des caractères d’une autre chaîne.  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Module :**`Strings`  
  
 **Assembly :** Visual Basic bibliothèque Runtime (dans Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [Chaînes](../../programming-guide/language-features/strings/index.md)
- [Introduction aux chaînes en Visual Basic](../../programming-guide/language-features/strings/introduction-to-strings.md)
