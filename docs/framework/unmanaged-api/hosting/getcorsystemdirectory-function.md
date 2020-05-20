---
title: GetCORSystemDirectory, fonction
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 137b2e30916cb1934d4389c5668bfb7eb5066064
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617228"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory, fonction
Retourne le répertoire d’installation du common language runtime (CLR) qui est chargé dans le processus. Le répertoire d’installation est complet, par exemple, « c:\Windows\Microsoft.NET\Framework\v1.0.3705 ».  
  
 Cette fonction est déconseillée. Elle est remplacée par la méthode [ICLRRuntimeInfo :: GetRuntimeDirectory,](iclrruntimeinfo-getruntimedirectory-method.md) fournie dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a>Paramètres  
 `pbuffer`  
 à Mémoire tampon dans laquelle le runtime retourne une chaîne qui contient le nom qualifié complet du répertoire d’installation du runtime chargé dans le processus. Si le runtime n’a pas encore été chargé dans le processus, la fonction retourne les informations de répertoire appropriées pour la version la plus récente du runtime installée sur l’ordinateur.  
  
 `cchBuffer`  
 dans Taille, en octets, de `pbuffer` .  
  
 `dwLength`  
 à Nombre de caractères retournés dans `pbuffer` .  
  
## <a name="remarks"></a>Notes  
  
> [!CAUTION]
> N’utilisez pas cette fonction dans les processus qui exécutent la version 4 du CLR. Si une version antérieure du CLR est installée sur l’ordinateur, cette fonction retourne le répertoire d’installation de cette version.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
