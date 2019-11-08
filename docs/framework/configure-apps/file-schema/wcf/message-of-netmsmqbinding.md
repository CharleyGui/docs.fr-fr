---
title: <message> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736759"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="6ef72-102">\<> de message de \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="6ef72-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="6ef72-103">Définit les paramètres de sécurité des messages SOAP sur cette liaison `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="6ef72-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

<span data-ttu-id="6ef72-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6ef72-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6ef72-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6ef72-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6ef72-106">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="6ef72-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="6ef72-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**NetMsmqBinding**](netmsmqbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="6ef72-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="6ef72-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="6ef72-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="6ef72-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **&nbsp;&nbsp;\<** ](security-of-netmsmqbinding.md) ></span><span class="sxs-lookup"><span data-stu-id="6ef72-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="6ef72-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** ></span><span class="sxs-lookup"><span data-stu-id="6ef72-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="6ef72-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ef72-111">Syntax</span></span>

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ef72-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6ef72-112">Attributes and Elements</span></span>

<span data-ttu-id="6ef72-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6ef72-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ef72-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="6ef72-114">Attributes</span></span>

|<span data-ttu-id="6ef72-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="6ef72-115">Attribute</span></span>|<span data-ttu-id="6ef72-116">Description</span><span class="sxs-lookup"><span data-stu-id="6ef72-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="6ef72-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="6ef72-117">algorithmSuite</span></span>|<span data-ttu-id="6ef72-118">Définit le chiffrement des messages et algorithmes de clé de type WRAP utilisés pour obtenir la sécurité basée sur des messages pour les messages envoyés via le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6ef72-118">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="6ef72-119">La valeur par défaut est `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="6ef72-119">The default value is `Aes256`.</span></span> <span data-ttu-id="6ef72-120">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="6ef72-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="6ef72-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="6ef72-121">clientCredentialType</span></span>|<span data-ttu-id="6ef72-122">Spécifie le type d'information d'identification à utiliser lors de l'exécution de l'authentification du client pour les messages envoyés via le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6ef72-122">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="6ef72-123">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6ef72-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6ef72-124">-None : cela permet au service d’interagir avec des clients anonymes.</span><span class="sxs-lookup"><span data-stu-id="6ef72-124">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="6ef72-125">Ni le service ni le client n'exigent d'informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="6ef72-125">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="6ef72-126">-Windows : permet aux échanges SOAP d’être sous le contexte authentifié d’une information d’identification Windows.</span><span class="sxs-lookup"><span data-stu-id="6ef72-126">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="6ef72-127">Exécute toujours une authentification basée sur Kerberos.</span><span class="sxs-lookup"><span data-stu-id="6ef72-127">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="6ef72-128">-UserName : permet au service d’exiger que le client soit authentifié à l’aide d’informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6ef72-128">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="6ef72-129">Dans ce cas, les informations d’identification doivent être spécifiées à l’aide de `clientCredentials` comportement **attention :** Windows Communication Foundation (WCF) ne prend pas en charge l’envoi d’un résumé de mot de passe ou la dérivation de clés à l’aide d’un mot de passe et de ces clés pour la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="6ef72-129">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="6ef72-130">Par conséquent, WCF garantit que l’échange est sécurisé lors de l’utilisation d’informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6ef72-130">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="6ef72-131">Ce mode requiert que le certificat de service soit spécifié côté client à l'aide du comportement `clientCredential` et de `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="6ef72-131">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="6ef72-132">-Certificat : permet au service d’exiger que le client soit authentifié à l’aide d’un certificat.</span><span class="sxs-lookup"><span data-stu-id="6ef72-132">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="6ef72-133">Les informations d'identification du client dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="6ef72-133">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="6ef72-134">Les informations d'identification du service dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials` en spécifiant le `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="6ef72-134">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="6ef72-135">-CardSpace : permet au service d’exiger que le client soit authentifié à l’aide d’un CardSpace.</span><span class="sxs-lookup"><span data-stu-id="6ef72-135">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="6ef72-136">Le `serviceCertificate` doit être configuré dans le comportement `clientCredential`.</span><span class="sxs-lookup"><span data-stu-id="6ef72-136">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="6ef72-137">La valeur par défaut est `Windows`.</span><span class="sxs-lookup"><span data-stu-id="6ef72-137">The default value is `Windows`.</span></span> <span data-ttu-id="6ef72-138">Cet attribut est de type <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="6ef72-138">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6ef72-139">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6ef72-139">Child Elements</span></span>

<span data-ttu-id="6ef72-140">aucune.</span><span class="sxs-lookup"><span data-stu-id="6ef72-140">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6ef72-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6ef72-141">Parent Elements</span></span>

|<span data-ttu-id="6ef72-142">Élément</span><span class="sxs-lookup"><span data-stu-id="6ef72-142">Element</span></span>|<span data-ttu-id="6ef72-143">Description</span><span class="sxs-lookup"><span data-stu-id="6ef72-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6ef72-144">> de sécurité \<</span><span class="sxs-lookup"><span data-stu-id="6ef72-144">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="6ef72-145">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="6ef72-145">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6ef72-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ef72-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="6ef72-147">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="6ef72-147">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="6ef72-148">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="6ef72-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6ef72-149">Liaisons</span><span class="sxs-lookup"><span data-stu-id="6ef72-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6ef72-150">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="6ef72-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6ef72-151">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="6ef72-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6ef72-152">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="6ef72-152">\<binding></span></span>](bindings.md)
