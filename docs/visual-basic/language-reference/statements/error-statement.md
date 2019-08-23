---
title: Error, instruction (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 7b926214d3be7f5f57783a8599acf1bb1042f956
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944455"
---
# <a name="error-statement"></a>Error, instruction
Simule l’occurrence d’une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a>Composants  
 `errornumber`  
 Requis. Peut être n’importe quel numéro d’erreur valide.  
  
## <a name="remarks"></a>Notes  
 L' `Error` instruction est prise en charge pour la compatibilité descendante. Dans le nouveau code, en particulier lors de la création `Err` d’objets `Raise` , utilisez la méthode de l’objet pour générer des erreurs au moment de l’exécution.  
  
 Si `errornumber` est défini, l' `Error` instruction appelle le gestionnaire d’erreurs après que les propriétés `Err` de l’objet reçoivent les valeurs par défaut suivantes:  
  
|Propriété|`Value`|  
|--------------|-----------|  
|`Number`|Valeur spécifiée comme argument de `Error` l’instruction. Peut être n’importe quel numéro d’erreur valide.|  
|`Source`|Nom du projet de Visual Basic actif.|  
|`Description`|Expression de chaîne correspondant à la valeur de retour `Error` de la fonction pour `Number`le spécifié, si cette chaîne existe. Si la chaîne n’existe pas, `Description` contient une chaîne de longueur nulle ("").|  
|`HelpFile`|Le lecteur complet, le chemin d’accès et le nom de fichier du fichier d’aide Visual Basic approprié.|  
|`HelpContext`|L’ID de contexte du fichier d’aide de Visual Basic approprié pour l' `Number` erreur correspondant à la propriété.|  
|`LastDLLError`|Nuls.|  
  
 Si aucun gestionnaire d’erreurs n’existe ou si aucun n’est activé, un message d’erreur est créé et `Err` affiché à partir des propriétés de l’objet.  
  
> [!NOTE]
> Certaines applications hôtes Visual Basic ne peuvent pas créer d’objets. Consultez la documentation de votre application hôte pour déterminer si elle peut créer des classes et des objets.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise `Error` l’instruction pour générer le numéro d’erreur 11.  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Configuration requise  
 **Espace de noms :** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Chargeur** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error (instruction)](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume (instruction)](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Messages d’erreur](../../../visual-basic/language-reference/error-messages/index.md)
