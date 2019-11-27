---
title: REM, instruction
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
ms.openlocfilehash: bdde4beae242c3175b02cd2af252babb850416f6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346732"
---
# <a name="rem-statement-visual-basic"></a>REM, instruction (Visual Basic)
Utilisé pour inclure des remarques explicatives dans le code source d’un programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Composants  
 `comment`  
 Ce paramètre est facultatif. Texte de tous les commentaires que vous souhaitez inclure. Un espace est requis entre le mot clé `REM` et `comment`.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez placer une instruction `REM` seule sur une ligne, ou vous pouvez la placer sur une ligne après une autre instruction. L’instruction `REM` doit être la dernière instruction de la ligne. S’il suit une autre instruction, le `REM` doit être séparé de cette instruction par un espace.  
  
 Vous pouvez utiliser un guillemet simple (`'`) au lieu de `REM`. Cela est vrai si votre commentaire suit une autre instruction sur la même ligne ou s’il se trouve seul sur une ligne.  
  
> [!NOTE]
> Vous ne pouvez pas continuer une instruction `REM` à l’aide d’une séquence de continuation de ligne (`_`). Une fois qu’un commentaire commence, le compilateur n’examine pas les caractères pour une signification particulière. Pour un commentaire sur plusieurs lignes, utilisez une autre instruction `REM` ou un symbole de commentaire (`'`) sur chaque ligne.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre l’instruction `REM`, qui est utilisée pour inclure des remarques explicatives dans un programme. Il montre également l’alternative à l’utilisation du caractère guillemet simple (`'`) au lieu de `REM`.  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Voir aussi

- [Commentaires dans le code](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [Guide pratique : diviser et combiner des instructions dans le code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
