---
title: 'Procédure : utiliser le fournisseur de rôle du Gestionnaire d’autorisations ASP.NET avec un service'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 4a92c9db000b703f4fdab7c34e5359de74b0228d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90545602"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="0ae3b-102">Procédure : utiliser le fournisseur de rôle du Gestionnaire d’autorisations ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="0ae3b-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="0ae3b-103">Quand ASP.NET héberge un service Web, vous pouvez intégrer le gestionnaire d’autorisations dans l’application pour fournir une autorisation au service.</span><span class="sxs-lookup"><span data-stu-id="0ae3b-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="0ae3b-104">Le Gestionnaire d'autorisations permet à un développeur d'applications de définir des opérations individuelles qui peuvent être regroupées pour former des tâches.</span><span class="sxs-lookup"><span data-stu-id="0ae3b-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="0ae3b-105">Un administrateur peut autoriser ensuite que les rôles exécutent des tâches spécifiques ou des opérations individuelles.</span><span class="sxs-lookup"><span data-stu-id="0ae3b-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="0ae3b-106">Le Gestionnaire d’autorisations fournit un outil d’administration sous la forme d’un composant logiciel enfichable MMC (Microsoft Management Console) pour gérer des rôles, des tâches, des opérations et des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="0ae3b-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="0ae3b-107">Les administrateurs configurent un magasin de stratégie du Gestionnaire d'autorisations dans un fichier XML, Active Directory, ou dans un magasin Active Directory en mode application (ADAM).</span><span class="sxs-lookup"><span data-stu-id="0ae3b-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="0ae3b-108">Le gestionnaire d’autorisations est intégré à l’application en configurant le fournisseur de rôle ASP.NET du gestionnaire d’autorisations pour l’application ASP.NET qui héberge le service Web.</span><span class="sxs-lookup"><span data-stu-id="0ae3b-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="0ae3b-109">Comme les autres fournisseurs de rôle ASP.NET, le fournisseur de rôle ASP.NET du gestionnaire d’autorisations est configuré à l’aide de l' `providers` élément <>.</span><span class="sxs-lookup"><span data-stu-id="0ae3b-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="0ae3b-110">L'exemple de code suivant représente une partie d'un fichier de configuration pour un service Web qui intègre le Gestionnaire d'autorisations dans l'application.</span><span class="sxs-lookup"><span data-stu-id="0ae3b-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="0ae3b-111">Pour plus d’informations sur l’intégration d’un fournisseur de rôle ASP.NET à une application WCF, consultez [Comment : utiliser le fournisseur de rôles ASP.net avec un service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="0ae3b-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="0ae3b-112">Pour plus d’informations sur l’utilisation du gestionnaire d’autorisations avec ASP.NET, consultez [procédure : utiliser le gestionnaire d’autorisations (AzMan) avec ASP.NET 2,0](/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="0ae3b-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae3b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ae3b-113">See also</span></span>

- [<span data-ttu-id="0ae3b-114">Procédure : utiliser le fournisseur de rôle ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="0ae3b-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
