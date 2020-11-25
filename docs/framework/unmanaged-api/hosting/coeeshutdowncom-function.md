---
title: CoEEShutDownCOM, fonction
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
ms.openlocfilehash: 774704698f92d546d6bafa61c65d18d083c65f89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716757"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM, fonction

Force le common language runtime (CLR) à libérer tous les pointeurs d’interface qu’il contient dans les wrappers RCW (Runtime Callable Wrapper). Cela a pour effet de libérer tous les caches RCW. Cette fonction globale est dépréciée dans le .NET Framework 4. Utilisez plutôt le point d’entrée pour un Runtime spécifique.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Notes  

 La `CoEEShutDownCOM` fonction libère d’abord tous les RCW dans tous les contextes et dans tous les caches, puis supprime toutes les notifications de destruction existantes dans le programme d’installation. Aucun déchargement de DLL ne se produit.  
  
> [!CAUTION]
> Cette fonction affecte tous les runtimes chargés dans le processus.  
  
 À partir du .NET Framework 4, appelez le point d’entrée de cette fonction sur le runtime spécifique que vous souhaitez affecter. Pour accéder au point d’entrée, appelez la méthode [ICLRRuntimeInfo :: GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) et spécifiez « CoEEShutDownCOM, ».  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../metadata/metadata-global-static-functions.md)
