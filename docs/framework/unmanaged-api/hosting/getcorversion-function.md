---
title: GetCORVersion, fonction
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: e7ef3f300c8cfa0c275d15913e171abe09385eea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681200"
---
# <a name="getcorversion-function"></a>GetCORVersion, fonction

Retourne le numéro de version du common language runtime (CLR) qui s’exécute dans le processus en cours.  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a>Paramètres  

 `pbuffer`  
 Pointeur vers une mémoire tampon dans laquelle le CLR retourne une chaîne spécifiant la version du runtime actuellement chargée dans le processus. La chaîne retournée prend la même forme que les chaînes passées à [CorBindToRuntimeEx](corbindtoruntimeex-function.md), par exemple, « v 1.0.1216 ». Si le runtime n’a pas encore été chargé dans le processus, la fonction retourne les informations de répertoire appropriées pour la version la plus récente du runtime installée sur l’ordinateur.  
  
 `cchBuffer`  
 Nombre de caractères `WCHAR` qui peuvent être contenus dans `pbuffer` .  
  
 `dwLength`  
 Pointeur vers le nombre de caractères réellement retournés dans `pbuffer` . Si `pbuffer` est un pointeur null, le runtime retourne E_POINTER. Si le nombre de caractères est supérieur à la longueur de `pbuffer` , le runtime retourne ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** MSCorEE. h  
  
 **Bibliothèque :** MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
