---
title: GetWin32ResBlob, méthode
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdc1ef6490f250ebe93b0482adf244adfc0ffd56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741782"
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob, méthode
Récupère le blob de ressources Win32. Appelez cette méthode après avoir défini les options d’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly.  
  
 `FileToken`  
 Jeton de fichier utilisé pour récupérer le nom de fichier à utiliser lors de la construction de la ressource de Version Win32  
  
 `fDll`  
 TRUE si le fichier est une DLL, false pour un fichier EXE.  
  
 `pszIconFile`  
 Icône facultative à insérer dans le blob de ressources.  
  
 `ppResBlob`  
 Reçoit le blob de ressources.  
  
 `pcbResBlob`  
 Reçoit la taille de l’objet blob.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Nécessite alink.h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
