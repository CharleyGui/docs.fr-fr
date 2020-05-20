---
title: Modifications avec rupture de la globalisation
description: Répertorie les dernières modifications de la globalisation dans .NET Core.
ms.date: 04/07/2020
ms.openlocfilehash: 0c3367cb3515c6f473f53be6062b54f2e836b8c5
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702308"
---
# <a name="globalization-breaking-changes"></a>Modifications avec rupture de la globalisation

Les modifications avec rupture suivantes sont documentées sur cette page :

| Modification avec rupture | Version introduite |
| - | :-: |
| [Les API de globalisation utilisent des bibliothèques ICU sur Windows](#globalization-apis-use-icu-libraries-on-windows) | 5.0 |
| [StringInfo et TextElementEnumerator sont désormais conformes à UAX29](#stringinfo-and-textelementenumerator-are-now-uax29-compliant) | 5.0 |
| [Les paramètres régionaux « C » sont mappés aux paramètres régionaux invariants](#c-locale-maps-to-the-invariant-locale) | 3.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [icu-globalization-api](../../../includes/core-changes/globalization/5.0/icu-globalization-api.md)]

***

[!INCLUDE [uax29-compliant-grapheme-enumeration](../../../includes/core-changes/globalization/5.0/uax29-compliant-grapheme-enumeration.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE["C" locale maps to the invariant locale](~/includes/core-changes/globalization/3.0/c-locale-maps-to-invariant-locale.md)]

***
