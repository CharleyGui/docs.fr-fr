---
title: GetRealProcAddress, fonction
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
ms.openlocfilehash: 6bbf8366054c58543444a4b710a687198f365e6e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617189"
---
# <a name="getrealprocaddress-function"></a>GetRealProcAddress, fonction
Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée du common language runtime (CLR).  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwszProcName`  
 dans Nom de la fonction.  
  
 `ppv`  
 à Emplacement qui reçoit un pointeur vers l’adresse de la fonction.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes définies dans CorError. h.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|La commande s'est correctement terminée.|  
|E_POINTER|`ppv` n'est pas valide.|  
|CLR_E_SHIM_RUNTIMEEXPORT|La fonction n’est pas exportée à partir du Runtime.|  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
