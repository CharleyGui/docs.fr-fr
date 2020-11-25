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
ms.openlocfilehash: 51cca1ab61027090b0d22781dfd740038bc9372d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718200"
---
# <a name="imaptokenmap-method"></a>IMapToken::Map, méthode

Mappe une relation entre les assemblys à l’aide de signatures de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Map (  
    [in]  mdToken tkImp,
    [in]  mdToken tkEmit  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `tkImp`  
 dans Jeton de métadonnées qui représente l’objet de code importé.  
  
 `tkEmit`  
 dans Jeton de métadonnées qui représente l’objet de code émis.  
  
## <a name="remarks"></a>Remarques  

 Lorsque le mappage de jeton se produit pendant une fusion, le jeton d’origine est étendu dans l’étendue de métadonnées importée (source) et le nouveau jeton est défini dans la portée des métadonnées (cible) émise.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMapToken, interface](imaptoken-interface.md)
