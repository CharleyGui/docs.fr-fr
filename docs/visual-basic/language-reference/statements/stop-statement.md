---
title: Stop, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
ms.openlocfilehash: 497c5f207b2228412411cc3eb01976564f82bd6c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346467"
---
# <a name="stop-statement-visual-basic"></a>Stop, instruction (Visual Basic)
Interrompt l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Stop  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez placer `Stop` instructions n’importe où dans les procédures pour interrompre l’exécution. L’utilisation de l’instruction `Stop` est semblable à la définition d’un point d’arrêt dans le code.  
  
 L’instruction `Stop` interrompt l’exécution, mais contrairement à `End`, elle ne ferme pas les fichiers ou n’efface aucune variable, sauf si elle est rencontrée dans un fichier exécutable (. exe) compilé.  
  
> [!NOTE]
> Si l’instruction `Stop` est rencontrée dans le code qui s’exécute en dehors de l’environnement de développement intégré (IDE), le débogueur est appelé. Cela est vrai que le code ait été compilé en mode de débogage ou de vente au détail.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `Stop` pour interrompre l’exécution de chaque itération via la boucle `For...Next`.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Voir aussi

- [End (instruction)](../../../visual-basic/language-reference/statements/end-statement.md)
