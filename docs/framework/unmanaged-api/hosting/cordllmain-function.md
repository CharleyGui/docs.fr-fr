---
title: _CorDllMain, fonction
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
ms.openlocfilehash: 1b3ebcabc66ee7ca29245bb02d958be311bc65fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673694"
---
# <a name="_cordllmain-function"></a>\_CorDllMain fonction)

Initialise le common language runtime (CLR), localise le point d’entrée managé dans l’en-tête CLR de l’assembly de DLL et commence l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `hInst`  
 dans Handle d’instance du module chargé.  
  
 `dwReason`  
 dans Indique la raison pour laquelle la fonction de point d’entrée de la DLL est appelée. Ce paramètre peut avoir l’une des valeurs suivantes : DLL \_ PROCESS_ATTACH, \_ attachement de thread dll \_ , \_ attachement de thread dll \_ ou \_ \_ détachement de processus dll. Pour obtenir une description de ces valeurs, consultez la `DllMain` documentation du kit de développement Platform SDK.  
  
 `lpReserved`  
 [in] Inutilisé.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne `true` pour réussite et `false` si une erreur se produit.  
  
## <a name="remarks"></a>Remarques  

 Cette fonction est appelée par le chargeur du système d’exploitation pour les assemblys DLL. Pour les assemblys exécutables, le chargeur appelle à la place la fonction [ \_ du CORExeMain](corexemain-function.md) .  
  
 Le chargeur du système d’exploitation appelle cette méthode quel que soit le point d’entrée spécifié dans le fichier DLL.  
  
La `_CorDllMain` fonction est appelée directement par le chargeur du système d’exploitation.
  
 Pour plus d’informations, consultez la section Notes de la rubrique [ \_ CorValidateImage](corvalidateimage-function.md) .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../metadata/metadata-global-static-functions.md)
