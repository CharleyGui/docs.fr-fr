---
title: 'Modification avec rupture : Socket. LocalEndPoint est mis à jour après l’appel de SendToAsync'
description: Découvrez la modification avec rupture dans .NET 5,0 où SendToAsync met à jour la valeur de la propriété de point de terminaison local à l’adresse locale du Socket.
ms.date: 10/18/2020
ms.openlocfilehash: 53d7da350eac6e65832012331044427fd90fe796
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760931"
---
# <a name="socketlocalendpoint-is-updated-after-calling-sendtoasync"></a>Socket. LocalEndPoint est mis à jour après l’appel de SendToAsync

<xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> met à jour la valeur de la <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> propriété avec l’adresse locale du Socket.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=nameWithType> ne modifie pas la valeur de la <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> propriété sur l’instance de Socket. À compter de .NET 5,0, lorsque <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> se termine avec succès, la valeur de <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> est l’adresse locale du socket lié implicitement. Ce nouveau comportement est cohérent avec le comportement de <xref:System.Net.Sockets.Socket.SendTo(System.Byte[],System.Net.EndPoint)> et <xref:System.Net.Sockets.Socket.BeginSendTo(System.Byte[],System.Int32,System.Int32,System.Net.Sockets.SocketFlags,System.Net.EndPoint,System.AsyncCallback,System.Object)> / <xref:System.Net.Sockets.Socket.EndSendTo(System.IAsyncResult)> .

## <a name="reason-for-change"></a>Motif de modification

Cette modification [corrige un bogue](https://github.com/dotnet/runtime/issues/915) et rend le comportement cohérent entre les `SendTo` variantes.

## <a name="recommended-action"></a>Action recommandée

Modifiez le code qui suppose que <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)> ne modifiera pas la valeur de <xref:System.Net.Sockets.Socket.LocalEndPoint?displayProperty=nameWithType> .

## <a name="affected-apis"></a>API affectées

- <xref:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Net.Sockets.Socket.SendToAsync(System.Net.Sockets.SocketAsyncEventArgs)`

### Category

Networking

-->
