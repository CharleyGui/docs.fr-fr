---
title: GetRequestedRuntimeVersion, fonction
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 6be0bc5d08f612dcb8ed7d256711e0c4367b9274
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178139"
---
# <a name="getrequestedruntimeversion-function"></a>GetRequestedRuntimeVersion, fonction
Obtient le numéro de version de l’heure d’exécution de langue commune (CLR) demandée par l’application spécifiée. Si cette version n’est pas installée, obtient la version la plus récente qui est installée avant la version demandée.  
  
 Cette fonction a été dépréciée dans le cadre .NET 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pExe`  
 [dans] Le nom de l’application.  
  
 `pVersion`  
 [out] Un tampon qui contient la chaîne de numéro de version une fois terminé.  
  
 `cchBuffer`  
 [dans] La longueur du tampon de version.  
  
 `pdwLength`  
 [out] Un pointeur sur la longueur de la chaîne de numéro de version.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode renvoie les codes d’erreur standard du modèle d’objet composant (COM), tels que définis dans WinError.h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|ERROR_INSUFFICIENT_BUFFER|Le tampon de version n’est pas assez grand pour stocker la chaîne de version.|  
|E_POINTER|`pdwLength` a la valeur null.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetRequestedRuntimeInfo, fonction](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetVersionFromProcess, fonction](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
