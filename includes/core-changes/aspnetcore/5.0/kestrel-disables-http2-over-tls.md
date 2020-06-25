---
ms.openlocfilehash: 92210f6becb5a5a43893ee0fd51ef51e2ddd7f8d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325223"
---
### <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a>Kestrel : HTTP/2 désactivé sur TLS sur des versions de Windows incompatibles

Pour activer HTTP/2 sur le protocole TLS (Transport Layer Security) sur Windows, deux conditions doivent être remplies :

- La prise en charge de la négociation de protocole de couche application (ALPN), disponible à partir de Windows 8.1 et de Windows Server 2012 R2.
- Un ensemble de chiffrements compatibles avec HTTP/2, disponible à partir de Windows 10 et Windows Server 2016.

Par conséquent, le comportement de Kestrel lorsque HTTP/2 sur TLS est configuré est devenu :

- Rétrograder à `Http1` et enregistrer un message au `Information` niveau lorsque [ListenOptions. HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols) a la valeur `Http1AndHttp2` . `Http1AndHttp2` est la valeur par défaut de `ListenOptions.HttpProtocols`.
- Lève une `NotSupportedException` lorsque `ListenOptions.HttpProtocols` a la valeur `Http2` .

Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 23068](https://github.com/dotnet/aspnetcore/issues/23068).

#### <a name="version-introduced"></a>Version introduite

ASP.NET Core 5,0 Preview 7

#### <a name="old-behavior"></a>Ancien comportement

Le tableau suivant décrit le comportement lorsque le protocole HTTP/2 sur TLS est configuré.

| Protocoles | Windows 7,<br />Windows Server 2008 R2,<br />ou version antérieure | Windows 8,<br />Windows Server 2012 | Windows 8.1<br />Windows Server 2012 R2 | Windows 10,<br />Windows Server 2016,<br />ou plus récent |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | Lever`NotSupportedException`                   | Erreur lors de la négociation TLS     | Erreur lors de la négociation TLS&ast;     | Aucune erreur |
| `Http1AndHttp2` | Rétrograder à`Http1`                    | Rétrograder à`Http1`     | Erreur lors de la négociation TLS&ast;     | Aucune erreur |

&ast;Configurez des suites de chiffrement compatibles pour activer ces scénarios.

#### <a name="new-behavior"></a>Nouveau comportement

Le tableau suivant décrit le comportement lorsque le protocole HTTP/2 sur TLS est configuré.

| Protocoles | Windows 7,<br />Windows Server 2008 R2,<br />ou version antérieure | Windows 8,<br />Windows Server 2012 | Windows 8.1<br />Windows Server 2012 R2 | Windows 10,<br />Windows Server 2016,<br />ou plus récent |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | Lever`NotSupportedException`                   | Lever`NotSupportedException`     | Lever `NotSupportedException`&ast;&ast;     | Aucune erreur |
| `Http1AndHttp2` | Rétrograder à`Http1`                    | Rétrograder à`Http1`     | Rétrograder à `Http1`&ast;&ast;     | Aucune erreur |

&ast;&ast;Configurez les suites de chiffrement compatibles et définissez le commutateur de contexte d’application `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` sur `true` pour activer ces scénarios.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification garantit que les erreurs de compatibilité pour HTTP/2 sur TLS sur des versions plus anciennes de Windows sont exposées le plus tôt et le plus clairement possible.

#### <a name="recommended-action"></a>Action recommandée

Assurez-vous que HTTP/2 sur TLS est désactivé sur les versions de Windows incompatibles. Windows 8.1 et Windows Server 2012 R2 ne sont pas compatibles, car ils n’ont pas les chiffrements nécessaires par défaut. Toutefois, il est possible de mettre à jour les paramètres de configuration de l’ordinateur pour utiliser les chiffrements compatibles HTTP/2. Pour plus d’informations, voir [suites de chiffrement TLS dans Windows 8.1](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1). Une fois configuré, vous devez activer HTTP/2 sur TLS sur Kestrel en définissant le commutateur de contexte d’application `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` . Par exemple :

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

Aucune prise en charge sous-jacente n’a changé. Par exemple, HTTP/2 sur TLS n’a jamais fonctionné sur Windows 8 ou Windows Server 2012. Cette modification modifie le mode de présentation des erreurs dans ces scénarios non pris en charge.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucune

<!--

#### Affected APIs

Not detectable via API analysis

-->
