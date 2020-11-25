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
ms.openlocfilehash: 6c16b02a5ae323ba80d44937f322810022dfa9f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711635"
---
# <a name="getrequestedruntimeversion-function"></a>GetRequestedRuntimeVersion, fonction

Obtient le numéro de version du common language runtime (CLR) demandé par l’application spécifiée. Si cette version n’est pas installée, obtient la version la plus récente installée avant la version demandée.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
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
 dans Nom de l’application.  
  
 `pVersion`  
 à Mémoire tampon qui contient la chaîne de numéro de version en cas de réussite.  
  
 `cchBuffer`  
 dans Longueur de la mémoire tampon de version.  
  
 `pdwLength`  
 à Pointeur vers la longueur de la chaîne de numéro de version.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|ERROR_INSUFFICIENT_BUFFER|La mémoire tampon de version n’est pas assez grande pour stocker la chaîne de version.|  
|E_POINTER|`pdwLength` a la valeur null.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetRequestedRuntimeInfo, fonction](getrequestedruntimeinfo-function.md)
- [GetVersionFromProcess, fonction](getversionfromprocess-function.md)
- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
