---
title: Stop, instruction (Visual Basic)
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
ms.openlocfilehash: a617038ec51d98c62b6cf7e3c124c8af01305bac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957618"
---
# <a name="stop-statement-visual-basic"></a>Stop, instruction (Visual Basic)
Interrompt l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez placer `Stop` des instructions n’importe où dans les procédures pour interrompre l’exécution. L’utilisation `Stop` de l’instruction revient à définir un point d’arrêt dans le code.  
  
 L' `Stop` instruction interrompt l’exécution, mais `End`contrairement à, elle ne ferme pas les fichiers ou n’efface aucune variable, sauf si elle est rencontrée dans un fichier exécutable (. exe) compilé.  
  
> [!NOTE]
> Si l' `Stop` instruction est rencontrée dans le code qui s’exécute en dehors de l’environnement de développement intégré (IDE), le débogueur est appelé. Cela est vrai que le code ait été compilé en mode de débogage ou de vente au détail.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `Stop` l’instruction pour suspendre l’exécution de chaque itération `For...Next` à travers la boucle.  
  
 [!code-vb[VbVbalrStatements#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#56)]  
  
## <a name="see-also"></a>Voir aussi

- [End (instruction)](../../../visual-basic/language-reference/statements/end-statement.md)
