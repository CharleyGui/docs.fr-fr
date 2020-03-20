---
title: ICorDebugProcess::ReadMemory, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178664"
---
# <a name="icordebugprocessreadmemory-method"></a>ICorDebugProcess::ReadMemory, méthode
Lit une zone de mémoire spécifiée pour ce processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a>Paramètres  
 `address`  
 [dans] Une `CORDB_ADDRESS` valeur qui spécifie l’adresse de base de la mémoire à lire.  
  
 `size`  
 [dans] Le nombre d’octets à lire de mémoire.  
  
 `buffer`  
 [out] Un tampon qui reçoit le contenu de la mémoire.  
  
 `read`  
 [out] Un pointeur sur le nombre d’octets transférés dans le tampon spécifié.  
  
## <a name="remarks"></a>Notes   
 La `ReadMemory` méthode est principalement destinée à être utilisée par le débogage interop pour inspecter les régions de mémoire qui sont utilisées par la partie non gestion du débbuggee. Cette méthode peut également être utilisée pour lire le code de langue intermédiaire Microsoft (MSIL) et le code CIT natif.  
  
 Tous les points d’arrêt gérés seront supprimés `buffer` des données retournées dans le paramètre. Aucun ajustement ne sera apporté pour les points de rupture natifs définis par [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Aucune mise en cache de la mémoire du processus n’est effectuée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
