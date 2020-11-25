---
title: 'Modification avec rupture : HttpSys : la renégociation de certificat client est désactivée par défaut'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé HttpSys : renégociation de certificat client désactivée par défaut'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 796989e1a21e3cb206d081e4fe8f79630121dc84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760839"
---
# <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a>HttpSys : la renégociation de certificat client est désactivée par défaut

L’option permettant de renégocier une connexion et de demander un certificat client a été désactivée par défaut. Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181).

## <a name="version-introduced"></a>Version introduite

ASP.NET Core 5,0

## <a name="old-behavior"></a>Ancien comportement

La connexion peut être renégociée pour demander un certificat client.

## <a name="new-behavior"></a>Nouveau comportement

Les certificats clients ne peuvent être demandés que lors de la négociation de connexion initiale. Pour plus d’informations, consultez requête de tirage [dotnet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162).

## <a name="reason-for-change"></a>Motif de modification

La renégociation a entraîné un certain nombre de problèmes de performances et de blocage. Il n’est pas non plus pris en charge dans HTTP/2. Pour plus de contexte lorsque l’option de contrôle de ce comportement a été introduite dans ASP.NET Core 3,1, consultez émettre [dotnet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806).

## <a name="recommended-action"></a>Action recommandée

Les applications qui requièrent des certificats clients doivent utiliser *netsh.exe* pour affecter la valeur `clientcertnegotiation` à l’option `enabled` . Pour plus d’informations, consultez [commandes netsh http](/windows-server/networking/technologies/netsh/netsh-http).

Si vous souhaitez que les certificats clients soient activés uniquement pour certaines parties de votre application, consultez les instructions à la page [certificats clients facultatifs](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).

Si vous avez besoin de l’ancien comportement de renégociation, définissez `HttpSysOptions.ClientCertificateMethod` sur l’ancienne valeur `ClientCertificateMethod.AllowRenegotiate` . Cela n’est pas recommandé pour les raisons indiquées ci-dessus et dans le guide lié.

## <a name="affected-apis"></a>API affectées

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
