---
title: <messageSenderAuthentication>, élément
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397789"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="fd99b-102">\<messageSenderAuthentication >, élément</span><span class="sxs-lookup"><span data-stu-id="fd99b-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="fd99b-103">Spécifie les options d'authentification pour les expéditeurs du message du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="fd99b-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="fd99b-104">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="fd99b-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="fd99b-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd99b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fd99b-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fd99b-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fd99b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fd99b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="fd99b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fd99b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="fd99b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fd99b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="fd99b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="fd99b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="fd99b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> homologues**](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd99b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="fd99b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<messageSenderAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="fd99b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd99b-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd99b-113">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd99b-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="fd99b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="fd99b-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="fd99b-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd99b-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="fd99b-116">Attributes</span></span>  
  
|<span data-ttu-id="fd99b-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="fd99b-117">Attribute</span></span>|<span data-ttu-id="fd99b-118">Description</span><span class="sxs-lookup"><span data-stu-id="fd99b-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="fd99b-119">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="fd99b-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="fd99b-120">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="fd99b-121">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="fd99b-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="fd99b-122">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="fd99b-122">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="fd99b-123">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="fd99b-123">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="fd99b-124">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-124">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="fd99b-125">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="fd99b-125">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="fd99b-126">La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="fd99b-126">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="fd99b-127">customCertificateValidatorType, attribut</span><span class="sxs-lookup"><span data-stu-id="fd99b-127">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="fd99b-128">`Value`</span><span class="sxs-lookup"><span data-stu-id="fd99b-128">Value</span></span>|<span data-ttu-id="fd99b-129">Description</span><span class="sxs-lookup"><span data-stu-id="fd99b-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd99b-130">String</span><span class="sxs-lookup"><span data-stu-id="fd99b-130">String</span></span>|<span data-ttu-id="fd99b-131">facultatif.</span><span class="sxs-lookup"><span data-stu-id="fd99b-131">Optional.</span></span> <span data-ttu-id="fd99b-132">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="fd99b-132">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="fd99b-133">Au minimum, un espace de noms et un nom de type sont requis.</span><span class="sxs-lookup"><span data-stu-id="fd99b-133">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="fd99b-134">Les informations facultatives incluent : le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="fd99b-134">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="fd99b-135">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="fd99b-135">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="fd99b-136">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd99b-136">Value</span></span>|<span data-ttu-id="fd99b-137">Description</span><span class="sxs-lookup"><span data-stu-id="fd99b-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd99b-138">Énumération</span><span class="sxs-lookup"><span data-stu-id="fd99b-138">Enumeration</span></span>|<span data-ttu-id="fd99b-139">facultatif.</span><span class="sxs-lookup"><span data-stu-id="fd99b-139">Optional.</span></span> <span data-ttu-id="fd99b-140">Une des valeurs suivantes : `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust` et `Custom`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-140">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="fd99b-141">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-141">The default is `ChainTrust`.</span></span> <span data-ttu-id="fd99b-142">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-142">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="fd99b-143">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="fd99b-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="fd99b-144">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="fd99b-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="fd99b-145">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd99b-145">Value</span></span>|<span data-ttu-id="fd99b-146">Description</span><span class="sxs-lookup"><span data-stu-id="fd99b-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd99b-147">Énumération</span><span class="sxs-lookup"><span data-stu-id="fd99b-147">Enumeration</span></span>|<span data-ttu-id="fd99b-148">Une des valeurs suivantes : `NoCheck`, `Online` et `Offline`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-148">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="fd99b-149">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-149">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="fd99b-150">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="fd99b-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="fd99b-151">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="fd99b-151">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="fd99b-152">Valeur</span><span class="sxs-lookup"><span data-stu-id="fd99b-152">Value</span></span>|<span data-ttu-id="fd99b-153">Description</span><span class="sxs-lookup"><span data-stu-id="fd99b-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd99b-154">Énumération</span><span class="sxs-lookup"><span data-stu-id="fd99b-154">Enumeration</span></span>|<span data-ttu-id="fd99b-155">Une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-155">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="fd99b-156">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-156">The default is `CurrentUser`.</span></span> <span data-ttu-id="fd99b-157">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-157">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="fd99b-158">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-158">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="fd99b-159">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-159">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd99b-160">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="fd99b-160">Child Elements</span></span>  
 <span data-ttu-id="fd99b-161">Aucun.</span><span class="sxs-lookup"><span data-stu-id="fd99b-161">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd99b-162">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="fd99b-162">Parent Elements</span></span>  
  
|<span data-ttu-id="fd99b-163">Élément</span><span class="sxs-lookup"><span data-stu-id="fd99b-163">Element</span></span>|<span data-ttu-id="fd99b-164">Description</span><span class="sxs-lookup"><span data-stu-id="fd99b-164">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd99b-165">\<peer></span><span class="sxs-lookup"><span data-stu-id="fd99b-165">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="fd99b-166">Spécifie une information d'identification utilisée pour authentifier le client auprès d'un service homologue.</span><span class="sxs-lookup"><span data-stu-id="fd99b-166">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd99b-167">Notes</span><span class="sxs-lookup"><span data-stu-id="fd99b-167">Remarks</span></span>  
 <span data-ttu-id="fd99b-168">Cet élément doit être configuré si l'authentification des messages est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="fd99b-168">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="fd99b-169">Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [ \<le certificat >](certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="fd99b-169">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="fd99b-170">Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément.</span><span class="sxs-lookup"><span data-stu-id="fd99b-170">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="fd99b-171">Le validateur peut accepter ou rejeter les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="fd99b-171">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd99b-172">Exemples</span><span class="sxs-lookup"><span data-stu-id="fd99b-172">Example</span></span>  
 <span data-ttu-id="fd99b-173">Les jeux de codes suivants affectent le mode de validation de l’expéditeur du message à `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="fd99b-173">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="fd99b-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd99b-174">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="fd99b-175">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="fd99b-175">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="fd99b-176">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="fd99b-176">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="fd99b-177">[canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fd99b-177">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="fd99b-178">[canal homologue l’authentification personnalisée](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fd99b-178">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="fd99b-179">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="fd99b-179">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
