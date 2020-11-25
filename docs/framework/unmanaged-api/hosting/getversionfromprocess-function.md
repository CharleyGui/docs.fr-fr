---
title: GetVersionFromProcess, fonction
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: da0d159da6eef7745c1fa7f7320d5e1355f6e413
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721879"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess, fonction

Obtient le numéro de version du common language runtime (CLR) associé au handle de processus spécifié.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `hProcess`  
 dans Handle d’un processus.  
  
 `pVersion`  
 à Mémoire tampon qui contient la chaîne de numéro de version en cas d’achèvement réussi de la méthode.  
  
 `cchBuffer`  
 dans Longueur de la mémoire tampon de version.  
  
 `pdwLength`  
 à Pointeur vers la longueur de la chaîne de numéro de version.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_INVALIDARG|`pVersion` a la valeur null et `cchBuffer` n’est pas null, ou vice versa.<br /><br /> - ou -<br /><br /> `hProcess` n’est pas un handle valide pour un processus.<br /><br /> - ou -<br /><br /> Le CLR n’est pas chargé.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` est null ou inférieur à la longueur de la chaîne de version.|  
|E_NOTIMPL|Cette méthode n’est pas disponible sur le système d’exploitation Microsoft Windows 95, Microsoft Windows 98 ou Microsoft Windows Millennium Edition.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetRequestedRuntimeInfo, fonction](getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion, fonction](getrequestedruntimeversion-function.md)
- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
