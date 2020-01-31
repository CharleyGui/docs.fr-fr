---
title: ICorDebugInternalFrame2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
ms.openlocfilehash: 9e333d71505a055cfe27df2c79a102c939bafc9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788475"
---
# <a name="icordebuginternalframe2-interface"></a>ICorDebugInternalFrame2, interface
Fournit des informations sur les frames internes, notamment l'adresse et la position de la pile par rapport aux objets ICorDebugFrame.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetFrameAddress, méthode](icordebuginternalframe2-getframeaddress-method.md)|Retourne l’adresse de la pile du frame interne.|  
|[IsCloserToLeaf, méthode](icordebuginternalframe2-isclosertoleaf-method.md)|Vérifie si le `this` Frame interne est plus proche de la feuille que l’objet ICorDebugFrame spécifié.|  
  
## <a name="remarks"></a>Notes  
 Cette interface étend l’interface ICorDebugInternalFrame.  
  
> [!NOTE]
> Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.  
  
## <a name="requirements"></a>Configuration requise pour  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de débogage](debugging-interfaces.md)
- [Débogage](index.md)
