---
title: SetManifestFile, méthode
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
ms.openlocfilehash: a4518e93db887dbdc4397636479be8bf5a705c2d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733722"
---
# <a name="setmanifestfile-method"></a>SetManifestFile, méthode

Vous permet de spécifier ou de réinitialiser le fichier manifeste que l’éditeur de liens utilise lorsqu’il crée l’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `pszFile`  
  
 Nom du fichier manifeste dont le contenu est placé dans l’objet blob de ressources Win32.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="remarks"></a>Remarques  

 Appelez-le avant de demander le Win32ResBlob. La valeur du `pszFile` paramètre est le nom du fichier manifeste dont le contenu est lu et placé dans les ressources Win32 avec l’ID de RT_MANIFEST. En cas d’appel à l’aide d’un paramètre de valeur NULL, tout manifeste précédemment lu est effacé. Cela permet à l’un de réinitialiser l’état de l’éditeur de liens à celui du temps d’initialisation.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert aLink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink3, interface](ialink3-interface.md)
- [API ALink](index.md)
- [IALink, interface](ialink-interface.md)
- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
