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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7421e0d0e1a1f0e1a5fbe0d0eb7d5a0ab2a48b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796420"
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
|`IIdentityAuthority::CreateDefinition`|Obtient un pointeur vers une nouvelle `IDefinitionIdentity` instance de qui représente l’objet de code dans l’étendue actuelle.|
|`IIdentityAuthority::CreateReference`|Obtient un pointeur vers une nouvelle `IReferenceIdentity` instance de qui représente l’objet de code dans l’étendue actuelle.|
|`IIdentityAuthority::DefinitionToText`|Obtient une version de chaîne mise en forme `IDefinitionIdentity`du spécifié.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Remplit la mémoire tampon de caractères larges spécifiée avec une version de chaîne du `IDefinitionIdentity`spécifié.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Obtient une valeur qui indique si les instances `IDefinitionIdentity` et `IReferenceIdentity` spécifiées font référence au même objet de code.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Obtient une valeur qui indique si les chaînes spécifiées font référence au même objet de code.|
|`IIdentityAuthority::GenerateDefinitionKey`|Obtient un pointeur vers une clé de chaîne nouvellement créée pour le `IDefinitionIdentity`spécifié.|
|`IIdentityAuthority::GenerateReferenceKey`|Obtient un pointeur vers une clé de chaîne nouvellement créée pour le `IReferenceIdentity`spécifié.|
|`IIdentityAuthority::HashDefinition`|Obtient une valeur de hachage pour le `IDefinitionIdentity`spécifié.|
|`IIdentityAuthority::HashReference`|Obtient une valeur de hachage pour le `IReferenceIdentity`spécifié.|
|`IIdentityAuthority::ReferenceToText`|Obtient une version de chaîne mise en forme `IReferenceIdentity`du spécifié.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Remplit la mémoire tampon de caractères larges spécifiée avec une version de chaîne du `IReferenceIdentity`spécifié.|
|`IIdentityAuthority::TextToDefinition`|Obtient un pointeur d’interface vers `IDefinitionIdentity` une instance générée à partir de la chaîne mise en forme spécifiée.|
|`IIdentityAuthority::TextToReference`|Obtient un pointeur d’interface vers `IReferenceIdentity` une instance générée à partir de la chaîne mise en forme spécifiée.|

## <a name="requirements"></a>Configuration requise

**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).

**En-tête :** Isolation. h

**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Interfaces de fusion](fusion-interfaces.md)
