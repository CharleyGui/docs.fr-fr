---
title: Fonction EnumerateCLRs
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
ms.openlocfilehash: 1f33fb98712939d1e687798547b784819f164d63
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860723"
---
# <a name="enumerateclrs-function"></a>Fonction EnumerateCLRs
Fournit un mécanisme pour énumérer les CLR dans un processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `debuggeePID`  
 [in] Identificateur du processus à partir duquel les CLR chargés sont énumérés.  
  
 `ppHandleArrayOut`  
 [out] Pointeur vers un tableau contenant les handles d'événements utilisés pour poursuivre un démarrage du CLR. Chaque handle du tableau n'est pas garanti comme valide. Si valide, le handle doit être utilisé comme l'événement continue-startup du runtime correspondant situé dans le même index de `ppStringArrayOut`.  
  
 `ppStringArrayOut`  
 [out] Pointeur vers un tableau de chaînes qui spécifient des chemins d'accès complets aux CLR chargés dans le processus.  
  
 `pdwArrayLengthOut`  
 [out] Pointeur vers une valeur DWORD qui contient la longueur de `ppHandleArrayOut` et `pdwArrayLengthOut` de taille égale.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK  
 Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.  
  
 E_INVALIDARG  
 `ppHandleArrayOut` a la valeur null, ou `ppStringArrayOut` ou `pdwArrayLengthOut` a la valeur null.  
  
 E_OUTOFMEMORY  
 La fonction ne peut pas allouer suffisamment de mémoire pour les tableaux de handles et de chemins d'accès.  
  
 E_FAIL (ou autres codes de retour E_)  
 Impossible d'énumérer les CLR chargés.  
  
## <a name="remarks"></a>Notes   
 Pour un processus cible qui est identifié par `debuggeePID`, la fonction retourne un tableau de chemins d’accès, `ppStringArrayOut`, vers les CLR chargés dans le processus ; un tableau de handles d’événement, `ppHandleArrayOut`, qui peut contenir un événement continue-startup pour le CLR au même index ; et la taille des tableaux, `pdwArrayLengthOut`, qui spécifie le nombre de CLR chargés.  
  
 Sur le système d'exploitation Windows, `debuggeePID` est mappé à un identificateur de processus du système d'exploitation.  
  
 La mémoire pour `ppHandleArrayOut` et `ppStringArrayOut` est allouée par cette fonction. Pour libérer la mémoire allouée, vous devez appeler la [fonction CloseCLREnumeration](closeclrenumeration-function.md).  
  
 Cette fonction peut être appelée en affectant la valeur null aux deux paramètres de tableau afin de retourner le nombre de CLR dans le processus cible. Avec ce nombre, un appelant peut déduire la taille de la mémoire tampon qui sera créée : `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** dbgshim. h  
  
 **Bibliothèque :** dbgshim. dll  
  
 **Versions de .NET Framework :** 3,5 SP1
