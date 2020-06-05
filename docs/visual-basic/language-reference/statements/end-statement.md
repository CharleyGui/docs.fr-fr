---
title: End, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: fe17a82662c4014069c77f2da76723a051ab9084
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404704"
---
# <a name="end-statement"></a>End, instruction
Termine immédiatement l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
End  
```  
  
## <a name="remarks"></a>Notes  
 Vous pouvez placer l' `End` instruction n’importe où dans une procédure pour forcer l’arrêt de l’exécution de l’application entière. `End`ferme tous les fichiers ouverts avec une `Open` instruction et efface toutes les variables de l’application. L’application se ferme dès qu’aucun autre programme ne contient des références à ses objets et qu’aucun de son code n’est en cours d’exécution.  
  
> [!NOTE]
> L' `End` instruction arrête l’exécution du code brusquement et n’appelle pas `Dispose` la `Finalize` méthode ou, ni tout autre Visual Basic de code. Les références d’objets détenues par d’autres programmes sont invalidées. Si une `End` instruction est rencontrée dans `Try` un `Catch` bloc ou, le contrôle ne passe pas au `Finally` bloc correspondant.  
  
 L' `Stop` instruction interrompt l’exécution, mais contrairement `End` à, elle ne ferme pas les fichiers ou n’efface aucune variable, sauf si elle est rencontrée dans un fichier exécutable (. exe) compilé.  
  
 Étant donné que `End` met fin à votre application sans vous préoccuper des ressources qui peuvent être ouvertes, vous devez essayer de la fermer correctement avant de l’utiliser. Par exemple, si des formulaires sont ouverts sur votre application, vous devez les fermer avant que le contrôle n’atteigne l' `End` instruction.  
  
 Vous devez utiliser `End` avec modération et uniquement lorsque vous devez arrêter immédiatement. Les méthodes normales pour mettre fin à une procédure ([instruction de retour](return-statement.md) et [instruction de sortie](exit-statement.md)) ferment uniquement la procédure proprement dit, mais elles permettent également au code appelant de fermer correctement. Une application console, par exemple, peut simplement être `Return` à partir de la `Main` procédure.  
  
> [!IMPORTANT]
> L' `End` instruction appelle la <xref:System.Environment.Exit%2A> méthode de la <xref:System.Environment> classe dans l' <xref:System> espace de noms. <xref:System.Environment.Exit%2A>requiert que vous disposiez d’une `UnmanagedCode` autorisation. Si vous ne le faites pas, une <xref:System.Security.SecurityException> erreur se produit.  
  
 Lorsqu’il est suivi d’un mot clé supplémentaire, [End \<keyword> Statement](end-keyword-statement.md) délimite la fin de la définition de la procédure ou du bloc approprié. Par exemple, `End Function` termine la définition d’une `Function` procédure.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `End` instruction pour mettre fin à l’exécution du code si l’utilisateur le demande.  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a>Notes de développement Smart Device  
 Cette instruction n'est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [Stop (instruction)](stop-statement.md)
- [End ( \<keyword> instruction)](end-keyword-statement.md)
