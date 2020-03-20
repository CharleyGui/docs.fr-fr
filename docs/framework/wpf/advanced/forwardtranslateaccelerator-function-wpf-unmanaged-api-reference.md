---
title: Fonction ForwardTranslateAccelerator - WPF non gestiond API référence
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: a0a01be3000dc53df7855cb74015ba1164206838
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186632"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>Fonction ForwardTranslateAccelerator (WPF Unmanaged API Reference)
Cette API prend en charge l’infrastructure de la Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement à partir de votre code.  
  
 Utilisé par l’infrastructure de la Windows Presentation Foundation (WPF) pour la gestion des fenêtres.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,
   VARIANT_BOOL appUnhandled  
)  
```  
  
## <a name="parameters"></a>Paramètres  
 pMsg  
 Un pointeur à un message.  
  
 appUnhandled  
 `true`lorsque l’application a déjà eu la chance de gérer le message d’entrée, mais ne l’a pas géré; autrement, `false`.  
  
## <a name="requirements"></a>Spécifications  
 **Plates-formes:** Voir [.NET Framework System Requirements](../../get-started/system-requirements.md).  
  
 **DLL:**  
  
 Dans le cadre .NET 3.0 et 3.5: PresentationHostDLL.dll  
  
 Dans le cadre .NET 4 et plus tard: PresentationHost_v0400.dll  
  
 **Version cadre .NET:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Informations de référence sur les API non managées WPF](wpf-unmanaged-api-reference.md)
