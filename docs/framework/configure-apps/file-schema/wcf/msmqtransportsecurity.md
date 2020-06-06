---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153007"
---
# \<msmqTransportSecurity>
<span data-ttu-id="f6a78-101">Spécifie des paramètres de sécurité de transport MSMQ pour une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f6a78-101">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="f6a78-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6a78-102">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6a78-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f6a78-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f6a78-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f6a78-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6a78-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="f6a78-105">Attributes</span></span>  
  
|<span data-ttu-id="f6a78-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="f6a78-106">Attribute</span></span>|<span data-ttu-id="f6a78-107">Description</span><span class="sxs-lookup"><span data-stu-id="f6a78-107">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="f6a78-108">Spécifie comment le message doit être authentifié par le transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f6a78-108">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="f6a78-109">S'il a la valeur `None`, la valeur de l'attribut `msmqProtectionLevel` doit également être `None`.</span><span class="sxs-lookup"><span data-stu-id="f6a78-109">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="f6a78-110">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f6a78-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f6a78-111">-None : aucune authentification.</span><span class="sxs-lookup"><span data-stu-id="f6a78-111">-   None: No authentication.</span></span><br /><span data-ttu-id="f6a78-112">-Windows : le mécanisme d’authentification utilise Active Directory pour obtenir le certificat X. 509 du SID associé au message.</span><span class="sxs-lookup"><span data-stu-id="f6a78-112">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="f6a78-113">Il est ensuite utilisé pour vérifier l'ACL de la file d'attente afin de s'assurer que l'utilisateur a l'autorisation d'écrire dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="f6a78-113">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="f6a78-114">-Certificat : le canal obtient le certificat à partir du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="f6a78-114">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="f6a78-115">La valeur par défaut est Windows.</span><span class="sxs-lookup"><span data-stu-id="f6a78-115">The default value is Windows.</span></span> <span data-ttu-id="f6a78-116">Cet attribut est de type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="f6a78-116">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="f6a78-117">Spécifie l'algorithme à utiliser pour le chiffrement des messages sur le câble lors du transfert de messages entre des gestionnaires de file d'attente de messages.</span><span class="sxs-lookup"><span data-stu-id="f6a78-117">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="f6a78-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f6a78-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f6a78-119">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="f6a78-119">-   RC4Stream</span></span><br /><span data-ttu-id="f6a78-120">-AES</span><span class="sxs-lookup"><span data-stu-id="f6a78-120">-   AES</span></span><br /><br /> <span data-ttu-id="f6a78-121">La valeur par défaut est RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="f6a78-121">The default value is RC4Stream.</span></span> <span data-ttu-id="f6a78-122">Cet attribut est de type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="f6a78-122">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="f6a78-123">Spécifie le mode de sécurisation du message au niveau du transport MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f6a78-123">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="f6a78-124">Le chiffrement garantit l’intégrité des messages tandis que EncryptAndSign garantit l’intégrité et la non-répudiation des messages. autrement dit, le message provient de l’expéditeur et l’expéditeur est bien celui qu’il prétend être.</span><span class="sxs-lookup"><span data-stu-id="f6a78-124">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="f6a78-125">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f6a78-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f6a78-126">-None : aucune protection.</span><span class="sxs-lookup"><span data-stu-id="f6a78-126">-   None: No protection.</span></span><br /><span data-ttu-id="f6a78-127">-Sign : les messages sont signés.</span><span class="sxs-lookup"><span data-stu-id="f6a78-127">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="f6a78-128">-EncryptAndSign : les messages sont chiffrés et signés.</span><span class="sxs-lookup"><span data-stu-id="f6a78-128">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="f6a78-129">La valeur par défaut est Sign.</span><span class="sxs-lookup"><span data-stu-id="f6a78-129">The default value is Sign.</span></span> <span data-ttu-id="f6a78-130">Cet attribut est de type <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="f6a78-130">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="f6a78-131">Spécifie l’algorithme à utiliser pour calculer le condensat dans le cadre des signatures.</span><span class="sxs-lookup"><span data-stu-id="f6a78-131">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="f6a78-132">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="f6a78-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f6a78-133">-MD5</span><span class="sxs-lookup"><span data-stu-id="f6a78-133">-   MD5</span></span><br /><span data-ttu-id="f6a78-134">-SHA1</span><span class="sxs-lookup"><span data-stu-id="f6a78-134">-   SHA1</span></span><br /><span data-ttu-id="f6a78-135">-SHA256</span><span class="sxs-lookup"><span data-stu-id="f6a78-135">-   SHA256</span></span><br /><span data-ttu-id="f6a78-136">-SHA512</span><span class="sxs-lookup"><span data-stu-id="f6a78-136">-   SHA512</span></span><br /><br /> <span data-ttu-id="f6a78-137">La valeur par défaut est SHA1.</span><span class="sxs-lookup"><span data-stu-id="f6a78-137">The default value is SHA1.</span></span> <span data-ttu-id="f6a78-138">Cet attribut est de type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="f6a78-138">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="f6a78-139">En raison de problèmes de collision avec MD5 et SHA1, Microsoft recommande SHA256 ou une meilleure solution.</span><span class="sxs-lookup"><span data-stu-id="f6a78-139">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6a78-140">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f6a78-140">Child Elements</span></span>  
 <span data-ttu-id="f6a78-141">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f6a78-141">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6a78-142">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f6a78-142">Parent Elements</span></span>  
  
|<span data-ttu-id="f6a78-143">Élément</span><span class="sxs-lookup"><span data-stu-id="f6a78-143">Element</span></span>|<span data-ttu-id="f6a78-144">Description</span><span class="sxs-lookup"><span data-stu-id="f6a78-144">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="f6a78-145">Spécifie des paramètres requis pour l'interaction avec un expéditeur ou un récepteur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f6a78-145">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="f6a78-146">Spécifie les propriétés de communication mises en file d'attente pour un service Windows Communication Foundation (WCF) qui utilise le protocole MSMQ natif.</span><span class="sxs-lookup"><span data-stu-id="f6a78-146">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6a78-147">Remarques</span><span class="sxs-lookup"><span data-stu-id="f6a78-147">Remarks</span></span>  
 <span data-ttu-id="f6a78-148">Pour plus d’informations sur la sécurité du transport, consultez [sécurité du transport](../../../wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="f6a78-148">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6a78-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6a78-149">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f6a78-150">Files d'attente dans WCF</span><span class="sxs-lookup"><span data-stu-id="f6a78-150">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="f6a78-151">Transports</span><span class="sxs-lookup"><span data-stu-id="f6a78-151">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="f6a78-152">Choix d'un transport</span><span class="sxs-lookup"><span data-stu-id="f6a78-152">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="f6a78-153">Liaisons</span><span class="sxs-lookup"><span data-stu-id="f6a78-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f6a78-154">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="f6a78-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f6a78-155">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="f6a78-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="f6a78-156">Sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="f6a78-156">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
