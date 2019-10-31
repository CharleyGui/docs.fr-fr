---
title: IIdentityAuthority, interface
ms.date: 03/30/2017
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
ms.openlocfilehash: 3e2d2335e37ced9139ea44092f10b19566894681
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127097"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority, interface

Gère les clés d’identité pour les objets de code.

## <a name="methods"></a>Méthodes

|Méthode|Description|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|Obtient une valeur qui indique si les deux instances de [IDefinitionIdentity](idefinitionidentity-interface.md) spécifiées sont égales.|
|`IIdentityAuthority::AreReferencesEqual`|Obtient une valeur qui indique si les deux instances [IReferenceIdentity](ireferenceidentity-interface.md) spécifiées sont égales.|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Obtient une valeur qui indique si les deux représentations d’identité de définition de chaîne spécifiées sont égales.|
|`IIdentityAuthority::AreTextualReferencesEqual`|Obtient une valeur qui indique si les deux représentations d’identité de référence de chaîne spécifiées sont égales.|
|`IIdentityAuthority::CreateDefinition`|Obtient un pointeur vers une nouvelle instance de `IDefinitionIdentity` qui représente l’objet de code dans la portée actuelle.|
|`IIdentityAuthority::CreateReference`|Obtient un pointeur vers une nouvelle instance de `IReferenceIdentity` qui représente l’objet de code dans la portée actuelle.|
|`IIdentityAuthority::DefinitionToText`|Obtient une version de chaîne mise en forme du `IDefinitionIdentity`spécifié.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Remplit la mémoire tampon de caractères larges spécifiée avec une version de chaîne du `IDefinitionIdentity`spécifié.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Obtient une valeur qui indique si le `IDefinitionIdentity` et les instances de `IReferenceIdentity` spécifiés font référence au même objet de code.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Obtient une valeur qui indique si les chaînes spécifiées font référence au même objet de code.|
|`IIdentityAuthority::GenerateDefinitionKey`|Obtient un pointeur vers une clé de chaîne nouvellement créée pour le `IDefinitionIdentity`spécifié.|
|`IIdentityAuthority::GenerateReferenceKey`|Obtient un pointeur vers une clé de chaîne nouvellement créée pour le `IReferenceIdentity`spécifié.|
|`IIdentityAuthority::HashDefinition`|Obtient une valeur de hachage pour le `IDefinitionIdentity`spécifié.|
|`IIdentityAuthority::HashReference`|Obtient une valeur de hachage pour le `IReferenceIdentity`spécifié.|
|`IIdentityAuthority::ReferenceToText`|Obtient une version de chaîne mise en forme du `IReferenceIdentity`spécifié.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Remplit la mémoire tampon de caractères larges spécifiée avec une version de chaîne du `IReferenceIdentity`spécifié.|
|`IIdentityAuthority::TextToDefinition`|Obtient un pointeur d’interface vers une instance de `IDefinitionIdentity` générée à partir de la chaîne mise en forme spécifiée.|
|`IIdentityAuthority::TextToReference`|Obtient un pointeur d’interface vers une instance de `IReferenceIdentity` générée à partir de la chaîne mise en forme spécifiée.|

## <a name="requirements"></a>spécifications

**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** Isolation. h

**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
