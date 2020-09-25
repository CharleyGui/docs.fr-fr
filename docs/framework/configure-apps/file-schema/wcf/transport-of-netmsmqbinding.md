---
title: <transport> de <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 84a5437de851ecdb96d0463ec574186ba5f91d9e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203876"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="fad7f-102">\<transport> de \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="fad7f-102">\<transport> of \<netMsmqBinding></span></span>

<span data-ttu-id="fad7f-103">Définit les paramètres de sécurité de transport.</span><span class="sxs-lookup"><span data-stu-id="fad7f-103">Defines the transport security settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="fad7f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fad7f-104">Syntax</span></span>  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fad7f-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fad7f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fad7f-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fad7f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fad7f-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="fad7f-107">Attributes</span></span>  
  
|<span data-ttu-id="fad7f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="fad7f-108">Attribute</span></span>|<span data-ttu-id="fad7f-109">Description</span><span class="sxs-lookup"><span data-stu-id="fad7f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fad7f-110">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="fad7f-110">msmqAuthenticationMode</span></span>|<span data-ttu-id="fad7f-111">Spécifie comment le message doit être authentifié par le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fad7f-111">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="fad7f-112">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fad7f-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fad7f-113">-None : aucune authentification.</span><span class="sxs-lookup"><span data-stu-id="fad7f-113">-   None: No authentication.</span></span><br /><span data-ttu-id="fad7f-114">-WindowsDomain : le mécanisme d’authentification utilise Active Directory pour récupérer le certificat X. 509 pour l’identificateur de sécurité associé au message.</span><span class="sxs-lookup"><span data-stu-id="fad7f-114">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="fad7f-115">Il est ensuite utilisé pour vérifier l'ACL de la file d'attente afin de s'assurer que l'utilisateur a l'autorisation en écriture dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="fad7f-115">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="fad7f-116">-Certificat : le canal récupère le certificat à partir du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="fad7f-116">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="fad7f-117">Par défaut, il s’agit de `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="fad7f-117">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="fad7f-118">Si cet attribut a la valeur `None`, l'attribut `msmqProtectionLevel` doit également être défini à `None`.</span><span class="sxs-lookup"><span data-stu-id="fad7f-118">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="fad7f-119">Cet attribut est de type <xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="fad7f-119">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="fad7f-120">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="fad7f-120">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="fad7f-121">Spécifie l'algorithme à utiliser pour le chiffrement des messages sur le câble lors du transfert de messages entre des gestionnaires de file d'attente de messages.</span><span class="sxs-lookup"><span data-stu-id="fad7f-121">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="fad7f-122">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fad7f-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fad7f-123">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="fad7f-123">-   RC4Stream</span></span><br /><span data-ttu-id="fad7f-124">-AES</span><span class="sxs-lookup"><span data-stu-id="fad7f-124">-   AES</span></span><br /><span data-ttu-id="fad7f-125">-La valeur par défaut est `RC4Stream` .</span><span class="sxs-lookup"><span data-stu-id="fad7f-125">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="fad7f-126">Cet attribut est de type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="fad7f-126">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="fad7f-127">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="fad7f-127">msmqProtectionLevel</span></span>|<span data-ttu-id="fad7f-128">Spécifie la façon dont les messages sont sécurisés au niveau du transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="fad7f-128">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="fad7f-129">Le chiffrement garantit l'intégrité des messages, tandis que la signature et le chiffrement garantissent à la fois l'intégrité et le non-rejet des messages.</span><span class="sxs-lookup"><span data-stu-id="fad7f-129">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="fad7f-130">Autrement dit, le message provient en effet de l’expéditeur et l’expéditeur est bien celui qu’il prétend être.</span><span class="sxs-lookup"><span data-stu-id="fad7f-130">That is, the message indeed came from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="fad7f-131">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fad7f-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fad7f-132">-None : aucune protection.</span><span class="sxs-lookup"><span data-stu-id="fad7f-132">-   None: No protection.</span></span><br /><span data-ttu-id="fad7f-133">-Sign : les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="fad7f-133">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="fad7f-134">-EncryptAndSign : les messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="fad7f-134">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="fad7f-135">-La valeur par défaut est `Sign` .</span><span class="sxs-lookup"><span data-stu-id="fad7f-135">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="fad7f-136">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="fad7f-136">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="fad7f-137">Spécifie l’algorithme de hachage à utiliser pour calculer le condensat de message.</span><span class="sxs-lookup"><span data-stu-id="fad7f-137">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="fad7f-138">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="fad7f-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fad7f-139">-MD5</span><span class="sxs-lookup"><span data-stu-id="fad7f-139">-   MD5</span></span><br /><span data-ttu-id="fad7f-140">-SHA1</span><span class="sxs-lookup"><span data-stu-id="fad7f-140">-   SHA1</span></span><br /><span data-ttu-id="fad7f-141">-SHA256</span><span class="sxs-lookup"><span data-stu-id="fad7f-141">-   SHA256</span></span><br /><span data-ttu-id="fad7f-142">-SHA512</span><span class="sxs-lookup"><span data-stu-id="fad7f-142">-   SHA512</span></span><br /><br /> <span data-ttu-id="fad7f-143">Par défaut, il s’agit de `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="fad7f-143">The default is `SHA1`.</span></span> <span data-ttu-id="fad7f-144">Cet attribut est de type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="fad7f-144">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="fad7f-145">En raison de problèmes de collision avec MD5 et SHA1, Microsoft recommande SHA256 ou une meilleure solution.</span><span class="sxs-lookup"><span data-stu-id="fad7f-145">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fad7f-146">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fad7f-146">Child Elements</span></span>  

 <span data-ttu-id="fad7f-147">None</span><span class="sxs-lookup"><span data-stu-id="fad7f-147">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fad7f-148">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fad7f-148">Parent Elements</span></span>  
  
|<span data-ttu-id="fad7f-149">Élément</span><span class="sxs-lookup"><span data-stu-id="fad7f-149">Element</span></span>|<span data-ttu-id="fad7f-150">Description</span><span class="sxs-lookup"><span data-stu-id="fad7f-150">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="fad7f-151">Définit les paramètres de sécurité de transport pour les transports de mise en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="fad7f-151">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fad7f-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fad7f-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="fad7f-153">Files d’attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="fad7f-153">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="fad7f-154">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="fad7f-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fad7f-155">Liaisons</span><span class="sxs-lookup"><span data-stu-id="fad7f-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fad7f-156">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="fad7f-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fad7f-157">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="fad7f-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
