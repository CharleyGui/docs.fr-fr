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
ms.openlocfilehash: c7b2adfe7f6b6ff5e89598cb318a90c51595ff6f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583377"
---
# <a name="error-statement"></a>Error, instruction
Simule l’occurrence d’une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>Composants  
 `errornumber`  
 Requis. Peut être n’importe quel numéro d’erreur valide.  
  
## <a name="remarks"></a>Notes  
 L’instruction `Error` est prise en charge pour la compatibilité descendante. Dans le nouveau code, en particulier lors de la création d’objets, utilisez la méthode `Raise` de l’objet `Err` pour générer des erreurs d’exécution.  
  
 Si `errornumber` est défini, l’instruction `Error` appelle le gestionnaire d’erreurs après que les propriétés de l’objet `Err` reçoivent les valeurs par défaut suivantes :  
  
|Property|valeur|  
|--------------|-----------|  
|`Number`|Valeur spécifiée comme argument pour `Error` instruction. Peut être n’importe quel numéro d’erreur valide.|  
|`Source`|Nom du projet de Visual Basic actif.|  
|`Description`|Expression de chaîne correspondant à la valeur de retour de la fonction `Error` pour le `Number` spécifié, si cette chaîne existe. Si la chaîne n’existe pas, `Description` contient une chaîne de longueur nulle ("").|  
|`HelpFile`|Le lecteur complet, le chemin d’accès et le nom de fichier du fichier d’aide Visual Basic approprié.|  
|`HelpContext`|L’ID de contexte du fichier d’aide Visual Basic approprié pour l’erreur correspondant à la propriété `Number`.|  
|`LastDLLError`|Nuls.|  
  
 Si aucun gestionnaire d’erreurs n’existe ou si aucun n’est activé, un message d’erreur est créé et affiché à partir des propriétés de l’objet `Err`.  
  
> [!NOTE]
> Certaines applications hôtes Visual Basic ne peuvent pas créer d’objets. Consultez la documentation de votre application hôte pour déterminer si elle peut créer des classes et des objets.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l’instruction `Error` pour générer le numéro d’erreur 11.  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>spécifications  
 **Espace de noms :** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly :** Visual Basic bibliothèque Runtime (dans Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error (instruction)](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [Resume (instruction)](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Messages d’erreur](../../../visual-basic/language-reference/error-messages/index.md)
