---
title: StrongNameHashSize, fonction
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8093a702069e4ecd4dad761ad0a431abe81d6141
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780423"
---
# <a name="strongnamehashsize-function"></a>StrongNameHashSize, fonction
Obtient la taille de mémoire tampon requise pour un hachage, à l’aide de l’algorithme de hachage spécifié.  
  
 Cette fonction a été déconseillée. Utilisez le [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ulHashAlg`  
 [in] L’algorithme de hachage utilisé pour calculer la taille du tampon.  
  
 `pcbSize`  
 [out] La taille de la mémoire tampon retournée, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 `true` de réussite ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Si le `StrongNameHashSize` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameHashSize, méthode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)
- [ICLRStrongName, interface](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
