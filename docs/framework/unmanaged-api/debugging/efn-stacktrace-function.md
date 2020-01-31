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
ms.openlocfilehash: cc5093a5ba0afcccaf960e9b8776f93a061cc2f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785678"
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
  
## <a name="parameters"></a>Parameters  
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
 dans Définissez sur 0 ou SOS_STACKTRACE_SHOWADDRESSES (0x01) pour afficher le registre EBP et le pointeur de pile Enter (ESP) devant chaque ligne de `module!functionname`.  
  
## <a name="remarks"></a>Notes  
 La structure `_EFN_StackTrace` peut être appelée à partir d’une interface de programmation WinDbg. Les paramètres sont utilisés comme suit :  
  
- Si `wszTextOut` a la valeur null et que `puiTextLength` n’a pas la valeur null, la fonction retourne la longueur de la chaîne dans `puiTextLength`.  
  
- Si `wszTextOut` n’a pas la valeur null, la fonction stocke le texte dans `wszTextOut` jusqu’à l’emplacement indiqué par `puiTextLength`. Elle retourne avec succès si la mémoire tampon est suffisamment grande, ou si elle retourne E_OUTOFMEMORY si la mémoire tampon n’était pas suffisamment longue.  
  
- La partie transition de la fonction est ignorée si `pTransitionContexts` et `puiTransitionContextCount` ont tous les deux la valeur null. Dans ce cas, la fonction fournit aux appelants une sortie texte uniquement des noms de fonctions.  
  
- Si `pTransitionContexts` a la valeur null et que `puiTransitionContextCount` n’a pas la valeur null, la fonction retourne le nombre nécessaire d’entrées de contexte dans `puiTransitionContextCount`.  
  
- Si `pTransitionContexts` n’a pas la valeur null, la fonction la traite comme un tableau de structures de longueur `puiTransitionContextCount`. La taille de la structure est donnée par `uiSizeOfContext`et doit être la taille de [SimpleContext](stacktrace-simplecontext-structure.md) ou `CONTEXT` pour l’architecture.  
  
- `wszTextOut` est écrit dans le format suivant :  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Si le décalage dans hex est 0x0, aucun décalage n’est écrit.  
  
- S’il n’existe aucun code managé sur le thread actuellement en contexte, la fonction retourne SOS_E_NOMANAGEDCODE.  
  
- Le paramètre `Flags` est égal à 0 ou SOS_STACKTRACE_SHOWADDRESSES pour voir EBP et ESP devant chaque ligne de `module!functionname`. Par défaut, il est égal à 0.  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** SOS_Stacktrace. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de débogage](debugging-global-static-functions.md)
