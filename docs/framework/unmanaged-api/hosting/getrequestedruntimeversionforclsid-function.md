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
ms.openlocfilehash: 899d6e74902e47f1f41b849bd5c25048baa175f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617137"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID, fonction
Obtient les informations de version de common language runtime (CLR) appropriées pour la classe avec le spécifié `CLSID` .  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
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
 dans  `CLSID`Du composant.  
  
 `pVersion`  
 à  Mémoire tampon qui contient la chaîne de numéro de version en cas de réussite.  
  
 `cchBuffer`  
 dans  Taille, en caractères larges, de la `pVersion` mémoire tampon.  
  
 `dwLength`  
 à Longueur, en octets, de la mémoire tampon retournée.  
  
 `dwResolutionFlags`  
 dans  L’une des valeurs CLSID_RESOLUTION_FLAGS. Les valeurs suivantes sont admises :  
  
- CLSID_RESOLUTION_DEFAULT : (0x0) spécifie que le comportement d’interopérabilité par défaut doit être utilisé.  
  
- CLSID_RESOLUTION_REGISTERED : (0x1) spécifie que la recherche doit être effectuée dans le registre et que la stratégie de shim doit être appliquée.  
  
## <a name="return-value"></a>Valeur de retour  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|La fonction a été retournée avec succès.|  
|E_INVALIDARG|Le type ou le format de l’un des paramètres n’est pas valide.|  
|ERROR_INSUFFICIENT_BUFFER|La `pVersion` mémoire tampon n’est pas assez grande pour contenir la chaîne de version entière.|  
|REGDB_E_CLASSNOTREG|Aucune classe n’est inscrite avec le spécifié `CLSID` .|  
|E_POINTER|`dwLength`a la valeur null ou `cchBuffer` est suffisamment grand pour contenir la chaîne de version, mais `pVersion` a la valeur null.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
