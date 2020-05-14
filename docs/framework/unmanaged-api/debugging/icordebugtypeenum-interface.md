---
title: ICorDebugTypeEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum
helpviewer_keywords:
- ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: 159ccfcf-b37c-4ad9-8e0d-a9a443262472
topic_type:
- apiref
ms.openlocfilehash: c647bc7a4a1b8a25a225482ee46db4cc1837b501
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396658"
---
# <a name="icordebugtypeenum-interface"></a>ICorDebugTypeEnum, interface
Implémente les méthodes « ICorDebugEnum » et énumère les tableaux « ICorDebugType ».  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next, méthode](icordebugtypeenum-next-method.md)|Obtient le nombre d' `ICorDebugType` instances spécifié à partir de l’énumération, en commençant à la position actuelle.|  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
