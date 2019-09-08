---
title: CreateHistoryReader, fonction
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2710d14d6e73879fd17a6b58659463ea205f2384
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795367"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader, fonction
Crée un lecteur d’historique pour le fichier spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a>Paramètres  
 `wzFilePath`  
 dans Chemin d’accès du fichier.  
  
 `ppHistoryReader`  
 à En cas de réussite, contient un pointeur vers le lecteur d’historique.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les codes d’erreur COM standard tels qu’ils sont définis dans WinError. h, en plus des valeurs décrites dans le tableau suivant.  
  
|Code de retour|Description|  
|-----------------|-----------------|  
|S_OK|Indique que la méthode s’est terminée avec succès.|  
|E_INVALIDARG|Indique que `wzFilePath` ou `ppHistoryReader` sont définis sur une référence null.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **Bibliothèque** Fusion.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de fusion](fusion-global-static-functions.md)
