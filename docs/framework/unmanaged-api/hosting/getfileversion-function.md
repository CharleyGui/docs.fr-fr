---
title: GetFileVersion, fonction
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: f3b51c1b376fa9c664de53aa76ec724ca305ae6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178177"
---
# <a name="getfileversion-function"></a>GetFileVersion, fonction
Obtient les informations courantes de version de l’heure d’exécution de langue (CLR) du fichier spécifié, en utilisant le tampon spécifié.  
  
 Cette fonction a été dépréciée dans le cadre .NET 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szFilename`  
 [dans] La voie du dossier à examiner.  
  
 `szBuffer`  
 [dans, dehors] Le tampon alloué pour les informations de version qui sont retournées.  
  
 `cchBuffer`  
 [dans] La taille, en caractères larges, de `szBuffer`.  
  
 `dwLength`  
 [out] La taille, dans les octets, du retour `szBuffer`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
