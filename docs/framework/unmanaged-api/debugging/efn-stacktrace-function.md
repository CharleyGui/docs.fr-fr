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
ms.openlocfilehash: 9b7624c2902d17e437cda9a0a84ddf288323b577
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676177"
---
# <a name="_efn_stacktrace-function"></a>\_EFN \_ fonction StackTrace

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
 à Pointeur vers le nombre de caractères dans `wszTextOut` .  
  
 `pTransitionContexts`  
 à Tableau de contextes de transition.  
  
 `puiTransitionContextCount`  
 à Pointeur vers le nombre de contextes de transition dans le tableau.  
  
 `uiSizeOfContext`  
 dans Taille de la structure de contexte.  
  
 `Flags`  
 dans Définissez sur 0 ou SOS_STACKTRACE_SHOWADDRESSES (0x01) pour afficher le registre EBP et le pointeur de pile Enter (ESP) devant chaque `module!functionname` ligne.  
  
## <a name="remarks"></a>Remarques  

 La `_EFN_StackTrace` structure peut être appelée à partir d’une interface de programmation WinDbg. Les paramètres sont utilisés comme suit :  
  
- Si `wszTextOut` a la valeur null et que `puiTextLength` n’est pas null, la fonction retourne la longueur de la chaîne dans `puiTextLength` .  
  
- Si `wszTextOut` n’a pas la valeur null, la fonction stocke le texte dans `wszTextOut` l’emplacement indiqué par `puiTextLength` . Elle retourne avec succès si la mémoire tampon est suffisamment grande, ou si elle retourne E_OUTOFMEMORY si la mémoire tampon n’était pas suffisamment longue.  
  
- La partie transition de la fonction est ignorée si `pTransitionContexts` et `puiTransitionContextCount` sont tous deux null. Dans ce cas, la fonction fournit aux appelants une sortie texte uniquement des noms de fonctions.  
  
- Si `pTransitionContexts` a la valeur null et que `puiTransitionContextCount` n’est pas null, la fonction retourne le nombre nécessaire d’entrées de contexte dans `puiTransitionContextCount` .  
  
- Si `pTransitionContexts` n’a pas la valeur null, la fonction la traite comme un tableau de structures de longueur `puiTransitionContextCount` . La taille de la structure est donnée par `uiSizeOfContext` , et doit être la taille de [SimpleContext](stacktrace-simplecontext-structure.md) ou `CONTEXT` de l’architecture.  
  
- `wszTextOut` est écrit au format suivant :  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- Si le décalage dans hex est 0x0, aucun décalage n’est écrit.  
  
- S’il n’existe aucun code managé sur le thread actuellement en contexte, la fonction retourne SOS_E_NOMANAGEDCODE.  
  
- Le `Flags` paramètre est égal à 0 ou SOS_STACKTRACE_SHOWADDRESSES pour voir EBP et ESP devant chaque `module!functionname` ligne. Par défaut, il est égal à 0.  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** SOS_Stacktrace. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales du débogage](debugging-global-static-functions.md)
