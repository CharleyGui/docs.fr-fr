---
title: _CorValidateImage, fonction
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 42da5bb761ba8ce388bd41d46e8fdc4561ad0290
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136885"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage, fonction
Valide les images de modules managés et notifie le chargeur du système d’exploitation après qu’elles ont été chargées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ImageBase`  
 dans Pointeur vers l’emplacement de départ de l’image à valider comme code managé. L’image doit déjà être chargée dans la mémoire.  
  
 `FileName`  
 dans Nom de fichier de l’image.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette fonction retourne les valeurs standard `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`et `E_FAIL`, ainsi que les valeurs suivantes.  
  
|Valeur de retour|Description|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|L’image n’est pas valide. Cette valeur a le HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|L’image est valide. Cette valeur a le HRESULT 0x00000000L.|  
  
## <a name="remarks"></a>Notes  
 Dans Windows XP et versions ultérieures, le chargeur du système d’exploitation recherche les modules managés en examinant le bit du répertoire du descripteur COM dans l’en-tête COFF (Common Object File Format). Un bit défini indique un module managé. Si le chargeur détecte un module managé, il charge MsCorEE. dll et appelle `_CorValidateImage`, qui effectue les actions suivantes :  
  
- Confirme que l’image est un module managé valide.  
  
- Modifie le point d’entrée dans l’image en point d’entrée dans le common language runtime (CLR).  
  
- Pour les versions 64 bits de Windows, modifie l’image en mémoire en la transformant de PE32 en format PE32 +.  
  
- Retourne au chargeur lorsque les images de modules managés sont chargées.  
  
 Pour les images exécutables, le chargeur du système d’exploitation appelle ensuite la fonction _ [CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) , quel que soit le point d’entrée spécifié dans le fichier exécutable. Pour les images d’assembly DLL, le chargeur appelle la fonction _ [cordllmain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) .  
  
 `_CorExeMain` ou `_CorDllMain` effectue les actions suivantes :  
  
- Initialise le CLR.  
  
- Localise le point d’entrée managé dans l’en-tête CLR de l’assembly.  
  
- Commence l’exécution.  
  
 Le chargeur appelle la fonction [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) lorsque les images de modules managés sont déchargées. Toutefois, cette fonction n’exécute aucune action ; elle retourne simplement.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
