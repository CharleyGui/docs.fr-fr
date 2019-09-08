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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 29f492173a7fd22ab497d6e0096798e164fccf26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796306"
---
# <a name="nukedownloadedcache-function"></a>NukeDownloadedCache, fonction
Supprime le cache de téléchargement common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les codes d’erreur COM standard, tels que définis dans WinError. h.  
  
## <a name="remarks"></a>Notes  
 Le cache de téléchargement CLR est la zone dans laquelle les assemblys avec nom fort téléchargés à partir d’une URL sont stockés pour une éventuelle réutilisation.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque** Fusion. dll et mscorwks. dll. Utilisez fusion. dll au lieu de Mscorwks. dll pour vous assurer que vous ciblez la version correcte du .NET Framework.  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CreateHistoryReader, fonction](createhistoryreader-function.md)
- [GetHistoryFileDirectory, fonction](gethistoryfiledirectory-function.md)
- [Fonctions statiques globales de fusion](fusion-global-static-functions.md)
