---
title: 'Procédure : configurer le traçage réseau'
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
ms.openlocfilehash: dc9b6b5399063026c0bbe5735964ed42a21168fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048371"
---
# <a name="how-to-configure-network-tracing"></a>Procédure : configurer le traçage réseau
Le fichier de configuration de l'application ou de l'ordinateur contient les paramètres qui déterminent le format et le contenu des traces réseau. Avant d'effectuer cette procédure, assurez-vous que le traçage est activé. Pour plus d’informations sur l’activation du suivi, consultez [Activation du suivi réseau](enabling-network-tracing.md).  
  
 Le fichier de configuration de l’ordinateur, machine.config, est stocké dans le dossier %Windir%\Microsoft.NET\Framework dans le répertoire dans lequel Windows a été installé. Il y a un fichier machine.config distinct dans les dossiers sous %Windir%\Microsoft.NET\Framework pour chaque version de .NET Framework installée sur l’ordinateur (par exemple, C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config ou C:\Windows\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config).  
  
 Ces paramètres peuvent également être effectués dans le fichier de configuration de l'application, qui est prioritaire sur le fichier de configuration de votre ordinateur.  
  
### <a name="to-configure-network-tracing"></a>Pour configurer le traçage réseau  
  
- Ajoutez les lignes suivantes au fichier de configuration approprié. Les valeurs et les options de ces paramètres sont décrites dans les tableaux ci-dessous.  
  
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
  
 Lorsque vous ajoutez un nom au bloc `<switches>`, la sortie de trace inclut les informations de certaines méthodes associées au nom. Le tableau suivant décrit la sortie.  
  
|Name|Sortie de|  
|----------|-----------------|  
|`System.Net.Sockets`|Certaines méthodes publiques des classes <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient> et <xref:System.Net.Dns>|  
|`System.Net`|Certaines méthodes publiques des classes <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest> et <xref:System.Net.FtpWebResponse>, et les informations de débogage de SSL (les certificats non valides, la liste des émetteurs manquants et les erreurs de certificat client.)|  
|`System.Net.HttpListener`|Certaines méthodes publiques des classes <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest> et <xref:System.Net.HttpListenerResponse>.|  
|`System.Net.Cache`|Certaines méthodes privées et internes dans `System.Net.Cache`.|  
|`System.Net.Http`|Certaines méthodes publiques des classes <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler> et <xref:System.Net.Http.WebRequestHandler>.|  
|`System.Net.WebSockets.WebSocket`|Certaines méthodes publiques des classes <xref:System.Net.WebSockets.ClientWebSocket> et <xref:System.Net.WebSockets.WebSocket>.|  
  
 Les attributs répertoriés dans le tableau suivant configurent la sortie de trace.  
  
|Nom d'attribut|Valeur d'attribut|  
|--------------------|---------------------|  
|`Value`|Attribut <xref:System.String> requis. Définit les commentaires de la sortie. Les valeurs légitimes sont `Critical`, `Error`, `Verbose`, `Warning` et `Information`.<br /><br /> Cet attribut doit être défini sur l’élément \<add name> de l’élément \<switches> comme illustré dans l’exemple. Une exception est levée si cet attribut est défini sur l’élément \<source>.|  
|`maxdatasize`|Attribut <xref:System.Int32> facultatif. Définit le nombre maximal d'octets de données réseau incluses dans chaque trace de ligne. La valeur par défaut est 1024.<br /><br /> Cet attribut doit être défini sur l’élément \<source> comme illustré dans l’exemple. Une exception est levée si cet attribut est défini sur un élément sous l’élément \<switches>.|  
|`Tracemode`|Attribut <xref:System.String> facultatif. Définissez la valeur `includehex` pour afficher les traces de protocole au format hexadécimal et texte. Définissez la valeur `protocolonly` pour afficher uniquement du texte. La valeur par défaut est `includehex`.<br /><br /> Cet attribut doit être défini sur l’élément \<switches> comme illustré dans l’exemple. Une exception est levée si cet attribut est défini sur un élément sous l’élément \<source>.|  
  
## <a name="see-also"></a>Voir aussi

- [Interprétation du suivi réseau](interpreting-network-tracing.md)
- [Traçage réseau dans .NET Framework](network-tracing.md)
- [Activation du suivi réseau](enabling-network-tracing.md)
- [Suivi et instrumentation d’applications](../debug-trace-profile/tracing-and-instrumenting-applications.md)
