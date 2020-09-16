---
ms.openlocfilehash: 97870553d4ec66a569ba63cd945639b03bbbd6df
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539466"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a>Kestrel : les versions de protocole TLS prises en charge par défaut ont été modifiées

Kestrel utilise désormais les versions de protocole TLS par défaut du système au lieu de restreindre les connexions aux protocoles TLS 1,1 et TLS 1,2 comme précédemment.

Cette modification permet :

* TLS 1,3 à utiliser par défaut dans les environnements qui le prennent en charge.
* TLS 1,0 à utiliser dans certains environnements (tels que Windows Server 2016 par défaut), ce qui n’est généralement [pas souhaitable](/security/engineering/solving-tls1-problem).

Pour plus d’informations, consultez émettre [dotnet/aspnetcore # 22563](https://github.com/dotnet/aspnetcore/issues/22563).

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 6

#### <a name="old-behavior"></a>Ancien comportement

Kestrel a demandé que les connexions utilisent TLS 1,1 ou TLS 1,2 par défaut.

#### <a name="new-behavior"></a>Nouveau comportement

Kestrel permet au système d’exploitation de choisir le meilleur protocole à utiliser et de bloquer les protocoles non sécurisés. <xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> la valeur par défaut est à la `SslProtocols.None` place de `SslProtocols.Tls12 | SslProtocols.Tls11` .

#### <a name="reason-for-change"></a>Motif de modification

La modification a été apportée pour prendre en charge les versions TLS 1,3 et futures par défaut dès qu’elles sont disponibles.

#### <a name="recommended-action"></a>Action recommandée

À moins que votre application ait une raison spécifique de ne pas le faire, vous devez utiliser les nouvelles valeurs par défaut. Vérifiez que votre système est configuré pour n’autoriser que les protocoles sécurisés.

Pour désactiver les anciens protocoles, effectuez l’une des actions suivantes :

* Désactivez les protocoles plus anciens, tels que TLS 1,0, à l’ensemble du système avec les [instructions Windows](../../../../docs/framework/network-programming/tls.md#configuring-schannel-protocols-in-the-windows-registry). Elle est actuellement activée par défaut sur toutes les versions de Windows.
* Sélectionnez manuellement les protocoles que vous souhaitez prendre en charge dans le code comme suit :

    ```csharp
    using System.Security.Authentication;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

Malheureusement, il n’existe aucune API pour exclure des protocoles spécifiques.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
