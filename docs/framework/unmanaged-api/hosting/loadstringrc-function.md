---
title: LoadStringRC, fonction
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176238"
---
# <a name="loadstringrc-function"></a>LoadStringRC, fonction
Traduit une valeur HRESULT en message d’erreur en utilisant la culture par défaut du thread actuel.  
  
 Cette fonction a été dépréciée dans le cadre .NET 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `iResourceID`  
 [in] HRESULT.  
  
 `szBuffer`  
 [out] Un tampon qui contient le message d’erreur une fois terminé.  
  
 `iMax`  
 [dans] La taille du tampon de message d’erreur.  
  
 `bQuiet`  
 [dans] Ignoré.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode renvoie les codes d’erreur standard du modèle d’objet composant (COM), tels que définis dans WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|`szBuffer`est nul `iMax` ou est nul (0).|  
  
## <a name="remarks"></a>Notes   
 Si la méthode ne `szBuffer` se termine pas avec succès, contient une ficelle vide.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll et Mscorwks.dll. Utilisez MSCorEE.dll au lieu de Mscorwks.dll pour vous assurer que vous ciblez la version correcte du cadre .NET.  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [LoadStringRCEx, fonction](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
