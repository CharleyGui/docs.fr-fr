---
title: 'Modification avec rupture : MulticastOption. Group n’accepte pas de valeur null'
description: Découvrez la modification avec rupture dans .NET 5,0 où MulticastOption. Group n’accepte plus de valeur null.
ms.date: 08/18/2020
ms.openlocfilehash: 164ac8c2c8dd14f9e0758017e54eeb377f88a7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760927"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a>MulticastOption. Group n’accepte pas de valeur null

<xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> n’accepte plus la valeur `null` . Si vous affectez à la propriété la valeur `null` , une <xref:System.ArgumentNullException> exception est levée.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, vous pouvez affecter <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> à la propriété la valeur `null` . Si le <xref:System.Net.Sockets.MulticastOption> est passé par la suite à <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , le runtime lève une exception <xref:System.NullReferenceException> .

Dans .NET 5,0 et versions ultérieures, une <xref:System.ArgumentNullException> exception est levée si vous affectez à la propriété la valeur `null` .

## <a name="reason-for-change"></a>Motif de modification

Pour être cohérente avec les règles de conception de l’infrastructure, la propriété a été mise à jour pour lever une <xref:System.ArgumentNullException> si la valeur est `null` .

## <a name="recommended-action"></a>Action recommandée

Assurez-vous que vous n’affectez pas la valeur <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> `null` .

## <a name="affected-apis"></a>API affectées

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

### Category

Networking

-->
