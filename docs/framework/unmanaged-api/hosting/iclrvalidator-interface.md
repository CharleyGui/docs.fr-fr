---
title: ICLRValidator, interface
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
ms.openlocfilehash: d9ccd5c6c91b1ab2166ff40a0fb2048e15927d3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723946"
---
# <a name="iclrvalidator-interface"></a>ICLRValidator, interface

Fournit des méthodes pour valider des images exécutables portables (PE) et des erreurs de validation de rapport.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[FormatEventInfo, méthode](iclrvalidator-formateventinfo-method.md)|Obtient un message détaillé sur l’erreur de validation spécifiée.|  
|[Validate, méthode](iclrvalidator-validate-method.md)|Valide l’exécutable portable ou le langage MSIL (Microsoft Intermediate Language) dans le fichier spécifié.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** IValidator. idl, IValidator. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [ICLRErrorReportingManager, interface](iclrerrorreportingmanager-interface.md)
- [Interfaces d'hébergement](hosting-interfaces.md)
- [Coclasse CLRRuntimeHost](clrruntimehost-coclass.md)
