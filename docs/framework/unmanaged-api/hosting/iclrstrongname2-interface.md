---
title: ICLRStrongName2, interface
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: bc871c29f53a9ea4451a0fc1c747939724b0da87
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092244"
---
# <a name="iclrstrongname2-interface"></a>ICLRStrongName2, interface
Offre la possibilité de créer des noms forts à l’aide du groupe SHA-2 d’algorithmes de hachage sécurisé (SHA-256, SHA-384 et SHA-512).  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[StrongNameGetPublicKeyEx, méthode](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|Obtient la clé publique à partir d’une paire de clés publique/privée et spécifie un algorithme de hachage et un algorithme de signature.|  
|[StrongNameSignatureVerificationEx2, méthode](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|Vérifie la signature d’un assembly avec un nom fort et fournit un mappage de la clé ECMA à une clé réelle.|  
  
## <a name="remarks"></a>Notes  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Metahost. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
