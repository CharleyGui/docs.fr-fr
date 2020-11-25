---
title: NukeDownloadedCache, fonction
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
ms.openlocfilehash: 5ae0a887d666a150b717d495848c8a411d030a09
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728574"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache, fonction

Supprime le cache de téléchargement common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Valeur de retour  

 Cette méthode retourne les codes d’erreur COM standard, tels que définis dans WinError. h.  
  
## <a name="remarks"></a>Remarques  

 Le cache de téléchargement CLR est la zone dans laquelle les assemblys avec nom fort téléchargés à partir d’une URL sont stockés pour une éventuelle réutilisation.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque :** Fusion.dll et Mscorwks.dll. Utilisez Fusion.dll au lieu de Mscorwks.dll pour vous assurer que vous ciblez la version correcte du .NET Framework.  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CreateHistoryReader, fonction](createhistoryreader-function.md)
- [GetHistoryFileDirectory, fonction](gethistoryfiledirectory-function.md)
- [Fonctions statiques globales de la fusion](fusion-global-static-functions.md)
