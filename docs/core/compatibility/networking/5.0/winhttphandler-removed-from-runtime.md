---
title: 'Modification avec rupture : WinHttpHandler supprimé du Runtime .NET'
description: Découvrez la modification avec rupture dans .NET 5,0 où WinHttpHandler a été supprimé du Runtime .NET.
ms.date: 10/18/2020
ms.openlocfilehash: f8b9910ade8d459133791a23704d624a91cc5dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760923"
---
# <a name="winhttphandler-removed-from-net-runtime"></a>WinHttpHandler supprimé du Runtime .NET

La `WinHttpHandler` classe a été supprimée de l’assembly *System.Net.Http.dll* . Il est désormais disponible uniquement en tant que [package NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)hors-bande (OOB).

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, la <xref:System.Net.Http.WinHttpHandler> classe est disponible dans le cadre des bibliothèques .net de base. À compter de .NET 5,0, la <xref:System.Net.Http.WinHttpHandler> classe est uniquement disponible en tant que [package NuGet](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)installé séparément.

## <a name="recommended-action"></a>Action recommandée

Installez le [package NuGet System .net. http. WinHttpHandler](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/). Ou, si vous n’avez pas besoin de fonctionnalités spécifiques à WinHTTP, utilisez à la <xref:System.Net.Http.SocketsHttpHandler> place.

## <a name="affected-apis"></a>API affectées

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

### Category

Networking

-->
