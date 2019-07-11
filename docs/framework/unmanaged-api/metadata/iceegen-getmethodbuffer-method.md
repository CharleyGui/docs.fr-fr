---
title: ICeeGen::GetMethodBuffer, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 14ea8dab2c4258fe490ef362fd527d80bd8a0178
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746107"
---
# <a name="iceegengetmethodbuffer-method"></a>ICeeGen::GetMethodBuffer, méthode
Obtient une mémoire tampon de la taille appropriée pour la méthode à l’adresse virtuelle relative spécifiée.  
  
 Cette méthode est obsolète et ne doit pas être utilisée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `RVA`  
 [in] L’adresse virtuelle relative de la méthode pour laquelle retourner une mémoire tampon.  
  
 `lpBuffer`  
 [out] Pointeur vers la mémoire tampon retournée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICeeGen, interface](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
