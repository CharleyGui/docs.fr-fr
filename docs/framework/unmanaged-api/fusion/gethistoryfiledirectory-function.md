---
title: GetHistoryFileDirectory, fonction
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
ms.openlocfilehash: 484adf288356b9955fe0cac0bb30002ec1f012d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724436"
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory, fonction

Récupère le chemin d’accès du répertoire de l’historique de l’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `wzDir`  
 à Mémoire tampon pour stocker le chemin d’accès au répertoire de l’historique de l’application.  
  
 `pdwSize`  
 [in, out] Longueur de la mémoire tampon.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne les codes d’erreur COM standard, tels que définis dans le fichier WinError. h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|`wzDir` ou `pdwSize` est null, ou la chaîne de version est incorrecte.|  
  
## <a name="remarks"></a>Remarques  

 Une fois l’opération terminée, l' `pdwSize` argument est défini sur la longueur de la chaîne de chemin d’accès.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque :** Fusion.dll et Mscorwks.dll. Utilisez Fusion.dll au lieu de Mscorwks.dll pour vous assurer que vous ciblez la version correcte du .NET Framework.  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [CreateHistoryReader, fonction](createhistoryreader-function.md)
- [NukeDownloadedCache, fonction](nukedownloadedcache-function.md)
- [Fonctions statiques globales de la fusion](fusion-global-static-functions.md)
