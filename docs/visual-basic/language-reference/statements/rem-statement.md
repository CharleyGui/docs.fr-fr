---
title: REM, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: 16149ce42e3476cf07a62298f83734fee9ec7253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957762"
---
# <a name="rem-statement-visual-basic"></a>REM, instruction (Visual Basic)
Utilisé pour inclure des remarques explicatives dans le code source d’un programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Composants  
 `comment`  
 facultatif. Texte de tous les commentaires que vous souhaitez inclure. Un espace est requis entre le `REM` mot clé `comment`et.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez placer une `REM` instruction seule sur une ligne, ou vous pouvez la placer sur une ligne après une autre instruction. L' `REM` instruction doit être la dernière instruction de la ligne. S’il suit une autre instruction, `REM` le doit être séparé de cette instruction par un espace.  
  
 Vous pouvez utiliser un guillemet simple (`'`) à la place de. `REM` Cela est vrai si votre commentaire suit une autre instruction sur la même ligne ou s’il se trouve seul sur une ligne.  
  
> [!NOTE]
> Vous ne pouvez pas `REM` continuer une instruction à l’aide d’une séquence`_`de continuation de ligne (). Une fois qu’un commentaire commence, le compilateur n’examine pas les caractères pour une signification particulière. Pour un commentaire de plusieurs lignes, utilisez une `REM` autre instruction ou un symbole de`'`commentaire () sur chaque ligne.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l' `REM` instruction, qui est utilisée pour inclure des remarques explicatives dans un programme. Elle illustre également l’utilisation du caractère guillemet simple (`'`) au lieu de. `REM`  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Commentaires dans le code](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Guide pratique pour diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
