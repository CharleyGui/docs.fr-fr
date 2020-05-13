---
title: ICorDebugProcess2::SetUnmanagedBreakpoint, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: 6b9396d03892f29e3698af90856d0c0023dc628a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213463"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>ICorDebugProcess2::SetUnmanagedBreakpoint, méthode
Définit un point d’arrêt non managé au niveau de l’offset d’image native spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `address`  
 dans `CORDB_ADDRESS`Objet qui spécifie le décalage de l’image native.  
  
 `bufsize`  
 dans Taille, en octets, du `buffer` tableau.  
  
 `buffer`  
 à Tableau qui contient l’opcode qui est remplacé par le point d’arrêt.  
  
 `bufLen`  
 à Pointeur vers le nombre d’octets retournés dans le `buffer` tableau.  
  
## <a name="remarks"></a>Remarks  
 Si le décalage de l’image native se trouve dans le common language runtime (CLR), le point d’arrêt est ignoré. Cela permet au CLR d’éviter la distribution d’un point d’arrêt hors bande, lorsque le point d’arrêt est défini par le débogueur.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
