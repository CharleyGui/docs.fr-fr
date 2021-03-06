---
title: 'Modification avec rupture : les API System. Security. Cryptography ne sont pas prises en charge sur le webassembly éblouissant'
description: Découvrez les modifications avec rupture dans .NET 5,0 où les API de chiffrement lèvent une exception lorsqu’elles sont exécutées sur un navigateur.
ms.date: 09/16/2020
ms.openlocfilehash: ec10fa777e91f641b5582378830536a0cfa8dd72
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760887"
---
# <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a>API System. Security. Cryptography non prises en charge sur le webassembly éblouissant

<xref:System.Security.Cryptography> Les API lèvent une <xref:System.PlatformNotSupportedException> au moment de l’exécution lorsqu’elles sont exécutées sur un navigateur.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, la plupart des <xref:System.Security.Cryptography> API ne sont pas disponibles pour les applications Webassembly éblouissantes. À compter de .NET 5,0, les applications de l’assembly Web éblouissant ciblent la surface d’exposition complète de l’API .NET 5. Toutefois, toutes les API .NET 5 ne sont pas prises en charge en raison des contraintes du bac à sable (sandbox). Dans .NET 5,0 et versions ultérieures, les API non prises en charge <xref:System.Security.Cryptography> lèvent une <xref:System.PlatformNotSupportedException> lorsqu’elles s’exécutent sur webassembly.

> [!TIP]
> L' [Analyseur de compatibilité](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) de la plateforme signale tous les appels aux API affectées lorsque vous générez un projet qui prend en charge la plateforme du navigateur. Cet analyseur s’exécute par défaut dans les applications .NET 5,0 et ultérieures.

## <a name="reason-for-change"></a>Motif de modification

Microsoft n’est pas en mesure d’envoyer OpenSSL comme dépendance dans la configuration de l’assembly éblouissant. Nous avons tenté de contourner ce contournement en tentant de s’intégrer à l’API du navigateur `SubtleCrypto` . Malheureusement, il nécessitait des modifications d’API importantes qui rendaientait trop difficile l’intégration.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Il n’existe aucune solution de contournement pour l’instant.

## <a name="affected-apis"></a>API affectées

Toutes les <xref:System.Security.Cryptography?displayProperty=fullName> API sauf les suivantes :

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

### Affected APIs

- `T:System.Security.Cryptography`

### Category

- ASP.NET Core
- Cryptography

-->
