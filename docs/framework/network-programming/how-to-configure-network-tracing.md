---
title: Guide pratique pour configurer le suivi réseau
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
ms.openlocfilehash: 06132509860b16d1e22cfdf7e3226c968d16b7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040642"
---
# <a name="how-to-configure-network-tracing"></a>Comment configurer le traçage du réseau

Le fichier de configuration de l'application ou de l'ordinateur contient les paramètres qui déterminent le format et le contenu des traces réseau. Avant d'effectuer cette procédure, assurez-vous que le traçage est activé. Pour plus d’informations, voir [Suivi du réseau Enable](enabling-network-tracing.md).

Le fichier de configuration de l’ordinateur, *machine.config*, est stocké dans le dossier *%windir%-Microsoft.NET-Framework.* Il existe un fichier *machine.config* séparé dans les dossiers sous *%windir%-Microsoft.NET-Framework* pour chaque version du cadre .NET installé sur l’ordinateur, par exemple:

- *C : 'WINDOWS’Microsoft.NET’Framework’v2.0.50727-Config-machine.config*
- *C : 'WINDOWS’Microsoft.NET’Framework64'v4.0.30319-Config-machine.config*

Ces paramètres peuvent également être effectués dans le fichier de configuration de l'application, qui est prioritaire sur le fichier de configuration de votre ordinateur.

## <a name="configure-network-tracing"></a>Configurer le traçage du réseau

Pour configurer le traçage du réseau, ajoutez les lignes suivantes au fichier de configuration approprié. Les valeurs et les options de ces paramètres sont décrites dans les tableaux ci-dessous.

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Net" tracemode="includehex" maxdatasize="1024">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Cache">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Http">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Sockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.WebSockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
   </sources>
    <switches>
      <add name="System.Net" value="Verbose"/>
      <add name="System.Net.Cache" value="Verbose"/>
      <add name="System.Net.Http" value="Verbose"/>
      <add name="System.Net.Sockets" value="Verbose"/>
      <add name="System.Net.WebSockets" value="Verbose"/>
    </switches>
    <sharedListeners>
      <add name="System.Net"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="network.log"
        traceOutputOptions="ProcessId, DateTime"
      />
    </sharedListeners>
    <trace autoflush="true"/>
  </system.diagnostics>
</configuration>
```

### <a name="trace-output-from-methods"></a>Sortie de trace des méthodes

Lorsque vous ajoutez un nom au bloc `<switches>`, la sortie de trace inclut les informations de certaines méthodes associées au nom. Le tableau suivant décrit la sortie :

|Nom|Sortie de|
|----------|-----------------|
|`System.Net.Sockets`|Quelques méthodes publiques <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener>de <xref:System.Net.Sockets.TcpClient>la <xref:System.Net.Dns> , , et les classes.|
|`System.Net`|Quelques méthodes publiques <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse>de <xref:System.Net.FtpWebRequest>la <xref:System.Net.FtpWebResponse> , , et les classes, et SSL débobli des informations (certificats invalides, liste d’émetteurs manquants, et erreurs de certificat client).|
|`System.Net.HttpListener`|Certaines méthodes publiques des classes <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest> et <xref:System.Net.HttpListenerResponse>.|
|`System.Net.Cache`|Certaines méthodes privées et internes dans `System.Net.Cache`.|
|`System.Net.Http`|Certaines méthodes publiques des classes <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler> et <xref:System.Net.Http.WebRequestHandler>.|
|`System.Net.WebSockets.WebSocket`|Certaines méthodes publiques des classes <xref:System.Net.WebSockets.ClientWebSocket> et <xref:System.Net.WebSockets.WebSocket>.|

### <a name="trace-output-attributes"></a>Attributs de sortie de trace

Les attributs énumérés dans le tableau suivant configurent la sortie de trace :

|Nom de l’attribut|Valeur d'attribut|
|--------------------|---------------------|
|`value`|Attribut <xref:System.String> requis. Définit les commentaires de la sortie. Les valeurs légitimes sont `Critical`, `Error`, `Verbose`, `Warning` et `Information`.<br /><br />Cet attribut doit être défini sur l’élément **add** de l’élément **commutateurs.** Une exception est projetée si cet attribut est défini sur l’élément **source.**<br/><br/>Exemple : `<add name="System.Net" value="Verbose"/>`|
|`maxdatasize`|Attribut <xref:System.Int32> facultatif. Définit le nombre maximal d'octets de données réseau incluses dans chaque trace de ligne. La valeur par défaut est 1024.<br /><br />Cet attribut doit être défini sur l’élément **source.** Une exception est projetée si cet attribut est défini sur un élément sous **l’élément des commutateurs.**<br/><br/>Exemple : `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|
|`tracemode`|Attribut <xref:System.String> facultatif. Définissez la valeur `includehex` pour afficher les traces de protocole au format hexadécimal et texte. Définissez la valeur `protocolonly` pour afficher uniquement du texte. La valeur par défaut est `includehex`.<br /><br />Cet attribut doit être défini sur l’élément **source.** Une exception est projetée si cet attribut est défini sur un élément sous **l’élément des commutateurs.**<br/><br/>Exemple : `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`|

## <a name="see-also"></a>Voir aussi

- [Interprétation du suivi réseau](interpreting-network-tracing.md)
- [Traçage réseau dans .NET Framework](network-tracing.md)
- [Activation du traçage réseau](enabling-network-tracing.md)
- [Traçage et instrumentation d'applications](../debug-trace-profile/tracing-and-instrumenting-applications.md)
