---
title: 'Procédure : configurer un service WCF hébergé par IIS avec SSL'
description: Découvrez comment configurer un service WCF hébergé par IIS pour utiliser la sécurité de transport HTTP, qui requiert un certificat inscrit auprès d’IIS.
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 8dc4692863d93e407a122c0ba93ae38323b8b213
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245256"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a>Procédure : configurer un service WCF hébergé par IIS avec SSL
Cette rubrique décrit comment installer un service WCF hébergé par IIS pour utiliser la sécurité de transport HTTP. La sécurité de transport HTTP requiert un certificat SSL à enregistrer avec IIS. Si vous n’avez pas de certificat SSL, vous pouvez utiliser IIS pour générer un certificat de test. Vous devez ensuite ajouter une liaison SSL au site web et configurer les propriétés d’authentification du site web. Enfin, vous devez configurer le service WCF pour utiliser HTTPS.  
  
### <a name="creating-a-self-signed-certificate"></a>Création d'un certificat auto-signé  
  
1. Ouvrez le Gestionnaire des services IIS (inetmgr.exe), puis choisissez le nom de votre ordinateur dans l’arborescence à gauche. Du côté droit de l'écran, sélectionnez Certificats de serveur.  
  
     ![Écran d'accueil du Gestionnaire des services IIS](media/mg-inetmgrhome.jpg "mg_INetMgrHome")  
  
2. Dans la fenêtre certificats de serveur, cliquez sur **créer un certificat auto-signé....** Lien.  
  
     ![Création d’un certificat auto&#45;signé avec IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")  
  
3. Entrez un nom convivial pour le certificat auto-signé, puis cliquez sur **OK**.  
  
     ![Boîte de dialogue créer un certificat auto&#45;signé](media/mg-mycert.jpg "mg_MyCert")  
  
     Les détails du certificat auto-signé que vous venez de créer s’affichent maintenant dans la fenêtre **certificats de serveur** .  
  
     ![Fenêtre Certificat de serveur](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")  
  
     Le certificat généré est installé dans le magasin d'Autorités de certification racines de confiance.  
  
### <a name="add-ssl-binding"></a>Ajouter une liaison SSL  
  
1. Toujours dans Internet Information Services Manager, développez le dossier **sites** , puis le dossier **site Web par défaut** dans l’arborescence sur le côté gauche de l’écran.  
  
2. Cliquez sur **liaisons....** Dans la section **actions** dans la partie supérieure droite de la fenêtre.  
  
     ![Ajout d'une liaison SSL](media/mg-addsslbinding.jpg "mg_AddSSLBinding")  
  
3. Dans la fenêtre liaisons de sites, cliquez sur le bouton **Ajouter** .  
  
     ![Boîte de dialogue Liaisons du site](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")  
  
4. Dans la boîte de dialogue **Ajouter la liaison de site** , sélectionnez HTTPS pour le type et le nom convivial du certificat auto-signé que vous venez de créer.  
  
     ![Exemple de liaison de site](media/mg-mycertbinding.jpg "mg_MyCertBinding")  
  
### <a name="configure-virtual-directory-for-ssl"></a>Configurer le répertoire virtuel pour SSL  
  
1. Toujours dans le Gestionnaire des services IIS, sélectionnez le répertoire virtuel qui contient votre service sécurisé WCF.  
  
2. Dans le volet central de la fenêtre, sélectionnez **Paramètres SSL** dans la section IIS.  
  
     ![Paramètres SSL pour le répertoire virtuel](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")  
  
3. Dans le volet Paramètres SSL, activez la case à cocher **exiger SSL** , puis cliquez sur le lien **appliquer** dans la section **actions** sur le côté droit de l’écran.  
  
     ![Paramètres SSL pour le répertoire virtuel](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")  
  
### <a name="configure-wcf-service-for-http-transport-security"></a>Configurer le service WCF pour la sécurité de transport HTTP  
  
1. Dans le fichier web.config du service WCF, configurez la liaison HTTP pour utiliser la sécurité de transport, comme indiqué dans le code XML suivant.  
  
    ```xml  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
    </bindings>  
    ```  
  
2. Spécifiez votre service et point de terminaison de service comme indiqué dans le code XML suivant.  
  
    ```xml  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
    </services>  
    ```  
  
## <a name="example"></a>Exemple  
 Voici un exemple complet d'un fichier web.config pour un service WCF utilisant la sécurité de transport HTTP.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
  <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement dans les services IIS (Internet Information Services)](hosting-in-internet-information-services.md)
- [Instructions relatives à l'hébergement dans les Services Internet (IIS)](../samples/internet-information-service-hosting-instructions.md)
- [Meilleures pratiques pour l'hébergement dans Internet Information Services](internet-information-services-hosting-best-practices.md)
- [IIS Hosting Using Inline Code](../samples/iis-hosting-using-inline-code.md)
