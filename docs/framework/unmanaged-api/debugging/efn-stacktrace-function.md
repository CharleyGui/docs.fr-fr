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
ms.openlocfilehash: 687fdd0735e6cb0f3a727c8a2da3cf33bffb6a39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738983"
---
# <a name="efnstacktrace-function"></a>\_EFN\_StackTrace (fonction)
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
 [in] Le client en cours de débogage.  
  
 `wszTextOut`  
 [out] La représentation textuelle de la trace de pile.  
  
 `puiTextLength`  
 [out] Un pointeur vers le nombre de caractères dans `wszTextOut`.  
  
 `pTransitionContexts`  
 [out] Le tableau de contextes de transition.  
  
 `puiTransitionContextCount`  
 [out] Pointeur vers le nombre de contextes de transition dans le tableau.  
  
 `uiSizeOfContext`  
 [in] La taille de la structure de contexte.  
  
 `Flags`  
 [in] La valeur 0 ou SOS_STACKTRACE_SHOWADDRESSES (0 x 01) pour afficher le registre EBP et le pointeur de pile d’entrée (ESP) devant chacun `module!functionname` ligne.  
  
## <a name="remarks"></a>Notes  
 Le `_EFN_StackTrace` structure peut être appelée à partir d’une interface de programmation WinDbg. Paramètres sont utilisés comme suit :  
  
- Si `wszTextOut` a la valeur null et `puiTextLength` est non null, la fonction retourne la longueur de chaîne dans `puiTextLength`.  
  
- Si `wszTextOut` est non null, la fonction stocke le texte dans `wszTextOut` jusqu'à l’emplacement indiqué par `puiTextLength`. Il retourne une valeur si il y a suffisamment d’espace dans la mémoire tampon, ou retourne E_OUTOFMEMORY si la mémoire tampon n’est pas assez long.  
  
- La partie de la transition de la fonction est ignorée si `pTransitionContexts` et `puiTransitionContextCount` sont tous deux null. Dans ce cas, la fonction fournit les appelants avec sortie texte du uniquement les noms de fonction.  
  
- Si `pTransitionContexts` a la valeur null et `puiTransitionContextCount` est non null, la fonction retourne le nombre nécessaire d’entrées de contexte dans `puiTransitionContextCount`.  
  
- Si `pTransitionContexts` est non null, la fonction traite comme un tableau de structures de longueur `puiTransitionContextCount`. La taille de la structure est fournie par `uiSizeOfContext`, et doit être la taille de [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) ou `CONTEXT` pour l’architecture.  
  
- `wszTextOut` est écrit dans le format suivant :  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Si l’offset en hexadécimal est 0 x 0, aucun offset n’est écrit.  
  
- S’il n’existe aucun code managé sur le thread actuellement dans le contexte, la fonction retourne alors SOS_E_NOMANAGEDCODE.  
  
- Le `Flags` paramètre est 0 ou SOS_STACKTRACE_SHOWADDRESSES pour voir EBP et ESP devant chaque `module!functionname` ligne. Par défaut, il est 0.  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** SOS_Stacktrace.h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
