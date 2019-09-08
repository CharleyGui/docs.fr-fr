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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91ab2f71e7fb74f8e0e517b566d46d61c316ebe2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796841"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority, interface
Fournit des méthodes qui génèrent et comparent des clés pour les identités et les références d’application.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Obtient une valeur qui indique si les deux instances [IDefinitionAppId](idefinitionappid-interface.md) spécifiées sont égales. Vous pouvez passer la valeur d’indicateur IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.|  
|`IAppIdAuthority::AreReferencesEqual`|Obtient une valeur qui indique si les deux instances [IReferenceAppId](ireferenceappid-interface.md) spécifiées sont égales. Vous pouvez passer la valeur d’indicateur IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Obtient une valeur qui indique si les deux définitions de chaîne spécifiées sont égales. Vous pouvez passer la valeur d’indicateur IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Obtient une valeur qui indique si les deux références de chaîne spécifiées sont égales. Vous pouvez passer la valeur d’indicateur IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.|  
|`IAppIdAuthority::CreateDefinition`|Obtient un pointeur d’interface vers une instance `IDefinitionAppId` nouvellement générée qui représente l’assembly dans la portée actuelle.|  
|`IAppIdAuthority::CreateReference`|Obtient un pointeur d’interface vers un objet `IReferenceAppId` qui vient d’être créé et qui représente l’assembly dans l’étendue actuelle.|  
|`IAppIdAuthority::DefinitionToText`|Obtient une version de chaîne du spécifié `IDefinitionAppId`, à l’aide des valeurs d’indicateur spécifiées.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Obtient une valeur qui indique si le spécifié `IDefinitionAppId` et `IReferenceAppId` représente le même assembly.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Obtient une valeur qui indique si la chaîne de définition et la chaîne de référence spécifiées représentent le même assembly.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Obtient une clé de chaîne qui représente l' `IDefinitionAppId` instance spécifiée.|  
|`IAppIdAuthority::GenerateReferenceKey`|Obtient une clé de chaîne qui représente l' `IReferenceAppId` instance spécifiée.|  
|`IAppIdAuthority::HashDefinition`|Obtient une clé de hachage pour l' `IDefinitionAppId` instance spécifiée.|  
|`IAppIdAuthority::HashReference`|Obtient une clé de hachage pour l' `IReferenceAppId` instance spécifiée.|  
|`IAppIdAuthority::ReferenceToText`|Obtient une version de chaîne du spécifié `IReferenceAppId`, à l’aide des valeurs d’indicateur spécifiées.|  
|`IAppIdAuthority::TextToDefinition`|Obtient un pointeur d’interface vers `IDefinitionAppId` une instance de qui représente l’assembly référencé par la clé de chaîne spécifiée.|  
|`IAppIdAuthority::TextToReference`|Obtient un pointeur d’interface vers `IReferenceAppId` une instance de qui représente l’assembly référencé par la clé de chaîne spécifiée.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Isolation. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
