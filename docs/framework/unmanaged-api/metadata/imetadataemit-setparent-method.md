---
title: IMetaDataEmit::SetParent, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: cef817b52718acfbc4360e9d3742a5a78abd3afe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675046"
---
# <a name="imetadataemitsetparent-method"></a>IMetaDataEmit::SetParent, méthode

Établit que le membre spécifié, tel que défini par un appel antérieur à [IMetaDataEmit ::D efinememberref](imetadataemit-definememberref-method.md), est un membre du type spécifié, tel que défini par un appel antérieur à [IMetaDataEmit ::D efinetypedef](imetadataemit-definetypedef-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `mr`  
 dans `mdMemberRef` Jeton pour recevoir un nouveau parent.  
  
 `tk`  
 dans `mdToken` Pour le nouveau parent.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](imetadataemit-interface.md)
- [IMetaDataEmit2, interface](imetadataemit2-interface.md)
