---
title: 'Comment : appeler une procédure surchargée'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: d983f5f6183c33141079ed35171f7a73f254450f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340207"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a>Comment : appeler une procédure surchargée (Visual Basic)
L’avantage de la surcharge d’une procédure est de la flexibilité de l’appel. Le code appelant peut obtenir les informations qu’il doit passer à la procédure, puis appeler un nom de procédure unique, quels que soient les arguments transmis.  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a>Pour appeler une procédure qui a plusieurs versions définies  
  
1. Dans le code appelant, déterminez les données à passer à la procédure.  
  
2. Écrivez l’appel de procédure de manière normale, en présentant les données dans la liste d’arguments. Veillez à ce que les arguments correspondent à la liste de paramètres dans l’une des versions définies pour la procédure.  
  
3. Vous n’avez pas besoin de déterminer la version de la procédure à appeler. Visual Basic passe le contrôle à la version correspondant à votre liste d’arguments.  
  
     L’exemple suivant appelle la procédure `post` déclarée dans [Comment : définir plusieurs versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md). Il obtient l’identification du client, détermine s’il s’agit d’un `String` ou d’un `Integer`, puis, dans les deux cas, appelle la même procédure.  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures](./index.md)
- [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)
- [Surcharge de procédure](./procedure-overloading.md)
- [Procédures de dépannage](./troubleshooting-procedures.md)
- [Guide pratique : définir plusieurs versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md)
- [Guide pratique : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Guide pratique : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md)
- [Résolution de surcharge](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
