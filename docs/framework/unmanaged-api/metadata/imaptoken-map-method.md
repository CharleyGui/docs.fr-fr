---
title: IMapToken::Map, méthode
ms.date: 03/30/2017
api_name:
- IMapToken.Map
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMapToken::Map
helpviewer_keywords:
- IMapToken::Map method [.NET Framework metadata]
- Map method [.NET Framework metadata]
ms.assetid: b9b4bf2f-1098-43d6-9619-a99b4bda1940
topic_type:
- apiref
ms.openlocfilehash: 428b022ed560648f59798154d5987d382938c280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176069"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map, méthode
Cartographiez une relation entre les assemblées à l’aide de signatures de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `tkImp`  
 [dans] Le jeton des métadonnées qui représente l’objet de code importé.  
  
 `tkEmit`  
 [dans] Le jeton des métadonnées qui représente l’objet de code émis.  
  
## <a name="remarks"></a>Notes   
 Lorsque la refonte du jeton se produit lors d’une fusion, le jeton d’origine est visé dans la portée des métadonnées importées (source) et le nouveau jeton est visé dans la portée des métadonnées émises (cible).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** Cor.h (en)  
  
 **Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMapToken, interface](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)
