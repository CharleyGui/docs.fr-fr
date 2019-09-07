---
title: <message> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 09d9d4a5d1967afaf9a6ed5756c309e78fee0923
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400257"
---
# <a name="message-of-netmsmqbinding"></a><span data-ttu-id="07d8a-102">\<> de message \<de NetMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="07d8a-102">\<message> of \<netMsmqBinding></span></span>

<span data-ttu-id="07d8a-103">Définit les paramètres de sécurité des messages SOAP sur cette liaison `netMsmqBinding`.</span><span class="sxs-lookup"><span data-stu-id="07d8a-103">Defines the SOAP message security settings on this `netMsmqBinding` binding.</span></span>

<span data-ttu-id="07d8a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="07d8a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="07d8a-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="07d8a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="07d8a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="07d8a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="07d8a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="07d8a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="07d8a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="07d8a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="07d8a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="07d8a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)</span></span>\
<span data-ttu-id="07d8a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de messages**</span><span class="sxs-lookup"><span data-stu-id="07d8a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="07d8a-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07d8a-111">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="07d8a-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="07d8a-112">Attributes and Elements</span></span>

<span data-ttu-id="07d8a-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="07d8a-113">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="07d8a-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="07d8a-114">Attributes</span></span>

|<span data-ttu-id="07d8a-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="07d8a-115">Attribute</span></span>|<span data-ttu-id="07d8a-116">Description</span><span class="sxs-lookup"><span data-stu-id="07d8a-116">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="07d8a-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="07d8a-117">algorithmSuite</span></span>|<span data-ttu-id="07d8a-118">Définit le chiffrement des messages et algorithmes de clé de type WRAP utilisés pour obtenir la sécurité basée sur des messages pour les messages envoyés via le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="07d8a-118">Sets the message encryption and key-wrap algorithms that are used to achieve message-based security for messages sent over MSMQ transport.</span></span><br /><br /> <span data-ttu-id="07d8a-119">La valeur par défaut est `Aes256`.</span><span class="sxs-lookup"><span data-stu-id="07d8a-119">The default value is `Aes256`.</span></span> <span data-ttu-id="07d8a-120">Cet attribut est de type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="07d8a-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span>|
|<span data-ttu-id="07d8a-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="07d8a-121">clientCredentialType</span></span>|<span data-ttu-id="07d8a-122">Spécifie le type d'information d'identification à utiliser lors de l'exécution de l'authentification du client pour les messages envoyés via le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="07d8a-122">Specifies the type of credential to be used when performing client authentication for messages sent over the MSMQ transport.</span></span> <span data-ttu-id="07d8a-123">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="07d8a-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="07d8a-124">None Permet au service d'interagir avec les clients anonymes.</span><span class="sxs-lookup"><span data-stu-id="07d8a-124">-   None: This allows the service to interact with anonymous clients.</span></span> <span data-ttu-id="07d8a-125">Ni le service ni le client n'exigent d'informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="07d8a-125">Neither the service nor the client requires a credential.</span></span><br /><span data-ttu-id="07d8a-126">Windows Cela permet aux échanges SOAP d’être sous le contexte authentifié d’une information d’identification Windows.</span><span class="sxs-lookup"><span data-stu-id="07d8a-126">-   Windows: This enables the SOAP exchanges to be under the authenticated context of a Windows credential.</span></span> <span data-ttu-id="07d8a-127">Exécute toujours une authentification basée sur Kerberos.</span><span class="sxs-lookup"><span data-stu-id="07d8a-127">This always performs Kerberos-based authentication.</span></span><br /><span data-ttu-id="07d8a-128">Nom d’utilisateur Cela permet au service d’exiger que le client soit authentifié à l’aide d’informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="07d8a-128">-   UserName: This enables the service to require that the client be authenticated using a UserName credential.</span></span> <span data-ttu-id="07d8a-129">Dans ce cas, les informations d’identification doivent être spécifiées à l’aide du `clientCredentials` comportement **attention :**  Windows Communication Foundation (WCF) ne prend pas en charge l’envoi d’un résumé de mot de passe ou la dérivation de clés à l’aide d’un mot de passe et de ces clés pour la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="07d8a-129">The credential in this case needs to be specified using the `clientCredentials` behavior **Caution:**  Windows Communication Foundation (WCF) does not support sending a password digest or deriving keys using password and using such keys for message security.</span></span> <span data-ttu-id="07d8a-130">Par conséquent, WCF garantit que l’échange est sécurisé lors de l’utilisation d’informations d’identification de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="07d8a-130">Therefore, WCF enforces that the exchange is secured when using UserName credentials.</span></span> <span data-ttu-id="07d8a-131">Ce mode requiert que le certificat de service soit spécifié côté client à l'aide du comportement `clientCredential` et de `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="07d8a-131">This mode requires that the service certificate be specified on the client side using `clientCredential` behavior and `serviceCertificate`.</span></span> <br /><br /> <span data-ttu-id="07d8a-132">Certificat Cela permet au service d’exiger que le client soit authentifié à l’aide d’un certificat.</span><span class="sxs-lookup"><span data-stu-id="07d8a-132">-   Certificate: This enables the service to require that the client be authenticated using a certificate.</span></span> <span data-ttu-id="07d8a-133">Les informations d'identification du client dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="07d8a-133">The client credential in this case needs to be specified using the `clientCredentials` behavior.</span></span> <span data-ttu-id="07d8a-134">Les informations d'identification du service dans ce cas doivent être spécifiées à l'aide du comportement `clientCredentials` en spécifiant le `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="07d8a-134">The service credential in this case needs to be specified using the `clientCredentials` behavior by specifying the `serviceCertificate`.</span></span><br /><span data-ttu-id="07d8a-135">CardSpace Cela permet au service d’exiger que le client soit authentifié à l’aide d’un CardSpace.</span><span class="sxs-lookup"><span data-stu-id="07d8a-135">-   CardSpace: This allows the service to require that the client be authenticated using a CardSpace.</span></span> <span data-ttu-id="07d8a-136">Le `serviceCertificate` doit être configuré dans le comportement `clientCredential`.</span><span class="sxs-lookup"><span data-stu-id="07d8a-136">The `serviceCertificate` must be provisioned in the `clientCredential` behavior.</span></span><br /><br /> <span data-ttu-id="07d8a-137">La valeur par défaut est `Windows`.</span><span class="sxs-lookup"><span data-stu-id="07d8a-137">The default value is `Windows`.</span></span> <span data-ttu-id="07d8a-138">Cet attribut est de type <xref:System.ServiceModel.MessageCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="07d8a-138">This attribute is of type <xref:System.ServiceModel.MessageCredentialType>.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="07d8a-139">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="07d8a-139">Child Elements</span></span>

<span data-ttu-id="07d8a-140">Aucun</span><span class="sxs-lookup"><span data-stu-id="07d8a-140">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="07d8a-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="07d8a-141">Parent Elements</span></span>

|<span data-ttu-id="07d8a-142">Élément</span><span class="sxs-lookup"><span data-stu-id="07d8a-142">Element</span></span>|<span data-ttu-id="07d8a-143">Description</span><span class="sxs-lookup"><span data-stu-id="07d8a-143">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07d8a-144">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="07d8a-144">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="07d8a-145">Définit les paramètres de sécurité d’une liaison.</span><span class="sxs-lookup"><span data-stu-id="07d8a-145">Defines the security settings for a binding.</span></span>|

## <a name="see-also"></a><span data-ttu-id="07d8a-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07d8a-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [<span data-ttu-id="07d8a-147">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="07d8a-147">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="07d8a-148">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="07d8a-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="07d8a-149">Liaisons</span><span class="sxs-lookup"><span data-stu-id="07d8a-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="07d8a-150">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="07d8a-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="07d8a-151">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="07d8a-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="07d8a-152">\<binding></span><span class="sxs-lookup"><span data-stu-id="07d8a-152">\<binding></span></span>](../../../misc/binding.md)
