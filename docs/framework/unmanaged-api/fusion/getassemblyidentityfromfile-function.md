---
title: GetAssemblyIdentityFromFile, fonction
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
ms.openlocfilehash: 9580dd3bc5a7279549e8deadac95d35a33da74f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724479"
---
# <a name="getassemblyidentityfromfile-function"></a>GetAssemblyIdentityFromFile, fonction

Obtient un pointeur vers un `IUnknown` objet avec le spécifié `IID` dans l’assembly dans le chemin d’accès au fichier spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a>Paramètres  

 `pwzFilePath`  
 dans Chemin d’accès valide à l’assembly demandé.  
  
 `riid`  
 dans `IID` De l’interface à retourner.  
  
 `ppIdentity`  
 à Pointeur d’interface retourné.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IUnknown](/cpp/atl/iunknown)
- [Fonctions statiques globales de la fusion](fusion-global-static-functions.md)
