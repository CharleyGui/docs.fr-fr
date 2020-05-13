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
ms.openlocfilehash: ccd2350589126109ff11da439a8b83abfc4b91fa
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210473"
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
 dans `CORDB_ADDRESS`Valeur qui spécifie l’adresse de base de la mémoire à lire.  
  
 `size`  
 dans Nombre d’octets à lire à partir de la mémoire.  
  
 `buffer`  
 à Mémoire tampon qui reçoit le contenu de la mémoire.  
  
 `read`  
 à Pointeur vers le nombre d’octets transférés dans la mémoire tampon spécifiée.  
  
## <a name="remarks"></a>Remarks  
 La `ReadMemory` méthode est principalement destinée à être utilisée par le débogage d’interopérabilité pour inspecter les régions de mémoire utilisées par la partie non managée de l’élément débogué. Cette méthode peut également être utilisée pour lire le code MSIL (Microsoft Intermediate Language) et le code natif compilé juste-à-temps.  
  
 Tous les points d’arrêt managés seront supprimés des données retournées dans le `buffer` paramètre. Aucun ajustement n’est effectué pour les points d’arrêt natifs définis par [ICorDebugProcess2 :: SetUnmanagedBreakpoint,](icordebugprocess2-setunmanagedbreakpoint-method.md).  
  
 Aucune mise en cache de la mémoire du processus n’est effectuée.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
