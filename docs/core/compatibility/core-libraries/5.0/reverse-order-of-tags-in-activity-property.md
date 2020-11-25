---
title: 'Modification avec rupture : ordre des balises dans Activity. les balises sont inversées'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où Activity. Tags stocke désormais les éléments dans la liste en fonction de l’ordre dans lequel ils sont ajoutés.
ms.date: 11/01/2020
ms.openlocfilehash: 1ff14dc1a4f7a0bf8cf9e79f3750b819f4d4a5ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760984"
---
# <a name="order-of-tags-in-activitytags-is-reversed"></a>Ordre des balises dans Activity. les balises sont inversées

<xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stocke désormais les éléments dans la liste en fonction de l’ordre dans lequel ils sont ajoutés, c’est-à-dire que le premier élément ajouté est tout d’abord dans la liste. Cette modification a été apportée pour correspondre à la [spécification des attributs OpenTelemetry](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stocke les éléments dans l’ordre inverse à partir duquel ils sont ajoutés. Autrement dit, le premier élément ajouté est le dernier de la liste. À compter de .NET 5,0, l’ordre des éléments est inversé et le premier élément ajouté est toujours en premier dans la liste.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Si votre application dépend de l’ordre de la <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> liste et que vous effectuez une mise à niveau vers .net 5,0 ou une version ultérieure, vous devez modifier cette partie de votre code.

## <a name="affected-apis"></a>API affectées

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
