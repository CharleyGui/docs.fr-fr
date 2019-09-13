---
title: _EFN_StackTrace, fonction
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9035d9a53c4b0c8822b79e641aef092b4a48c418
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895036"
---
# <a name="_efn_stacktrace-function"></a>\_EFN\_fonction StackTrace
Fournit une représentation textuelle d'une trace de pile managée et un tableau d'enregistrements `CONTEXT` pour chaque transition entre du code non managé et du code managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `Client`  
 dans Client en cours de débogage.  
  
 `wszTextOut`  
 à Représentation textuelle de la trace de la pile.  
  
 `puiTextLength`  
 à Pointeur vers le nombre de caractères dans `wszTextOut`.  
  
 `pTransitionContexts`  
 à Tableau de contextes de transition.  
  
 `puiTransitionContextCount`  
 à Pointeur vers le nombre de contextes de transition dans le tableau.  
  
 `uiSizeOfContext`  
 dans Taille de la structure de contexte.  
  
 `Flags`  
 dans Définissez sur 0 ou SOS_STACKTRACE_SHOWADDRESSES (0x01) pour afficher le registre EBP et le pointeur de pile Enter (ESP) devant chaque `module!functionname` ligne.  
  
## <a name="remarks"></a>Notes  
 La `_EFN_StackTrace` structure peut être appelée à partir d’une interface de programmation WinDbg. Les paramètres sont utilisés comme suit :  
  
- Si `wszTextOut` a la valeur `puiTextLength` null et que n’est pas null, la fonction retourne `puiTextLength`la longueur de la chaîne dans.  
  
- Si `wszTextOut` n’a pas la valeur null, la fonction `wszTextOut` stocke le texte dans l' `puiTextLength`emplacement indiqué par. Elle retourne avec succès si la mémoire tampon a suffisamment d’espace, ou retourne E_OUTOFMEMORY si la mémoire tampon n’était pas suffisamment longue.  
  
- La partie transition de la fonction est ignorée `pTransitionContexts` si `puiTransitionContextCount` et sont tous deux null. Dans ce cas, la fonction fournit aux appelants une sortie texte uniquement des noms de fonctions.  
  
- Si `pTransitionContexts` a la valeur `puiTransitionContextCount` null et que n’est pas null, la fonction retourne le nombre nécessaire `puiTransitionContextCount`d’entrées de contexte dans.  
  
- Si `pTransitionContexts` n’a pas la valeur null, la fonction la traite comme un tableau de `puiTransitionContextCount`structures de longueur. La taille de la structure est `uiSizeOfContext`donnée par, et doit être la taille de `CONTEXT` [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) ou de l’architecture.  
  
- `wszTextOut`est écrit au format suivant :  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Si le décalage dans hex est 0x0, aucun décalage n’est écrit.  
  
- S’il n’existe aucun code managé sur le thread actuellement en contexte, la fonction retourne SOS_E_NOMANAGEDCODE.  
  
- Le `Flags` paramètre est 0 ou SOS_STACKTRACE_SHOWADDRESSES pour voir EBP et ESP devant chaque `module!functionname` ligne. Par défaut, il est égal à 0.  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** SOS_Stacktrace. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
