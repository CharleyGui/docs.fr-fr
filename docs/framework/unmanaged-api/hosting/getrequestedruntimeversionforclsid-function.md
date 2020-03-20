---
title: GetRequestedRuntimeVersionForCLSID, fonction
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178114"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID, fonction
Obtient les informations appropriées de version de l’heure courante `CLSID`(CLR) pour la classe avec le spécifié .  
  
 Cette fonction a été dépréciée dans le cadre .NET 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `rclsid`  
 [dans]  Le `CLSID` composant.  
  
 `pVersion`  
 [out]  Un tampon qui contient la chaîne de numéro de version une fois terminé.  
  
 `cchBuffer`  
 [dans]  La taille, en caractères `pVersion` larges, du tampon.  
  
 `dwLength`  
 [out] La longueur, dans les octets, du tampon retourné.  
  
 `dwResolutionFlags`  
 [dans]  Une des valeurs CLSID_RESOLUTION_FLAGS. Les valeurs suivantes sont admises :  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) précise que le comportement interop par défaut doit être utilisé.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) précise que le registre doit être recherché et la politique cale doit être appliquée.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La fonction est revenue avec succès.|  
|E_INVALIDARG|L’un des paramètres a un type ou un format invalide.|  
|ERROR_INSUFFICIENT_BUFFER|Le `pVersion` tampon n’est pas assez grand pour tenir la chaîne de version entière.|  
|REGDB_E_CLASSNOTREG|Il n’y a `CLSID`pas de classe enregistrée auprès des spécifiés .|  
|E_POINTER|`dwLength`est nul, `cchBuffer` ou est assez grand pour `pVersion` tenir la chaîne de version, mais est nul.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
