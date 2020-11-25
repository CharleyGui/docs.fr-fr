---
title: IAppIdAuthority, interface
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
ms.openlocfilehash: a344f2ab5d9a7aa92018c47ee7a162cd1721aeb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732110"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority, interface

Fournit des méthodes qui génèrent et comparent des clés pour les identités et les références d’application.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Obtient une valeur qui indique si les deux instances [IDefinitionAppId](idefinitionappid-interface.md) spécifiées sont égales. Vous pouvez passer la valeur de l’indicateur IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.|  
|`IAppIdAuthority::AreReferencesEqual`|Obtient une valeur qui indique si les deux instances [IReferenceAppId](ireferenceappid-interface.md) spécifiées sont égales. Vous pouvez passer la valeur de l’indicateur IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Obtient une valeur qui indique si les deux définitions de chaîne spécifiées sont égales. Vous pouvez passer la valeur de l’indicateur IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Obtient une valeur qui indique si les deux références de chaîne spécifiées sont égales. Vous pouvez passer la valeur de l’indicateur IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.|  
|`IAppIdAuthority::CreateDefinition`|Obtient un pointeur d’interface vers une instance nouvellement générée `IDefinitionAppId` qui représente l’assembly dans la portée actuelle.|  
|`IAppIdAuthority::CreateReference`|Obtient un pointeur d’interface vers un objet qui vient d’être créé `IReferenceAppId` et qui représente l’assembly dans l’étendue actuelle.|  
|`IAppIdAuthority::DefinitionToText`|Obtient une version de chaîne du spécifié `IDefinitionAppId` , à l’aide des valeurs d’indicateur spécifiées.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Obtient une valeur qui indique si le spécifié `IDefinitionAppId` et `IReferenceAppId` représente le même assembly.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Obtient une valeur qui indique si la chaîne de définition et la chaîne de référence spécifiées représentent le même assembly.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Obtient une clé de chaîne qui représente l' `IDefinitionAppId` instance spécifiée.|  
|`IAppIdAuthority::GenerateReferenceKey`|Obtient une clé de chaîne qui représente l' `IReferenceAppId` instance spécifiée.|  
|`IAppIdAuthority::HashDefinition`|Obtient une clé de hachage pour l' `IDefinitionAppId` instance spécifiée.|  
|`IAppIdAuthority::HashReference`|Obtient une clé de hachage pour l' `IReferenceAppId` instance spécifiée.|  
|`IAppIdAuthority::ReferenceToText`|Obtient une version de chaîne du spécifié `IReferenceAppId` , à l’aide des valeurs d’indicateur spécifiées.|  
|`IAppIdAuthority::TextToDefinition`|Obtient un pointeur d’interface vers une `IDefinitionAppId` instance de qui représente l’assembly référencé par la clé de chaîne spécifiée.|  
|`IAppIdAuthority::TextToReference`|Obtient un pointeur d’interface vers une `IReferenceAppId` instance de qui représente l’assembly référencé par la clé de chaîne spécifiée.|  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
