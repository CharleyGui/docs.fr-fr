---
title: ICorPublishEnum, interface
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: acbc37d0f49af21c60ff6989932c5d341673512b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421174"
---
# <a name="icorpublishenum-interface"></a>ICorPublishEnum, interface
Sert d’interface de base abstraite pour les énumérateurs utilisés dans la publication d’informations sur les processus et les domaines d’application.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Clone, méthode](icorpublishenum-clone-method.md)|Crée une copie de cet objet `ICorPublishEnum`.|  
|[GetCount, méthode](icorpublishenum-getcount-method.md)|Obtient le nombre d’éléments dans l’énumération.|  
|[Reset, méthode](icorpublishenum-reset-method.md)|Déplace le curseur de au début de l’énumération.|  
|[Skip, méthode](icorpublishenum-skip-method.md)|Déplace le curseur vers l’avant dans l’énumération d’après le nombre d’éléments spécifié.|  
  
## <a name="remarks"></a>Notes  
 Les énumérateurs suivants dérivent de `ICorPublishEnum` :  
  
- [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md)  
  
- [ICorPublishProcessEnum](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorPub. idl, CorPub. h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CorpubPublish (coclasse)](corpubpublish-coclass.md)
- [Interfaces de débogage](debugging-interfaces.md)
