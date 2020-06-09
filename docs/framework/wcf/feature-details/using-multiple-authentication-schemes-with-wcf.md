---
title: Utilisation de schémas d'authentification multiples avec WCF
ms.date: 03/30/2017
ms.assetid: f32a56a0-e2b2-46bf-a302-29e1275917f9
ms.openlocfilehash: 1874963573a6ec12939bd12b79574f1e2c889bfd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600216"
---
# <a name="using-multiple-authentication-schemes-with-wcf"></a><span data-ttu-id="af7ae-102">Utilisation de schémas d'authentification multiples avec WCF</span><span class="sxs-lookup"><span data-stu-id="af7ae-102">Using Multiple Authentication Schemes with WCF</span></span>
<span data-ttu-id="af7ae-103">WCF vous permet maintenant de spécifier plusieurs schémas d'authentification sur un seul point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="af7ae-103">WCF now allows you to specify multiple authentication schemes on a single endpoint.</span></span> <span data-ttu-id="af7ae-104">En outre les services hébergés sur le Web peuvent hériter leurs paramètres d'authentification directement d'IIS.</span><span class="sxs-lookup"><span data-stu-id="af7ae-104">Furthermore web hosted services can inherit their authentication settings directly from IIS.</span></span> <span data-ttu-id="af7ae-105">Les services auto-hébergés peuvent spécifier que les schémas d'authentification peuvent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="af7ae-105">Self-hosted services can specify what authentication schemes can be used.</span></span> <span data-ttu-id="af7ae-106">Pour plus d’informations sur la définition des paramètres d’authentification dans IIS, consultez [authentification IIS](https://go.microsoft.com/fwlink/?LinkId=232458)</span><span class="sxs-lookup"><span data-stu-id="af7ae-106">For more information about setting authentication settings in IIS, see [IIS Authentication](https://go.microsoft.com/fwlink/?LinkId=232458)</span></span>  
  
## <a name="iis-hosted-services"></a><span data-ttu-id="af7ae-107">Services hébergés IIS</span><span class="sxs-lookup"><span data-stu-id="af7ae-107">IIS-Hosted Services</span></span>  
 <span data-ttu-id="af7ae-108">Pour les services hébergés dans IIS, définissez les schémas d'authentification que vous souhaitez utiliser dans IIS.</span><span class="sxs-lookup"><span data-stu-id="af7ae-108">For IIS-hosted services, set the authentication schemes you wish to use in IIS.</span></span> <span data-ttu-id="af7ae-109">Ensuite, dans le fichier Web. config de votre service, dans votre configuration de liaison, spécifiez « InheritedFromHost » comme type de clientCredential, comme indiqué dans l’extrait de code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="af7ae-109">Then in your service’s web.config file, in your binding configuration specify clientCredential type as "InheritedFromHost" as shown in the following XML snippet:</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="af7ae-110">Vous pouvez spécifier que vous souhaitez qu’un sous-ensemble de schémas d’authentification soit utilisé avec votre service à l’aide de ServiceAuthenticationBehavior ou de l' \<serviceAuthenticationManager> élément.</span><span class="sxs-lookup"><span data-stu-id="af7ae-110">You can specify that you only want a subset of authentication schemes to be used with your service using the ServiceAuthenticationBehavior or the \<serviceAuthenticationManager> element.</span></span> <span data-ttu-id="af7ae-111">Lors de la configuration dans le code, utilisez ServiceAuthenticationBehavior comme indiqué dans l'extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="af7ae-111">When configuring this in code use the ServiceAuthenticationBehavior as shown in the following code snippet.</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="af7ae-112">Quand vous configurez cette configuration dans un fichier de configuration, utilisez l' \<serviceAuthenticationManager> élément comme indiqué dans l’extrait de code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="af7ae-112">When configuring this in a config file, use the \<serviceAuthenticationManager> element as shown in the following XML snippet.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="af7ae-113">De cette façon, seul un sous-ensemble des schémas d'authentification répertoriés ici est pris en compte pour l'application sur le point de terminaison de service, selon ce qui est sélectionné dans IIS.</span><span class="sxs-lookup"><span data-stu-id="af7ae-113">This will ensure that only a subset of the authentication schemes listed here will be considered for applying on the service endpoint, depending on what is selected in the IIS.</span></span> <span data-ttu-id="af7ae-114">Cela signifie qu'un développeur peut exclure l'authentification de base de la liste en l'omettant dans la liste serviceAuthenticationManager, et même si elle est activée dans IIS, elle ne sera pas appliquée sur le point de terminaison de service</span><span class="sxs-lookup"><span data-stu-id="af7ae-114">This means that a developer can exclude say Basic auth from the list by omitting it from the serviceAuthenticationManager listing and even if it is enabled in IIS, it will not be applied on the service endpoint</span></span>  
  
## <a name="self-hosted-services"></a><span data-ttu-id="af7ae-115">Services auto-hébergés</span><span class="sxs-lookup"><span data-stu-id="af7ae-115">Self-Hosted Services</span></span>  
 <span data-ttu-id="af7ae-116">Les services auto-hébergés sont configurés un peu différemment étant donné l'absence d'IIS pour hériter des paramètres.</span><span class="sxs-lookup"><span data-stu-id="af7ae-116">Self-hosted services are configured a bit differently since there is no IIS to inherit settings from.</span></span> <span data-ttu-id="af7ae-117">Ici, vous utilisez l' \<serviceAuthenticationManager> élément ou ServiceAuthenticationBehavior pour spécifier les paramètres d’authentification qui seront hérités.</span><span class="sxs-lookup"><span data-stu-id="af7ae-117">Here you use the \<serviceAuthenticationManager> element or ServiceAuthenticationBehavior to specify the authentication settings that will be inherited.</span></span> <span data-ttu-id="af7ae-118">Le code présente l'aspect suivant :</span><span class="sxs-lookup"><span data-stu-id="af7ae-118">In code it looks like this:</span></span>  
  
```csharp  
// ...  
ServiceAuthenticationBehavior sab = null;  
sab = serviceHost.Description.Behaviors.Find<ServiceAuthenticationBehavior>();  
  
if (sab == null)  
{  
    sab = new ServiceAuthenticationBehavior();  
    sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
    serviceHost.Description.Behaviors.Add(sab);  
}  
else  
{  
     sab.AuthenticationSchemes = AuthenticationSchemes.Basic | AuthenticationSchemes.Negotiate | AuthenticationSchemes.Digest;  
}  
// ...  
```  
  
 <span data-ttu-id="af7ae-119">La configuration présente l'aspect suivant :</span><span class="sxs-lookup"><span data-stu-id="af7ae-119">In config, it looks like this:</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="limitedAuthBehavior">  
          <serviceAuthenticationManager authenticationSchemes="Negotiate, Digest, Basic"/>  
          <!-- ... -->  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="af7ae-120">Et vous pouvez ensuite spécifier InheritFromHost dans vos paramètres de liaison comme indiqué dans l'extrait de code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="af7ae-120">And then you can specify InheritFromHost in your binding settings as shown in the following XML snippet.</span></span>  
  
```xml  
<bindings>  
      <basicHttpBinding>  
        <binding name="secureBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="InheritedFromHost" />  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
```  
  
 <span data-ttu-id="af7ae-121">Sinon, vous pouvez spécifier les schémas d’authentification dans la liaison personnalisée, en définissant les schémas d’authentification sur l’élément de liaison de transport HTTP, comme indiqué dans l’extrait de code de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="af7ae-121">Alternatively, you can specify the authentication schemes in a custom binding, by setting the authentication schemes on the HTTP transport binding element, as shown in the following config snippet.</span></span>  
  
```xml  
<binding name="multipleBinding">  
      <textMessageEncoding/>  
      <httpTransport authenticationScheme="Negotiate, Ntlm, Digest, Basic" />  
    </binding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="af7ae-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af7ae-122">See also</span></span>

- [<span data-ttu-id="af7ae-123">Liaisons et sécurité</span><span class="sxs-lookup"><span data-stu-id="af7ae-123">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="af7ae-124">Points de terminaison : adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="af7ae-124">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="af7ae-125">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="af7ae-125">Configuring System-Provided Bindings</span></span>](configuring-system-provided-bindings.md)
- [<span data-ttu-id="af7ae-126">Fonctionnalités de sécurité avec des liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="af7ae-126">Security Capabilities with Custom Bindings</span></span>](security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="af7ae-127">Liaisons</span><span class="sxs-lookup"><span data-stu-id="af7ae-127">Bindings</span></span>](bindings.md)
- [<span data-ttu-id="af7ae-128">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="af7ae-128">Custom Bindings</span></span>](../extending/custom-bindings.md)
