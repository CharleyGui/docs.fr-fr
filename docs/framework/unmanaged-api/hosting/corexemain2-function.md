---
title: _CorExeMain2, fonction
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
ms.openlocfilehash: 8202fe4ec3ae6ef96440f203c5aea6db84744a72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616578"
---
# <a name="_corexemain2-function"></a>_CorExeMain2, fonction
Exécute le point d’entrée dans le code mappé en mémoire spécifié. Cette fonction est appelée par le chargeur du système d’exploitation.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pUnmappedPE`  
 dans Pointeur vers le code mappé en mémoire.  
  
 `cUnmappedPE`  
 dans Le nombre d’éléments `pUnmappedPE` peut contenir.  
  
 `pImageNameIn`  
 dans Pointeur vers le nom de l’image exécutable.  
  
 `pLoadersFileName`  
 dans Nom du fichier de chargeur.  
  
 `pCmdLine`  
 dans Paramètres de ligne de commande, le cas échéant.  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../metadata/metadata-global-static-functions.md)
