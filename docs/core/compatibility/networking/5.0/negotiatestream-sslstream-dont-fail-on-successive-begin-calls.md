---
title: 'Modification avec rupture : NegotiateStream et SslStream autorisent les opérations Begin successives'
description: Découvrez la modification avec rupture dans .NET 5,0 où les cas d’erreur sur les flux de sécurité sont gérés différemment, et les appels successifs à BeginAuthenticateAsServer ou BeginAuthenticateAsClient peuvent ne plus échouer.
ms.date: 10/18/2020
ms.openlocfilehash: e0226d0f5586efca050ca3497ca1490fa21fd943
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760924"
---
# <a name="negotiatestream-and-sslstream-allow-successive-begin-operations"></a>NegotiateStream et SslStream autorisent les opérations Begin successives

Les cas d’erreur sur les flux de sécurité sont gérés différemment, et les appels successifs à `BeginAuthenticateAsServer` ou `BeginAuthenticateAsClient` peuvent ne plus échouer.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, l’appel de ou, de manière `BeginAuthenticateAsServer` `BeginAuthenticateAsClient` consécutive, sans commencer `EndAuthenticateAsServer` par appeler ou `EndAuthenticateAsClient` engendre un <xref:System.NotSupportedException> . À compter de .NET 5,0, les appels successifs à `BeginAuthenticateAsServer` ou `BeginAuthenticateAsClient` n’aboutissent plus à un <xref:System.NotSupportedException> , car ces API sont soutenus par une <xref:System.Threading.Tasks.Task> implémentation basée sur.

## <a name="reason-for-change"></a>Motif de modification

Le basculement de l’implémentation interne du modèle de programmation asynchrone (APM) vers basé sur repose sur les <xref:System.Threading.Tasks.Task> performances et réduit la complexité du code.

## <a name="recommended-action"></a>Action recommandée

Aucune action n’est requise de la part du développeur.

## <a name="affected-apis"></a>API affectées

- <xref:System.Net.Security.SslStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.SslStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A?displayProperty=fullName>
- <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.SslStream.BeginAuthenticateAsClient`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer`
- `Overload:M:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient`

### Category

Networking

-->
