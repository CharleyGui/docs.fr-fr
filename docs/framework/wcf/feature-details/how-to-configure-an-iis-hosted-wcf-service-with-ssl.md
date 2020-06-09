---
title: 'Procédure : configurer un service WCF hébergé par IIS avec SSL'
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: fb3e87021c3dce1172250f33fd302916920af74d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597226"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="0f47e-102">Procédure : configurer un service WCF hébergé par IIS avec SSL</span><span class="sxs-lookup"><span data-stu-id="0f47e-102">How to: Configure an IIS-hosted WCF service with SSL</span></span>
<span data-ttu-id="0f47e-103">Cette rubrique décrit comment installer un service WCF hébergé par IIS pour utiliser la sécurité de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="0f47e-103">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="0f47e-104">La sécurité de transport HTTP requiert un certificat SSL à enregistrer avec IIS.</span><span class="sxs-lookup"><span data-stu-id="0f47e-104">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="0f47e-105">Si vous n’avez pas de certificat SSL, vous pouvez utiliser IIS pour générer un certificat de test.</span><span class="sxs-lookup"><span data-stu-id="0f47e-105">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="0f47e-106">Vous devez ensuite ajouter une liaison SSL au site web et configurer les propriétés d’authentification du site web.</span><span class="sxs-lookup"><span data-stu-id="0f47e-106">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="0f47e-107">Enfin, vous devez configurer le service WCF pour utiliser HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0f47e-107">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="0f47e-108">Création d'un certificat auto-signé</span><span class="sxs-lookup"><span data-stu-id="0f47e-108">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="0f47e-109">Ouvrez le Gestionnaire des services IIS (inetmgr.exe), puis choisissez le nom de votre ordinateur dans l’arborescence à gauche.</span><span class="sxs-lookup"><span data-stu-id="0f47e-109">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="0f47e-110">Du côté droit de l'écran, sélectionnez Certificats de serveur.</span><span class="sxs-lookup"><span data-stu-id="0f47e-110">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="0f47e-111">![Écran d'accueil du Gestionnaire des services IIS](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="0f47e-111">![IIS Manager Home Screen](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="0f47e-112">Dans la fenêtre certificats de serveur, cliquez sur **créer un certificat auto-signé....**</span><span class="sxs-lookup"><span data-stu-id="0f47e-112">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="0f47e-113">Lien.</span><span class="sxs-lookup"><span data-stu-id="0f47e-113">Link.</span></span>  
  
     <span data-ttu-id="0f47e-114">![Création d’un certificat auto&#45;signé avec IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="0f47e-114">![Creating a self&#45;signed certificate with IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="0f47e-115">Entrez un nom convivial pour le certificat auto-signé, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="0f47e-115">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="0f47e-116">![Boîte de dialogue créer un certificat auto&#45;signé](media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="0f47e-116">![Create Self&#45;Signed Certificate Dialog](media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="0f47e-117">Les détails du certificat auto-signé que vous venez de créer s’affichent maintenant dans la fenêtre **certificats de serveur** .</span><span class="sxs-lookup"><span data-stu-id="0f47e-117">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="0f47e-118">![Fenêtre Certificat de serveur](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="0f47e-118">![Server Certificate Window](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="0f47e-119">Le certificat généré est installé dans le magasin d'Autorités de certification racines de confiance.</span><span class="sxs-lookup"><span data-stu-id="0f47e-119">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="0f47e-120">Ajouter une liaison SSL</span><span class="sxs-lookup"><span data-stu-id="0f47e-120">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="0f47e-121">Toujours dans Internet Information Services Manager, développez le dossier **sites** , puis le dossier **site Web par défaut** dans l’arborescence sur le côté gauche de l’écran.</span><span class="sxs-lookup"><span data-stu-id="0f47e-121">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="0f47e-122">Cliquez sur **liaisons....**</span><span class="sxs-lookup"><span data-stu-id="0f47e-122">Click the **Bindings….**</span></span> <span data-ttu-id="0f47e-123">Dans la section **actions** dans la partie supérieure droite de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="0f47e-123">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="0f47e-124">![Ajout d'une liaison SSL](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="0f47e-124">![Adding an SSL binding](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="0f47e-125">Dans la fenêtre liaisons de sites, cliquez sur le bouton **Ajouter** .</span><span class="sxs-lookup"><span data-stu-id="0f47e-125">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="0f47e-126">![Boîte de dialogue Liaisons du site](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="0f47e-126">![Site Bindings Dialog](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="0f47e-127">Dans la boîte de dialogue **Ajouter la liaison de site** , sélectionnez HTTPS pour le type et le nom convivial du certificat auto-signé que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="0f47e-127">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="0f47e-128">![Exemple de liaison de site](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="0f47e-128">![Site binding example](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="0f47e-129">Configurer le répertoire virtuel pour SSL</span><span class="sxs-lookup"><span data-stu-id="0f47e-129">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="0f47e-130">Toujours dans le Gestionnaire des services IIS, sélectionnez le répertoire virtuel qui contient votre service sécurisé WCF.</span><span class="sxs-lookup"><span data-stu-id="0f47e-130">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="0f47e-131">Dans le volet central de la fenêtre, sélectionnez **Paramètres SSL** dans la section IIS.</span><span class="sxs-lookup"><span data-stu-id="0f47e-131">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="0f47e-132">![Paramètres SSL pour le répertoire virtuel](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="0f47e-132">![SSL Settings for virtual directory](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="0f47e-133">Dans le volet Paramètres SSL, activez la case à cocher **exiger SSL** , puis cliquez sur le lien **appliquer** dans la section **actions** sur le côté droit de l’écran.</span><span class="sxs-lookup"><span data-stu-id="0f47e-133">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="0f47e-134">![Paramètres SSL pour le répertoire virtuel](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="0f47e-134">![Virtual directory SSL settings](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="0f47e-135">Configurer le service WCF pour la sécurité de transport HTTP</span><span class="sxs-lookup"><span data-stu-id="0f47e-135">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="0f47e-136">Dans le fichier web.config du service WCF, configurez la liaison HTTP pour utiliser la sécurité de transport, comme indiqué dans le code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="0f47e-136">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
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
  
2. <span data-ttu-id="0f47e-137">Spécifiez votre service et point de terminaison de service comme indiqué dans le code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="0f47e-137">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0f47e-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="0f47e-138">Example</span></span>  
 <span data-ttu-id="0f47e-139">Voici un exemple complet d'un fichier web.config pour un service WCF utilisant la sécurité de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="0f47e-139">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0f47e-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f47e-140">See also</span></span>

- [<span data-ttu-id="0f47e-141">Hébergement dans les services IIS (Internet Information Services)</span><span class="sxs-lookup"><span data-stu-id="0f47e-141">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="0f47e-142">Instructions relatives à l'hébergement dans les Services Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="0f47e-142">Internet Information Service Hosting Instructions</span></span>](../samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="0f47e-143">Meilleures pratiques pour l'hébergement dans Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="0f47e-143">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="0f47e-144">IIS Hosting Using Inline Code</span><span class="sxs-lookup"><span data-stu-id="0f47e-144">IIS Hosting Using Inline Code</span></span>](../samples/iis-hosting-using-inline-code.md)
