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
ms.openlocfilehash: ff3103a46390c880a56ff443bfe20744f2ba0bfd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430685"
---
# <a name="getwin32resblob-method"></a>GetWin32ResBlob, méthode
Récupère l’objet blob de ressources Win32. Appelez cette méthode après avoir défini les options d’assembly.  
  
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
 Jeton de fichier utilisé pour récupérer le nom de fichier à utiliser lors de la construction de la ressource de version Win32  
  
 `fDll`  
 TRUE si le fichier est une DLL, false pour un EXE.  
  
 `pszIconFile`  
 Icône facultative à insérer dans l’objet blob de ressources.  
  
 `ppResBlob`  
 Reçoit l’objet blob de ressources.  
  
 `pcbResBlob`  
 Reçoit la taille de l’objet BLOB.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
