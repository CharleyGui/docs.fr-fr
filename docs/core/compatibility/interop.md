---
title: Modifications avec rupture d’interopérabilité
description: Répertorie les dernières modifications apportées à l’interopérabilité dans .NET Core et .NET 5,0 et versions ultérieures.
ms.date: 06/23/2020
ms.openlocfilehash: a38fb1837e565be33f8ae1119480c8f1ae848ab0
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91438036"
---
# <a name="interop-breaking-changes"></a>Modifications avec rupture d’interopérabilité

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | :-: |
| [La conversion du wrapper RCW en `InterfaceIsIInspectable` interface lève PlatformNotSupportedException](#casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception) | 5.0 |
| [Pas de détection de suffixe A/W sur les plateformes non-Windows](#no-aw-suffix-probing-on-non-windows-platforms) | 5.0 |
| [La prise en charge intégrée de WinRT est supprimée de .NET](#built-in-support-for-winrt-is-removed-from-net) | 5.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [casting-rcw-to-inspectable-interface-throws-exception](../../../includes/core-changes/interop/5.0/casting-rcw-to-inspectable-interface-throws-exception.md)]

***

[!INCLUDE [function-suffix-pinvoke](../../../includes/core-changes/interop/5.0/function-suffix-pinvoke.md)]

***

[!INCLUDE [built-in-support-for-winrt-removed](~/includes/core-changes/interop/5.0/built-in-support-for-winrt-removed.md)]

***
