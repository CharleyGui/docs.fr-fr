---
title: Error, instruction
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
ms.openlocfilehash: 35ba1f19654d1d23ac1ec73564bc36b0af4f6777
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404743"
---
# <a name="error-statement"></a>Error, instruction
Simule l’occurrence d’une erreur.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a>Éléments  
 `errornumber`  
 Obligatoire. Peut être n’importe quel numéro d’erreur valide.  
  
## <a name="remarks"></a>Notes  
 L' `Error` instruction est prise en charge pour la compatibilité descendante. Dans le nouveau code, en particulier lors de la création d’objets, utilisez la `Err` méthode de l’objet `Raise` pour générer des erreurs au moment de l’exécution.  
  
 Si `errornumber` est défini, l' `Error` instruction appelle le gestionnaire d’erreurs après que les propriétés de l' `Err` objet reçoivent les valeurs par défaut suivantes :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|`Number`|Valeur spécifiée comme argument de l' `Error` instruction. Peut être n’importe quel numéro d’erreur valide.|  
|`Source`|Nom du projet de Visual Basic actif.|  
|`Description`|Expression de chaîne correspondant à la valeur de retour de la `Error` fonction pour le spécifié `Number` , si cette chaîne existe. Si la chaîne n’existe pas, `Description` contient une chaîne de longueur nulle ("").|  
|`HelpFile`|Le lecteur complet, le chemin d’accès et le nom de fichier du fichier d’aide Visual Basic approprié.|  
|`HelpContext`|L’ID de contexte du fichier d’aide de Visual Basic approprié pour l’erreur correspondant à la `Number` propriété.|  
|`LastDLLError`|Zéro.|  
  
 Si aucun gestionnaire d’erreurs n’existe ou si aucun n’est activé, un message d’erreur est créé et affiché à partir des propriétés de l' `Err` objet.  
  
> [!NOTE]
> Certaines applications hôtes Visual Basic ne peuvent pas créer d’objets. Consultez la documentation de votre application hôte pour déterminer si elle peut créer des classes et des objets.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise l' `Error` instruction pour générer le numéro d’erreur 11.  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a>Spécifications  
 **Espace de noms :** [Microsoft. VisualBasic](../runtime-library-members.md)  
  
 **Assembly :** Visual Basic bibliothèque Runtime (dans Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [On Error (instruction)](on-error-statement.md)
- [Resume, instruction](resume-statement.md)
- [Messages d’erreur](../error-messages/index.md)
