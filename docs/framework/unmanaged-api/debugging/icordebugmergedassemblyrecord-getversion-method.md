---
title: ICorDebugMergedAssemblyRecord::GetVersion, méthode
ms.date: 03/30/2017
ms.assetid: c6858b06-ae26-4312-b325-ea6025016675
ms.openlocfilehash: 5dc9995e88086da854d2e9382cef81b229ff9dc9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178686"
---
# <a name="icordebugmergedassemblyrecordgetversion-method"></a>ICorDebugMergedAssemblyRecord::GetVersion, méthode
Obtient les informations de version de l'assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersion(  
   [out] USHORT *pMajor,
   [out] USHORT *pMinor,
   [out] USHORT *pBuild,
   [out] USHORT *pRevision  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pMajor`  
 [out] Pointeur vers le numéro de version principale.  
  
 `pMinor`  
 [out] Pointeur vers le numéro de version secondaire.  
  
 `pBuild`  
 [out] Pointeur vers le numéro de build.  
  
 `pRevision`  
 [out] Pointeur vers le numéro de révision.  
  
## <a name="remarks"></a>Notes   
 Pour plus d'informations sur les numéros de version d'assembly, consultez la rubrique de la classe <xref:System.Version>.  
  
> [!NOTE]
> Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICorDebugMergedAssemblyRecord, interface](icordebugmergedassemblyrecord-interface.md)
- [Interfaces de débogage](debugging-interfaces.md)
