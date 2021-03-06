---
title: Sécurité de transport avec l'authentification par certificat
description: En savoir plus sur la façon dont WFC utilise les certificats pour l’authentification serveur et client lors de l’utilisation de la sécurité de transport.
ms.date: 03/30/2017
dev_langs:
- csharp
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: d3f2a10bb6b355e82f94b8cc793c93ce4634c7d2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251826"
---
# <a name="transport-security-with-certificate-authentication"></a>Sécurité de transport avec l'authentification par certificat

Cet article décrit l’utilisation de certificats X. 509 pour l’authentification serveur et client lors de l’utilisation de la sécurité de transport. Pour plus d’informations sur les certificats X.509, consultez [Certificats de clé publique X.509](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). Les certificats doivent être émis par une autorité de certification, qui est souvent un émetteur de certificats tiers. Dans un domaine Windows Server, les services de certificats Active Directory peuvent être utilisés pour émettre des certificats pour les ordinateurs clients figurant sur le domaine. Dans ce scénario, le service est hébergé sous Internet Information Services (IIS) qui est configuré avec SSL (Secure Sockets Layer). Le service est configuré avec un certificat SSL (X.509) pour permettre aux clients de vérifier l'identité du serveur. Le client est également configuré avec un certificat X.509 qui permet au service de vérifier l'identité du client. Le certificat du serveur doit être approuvé par le client et le certificat du client doit être approuvé par le serveur. La façon dont le service et le client vérifie l’identité de l’autre de manière réelle n’entre pas dans le cadre de cet article. Pour plus d’informations, consultez [signature numérique](https://en.wikipedia.org/wiki/Digital_signature) sur Wikipédia.
  
 Ce scénario implémente un modèle de message de demande/réponse comme illustré dans le schéma suivant.  
  
 ![Transfert sécurisé à l’aide de certificats](media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")  
  
 Pour plus d’informations sur l’utilisation d’un certificat avec un service, consultez [utilisation des certificats](working-with-certificates.md) et [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md). Le tableau suivant décrit les différentes caractéristiques du scénario.  
  
|Caractéristique|Description|  
|--------------------|-----------------|  
|Mode de sécurité|Transport|  
|Interopérabilité|Avec les clients de service Web et les services existants.|  
|Authentification (serveur)<br /><br /> Authentification (client)|Oui (à l’aide d’un certificat SSL)<br /><br /> Oui (à l'aide d'un certificat X.509)|  
|Intégrité des données|Oui|  
|Confidentialité des données|Oui|  
|Transport|HTTPS|  
|Liaison|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a>Configuration du service  

 Puisque le service dans ce scénario est hébergé sous IIS, il est configuré à l'aide d'un fichier web.config. La configuration Web suivante illustre comment configurer le <xref:System.ServiceModel.WSHttpBinding> pour utiliser la sécurité de transport et les informations d'identification du client X.509.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a>Configuration du client  

 Le client peut être configuré en code ou dans un fichier app.config. L'exemple suivant indique comment configurer le client en code.  
  
```csharp
// Create the binding.  
var myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.
var ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
var cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 Vous pouvez aussi configurer le client dans un fichier app.config, comme indiqué dans l'exemple suivant :  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Présentation de la sécurité](security-overview.md)
- [Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))
