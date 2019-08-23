---
title: 'Procédure : Fractionner et combiner des instructions dans le code (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 745974523bd747dd23f3cfaf7cb70bb6cd4513f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946211"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Procédure : Fractionner et combiner des instructions dans le code (Visual Basic)
Lors de l’écriture de votre code, vous pouvez parfois créer des instructions longues qui nécessitent un défilement horizontal dans l’éditeur de code. Bien que cela n’affecte pas la manière dont votre code s’exécute, cela complique la lecture du code tel qu’il apparaît sur le moniteur. Dans ce cas, vous devez envisager de fractionner une seule instruction longue en plusieurs lignes.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Pour scinder une seule instruction en plusieurs lignes  
  
- Utilisez le caractère de continuation de ligne, qui est un trait`_`de soulignement (), à l’endroit où vous souhaitez que la ligne s’arrête. Le trait de soulignement doit être immédiatement précédé d’un espace et immédiatement suivi d’un terminateur de ligne (retour chariot).  
  
    > [!NOTE]
    > Dans certains cas, si vous omettez le caractère de continuation de ligne, le compilateur Visual Basic continue implicitement l’instruction sur la ligne de code suivante. Pour obtenir la liste des éléments syntaxiques pour lesquels vous pouvez omettre le caractère de continuation de ligne, consultez «continuation de ligne implicite» dans les [instructions](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     Dans l’exemple suivant, l’instruction est divisée en quatre lignes avec des caractères de continuation de ligne qui terminent tous sauf la dernière ligne.  
  
     [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]  
  
     L’utilisation de cette séquence rend votre code plus facile à lire, en ligne et à l’impression.  
  
     Le caractère de continuation de ligne doit être le dernier caractère d’une ligne. Vous ne pouvez pas le suivre avec d’autres éléments sur la même ligne.  
  
     Il existe certaines limitations quant à l’emplacement où vous pouvez utiliser le caractère de continuation de ligne. par exemple, vous ne pouvez pas l’utiliser au milieu d’un nom d’argument. Vous pouvez arrêter une liste d’arguments avec le caractère de continuation de ligne, mais les noms individuels des arguments doivent rester intacts.  
  
     Vous ne pouvez pas continuer un commentaire en utilisant un caractère de continuation de ligne. Le compilateur n’examine pas les caractères d’un commentaire pour une signification particulière. Pour un commentaire de plusieurs lignes, répétez le symbole de`'`commentaire () sur chaque ligne.  
  
 Bien que la méthode recommandée consiste à placer chaque instruction sur une ligne distincte, Visual Basic vous permet également de placer plusieurs instructions sur la même ligne.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Pour placer plusieurs instructions sur la même ligne  
  
- Séparez les instructions par un signe`:`deux-points (), comme dans l’exemple suivant.  
  
     [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]  
  
## <a name="see-also"></a>Voir aussi

- [Structure de programme et conventions de codage](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Instructions](../../../visual-basic/programming-guide/language-features/statements.md)
