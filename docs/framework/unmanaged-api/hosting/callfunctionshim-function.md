---
title: CallFunctionShim, fonction
ms.date: 03/30/2017
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dfe2c98fd5898a0ad5a1d4fd9e89c7f20741bb0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490699"
---
# <a name="callfunctionshim-function"></a>CallFunctionShim, fonction
Effectue un appel à la fonction qui a le nom spécifié et les paramètres dans la bibliothèque spécifiée.  
  
 Cette fonction a été déconseillée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szDllName`  
 [in] Le nom de la bibliothèque contenant la fonction.  
  
 `szFunctionName`  
 [in] Le nom de la fonction.  
  
 `lpvArgument1`  
 [in] Le premier argument à passer à la fonction.  
  
 `lpvArgument2`  
 [in] Le deuxième argument à passer à la fonction.  
  
 `szVersion`  
 [in] La version de la bibliothèque qui contient la fonction.  
  
 `pvReserved`  
 [in] Réservé pour une utilisation ultérieure. Passer zéro dans ce paramètre.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE.h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’hébergement CLR dépréciées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
