---
title: <messageSenderAuthentication> (élément)
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 3693b2b4c6b6cbc3705a25967aedc88e36291407
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547009"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="10f6e-102">\<messageSenderAuthentication>, élément</span><span class="sxs-lookup"><span data-stu-id="10f6e-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="10f6e-103">Spécifie les options d'authentification pour les expéditeurs du message du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="10f6e-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="10f6e-104">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="10f6e-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="10f6e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10f6e-105">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10f6e-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="10f6e-106">Attributes and Elements</span></span>  
 <span data-ttu-id="10f6e-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="10f6e-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10f6e-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="10f6e-108">Attributes</span></span>  
  
|<span data-ttu-id="10f6e-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="10f6e-109">Attribute</span></span>|<span data-ttu-id="10f6e-110">Description</span><span class="sxs-lookup"><span data-stu-id="10f6e-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="10f6e-111">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="10f6e-111">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="10f6e-112">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-112">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="10f6e-113">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="10f6e-113">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="10f6e-114">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="10f6e-114">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="10f6e-115">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="10f6e-115">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="10f6e-116">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-116">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="10f6e-117">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="10f6e-117">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="10f6e-118">La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="10f6e-118">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="10f6e-119">customCertificateValidatorType, attribut</span><span class="sxs-lookup"><span data-stu-id="10f6e-119">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="10f6e-120">Value</span><span class="sxs-lookup"><span data-stu-id="10f6e-120">Value</span></span>|<span data-ttu-id="10f6e-121">Description</span><span class="sxs-lookup"><span data-stu-id="10f6e-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10f6e-122">String</span><span class="sxs-lookup"><span data-stu-id="10f6e-122">String</span></span>|<span data-ttu-id="10f6e-123">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="10f6e-123">Optional.</span></span> <span data-ttu-id="10f6e-124">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="10f6e-124">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="10f6e-125">Au minimum, un espace de noms et un nom de type sont requis.</span><span class="sxs-lookup"><span data-stu-id="10f6e-125">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="10f6e-126">Les informations facultatives incluent : le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="10f6e-126">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="10f6e-127">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="10f6e-127">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="10f6e-128">Value</span><span class="sxs-lookup"><span data-stu-id="10f6e-128">Value</span></span>|<span data-ttu-id="10f6e-129">Description</span><span class="sxs-lookup"><span data-stu-id="10f6e-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10f6e-130">Énumération</span><span class="sxs-lookup"><span data-stu-id="10f6e-130">Enumeration</span></span>|<span data-ttu-id="10f6e-131">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="10f6e-131">Optional.</span></span> <span data-ttu-id="10f6e-132">Une des valeurs suivantes : `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust` et `Custom`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-132">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="10f6e-133">La valeur par défaut est `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-133">The default is `ChainTrust`.</span></span> <span data-ttu-id="10f6e-134">La valeur par défaut est `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-134">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="10f6e-135">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="10f6e-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="10f6e-136">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="10f6e-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="10f6e-137">Value</span><span class="sxs-lookup"><span data-stu-id="10f6e-137">Value</span></span>|<span data-ttu-id="10f6e-138">Description</span><span class="sxs-lookup"><span data-stu-id="10f6e-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10f6e-139">Énumération</span><span class="sxs-lookup"><span data-stu-id="10f6e-139">Enumeration</span></span>|<span data-ttu-id="10f6e-140">Une des valeurs suivantes : `NoCheck`, `Online` et `Offline`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-140">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="10f6e-141">La valeur par défaut est `Online`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-141">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="10f6e-142">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="10f6e-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="10f6e-143">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="10f6e-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="10f6e-144">Value</span><span class="sxs-lookup"><span data-stu-id="10f6e-144">Value</span></span>|<span data-ttu-id="10f6e-145">Description</span><span class="sxs-lookup"><span data-stu-id="10f6e-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10f6e-146">Énumération</span><span class="sxs-lookup"><span data-stu-id="10f6e-146">Enumeration</span></span>|<span data-ttu-id="10f6e-147">L’une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-147">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="10f6e-148">La valeur par défaut est `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-148">The default is `CurrentUser`.</span></span> <span data-ttu-id="10f6e-149">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-149">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="10f6e-150">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-150">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="10f6e-151">La valeur par défaut est `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-151">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10f6e-152">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="10f6e-152">Child Elements</span></span>  
 <span data-ttu-id="10f6e-153">Aucun.</span><span class="sxs-lookup"><span data-stu-id="10f6e-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10f6e-154">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="10f6e-154">Parent Elements</span></span>  
  
|<span data-ttu-id="10f6e-155">Élément</span><span class="sxs-lookup"><span data-stu-id="10f6e-155">Element</span></span>|<span data-ttu-id="10f6e-156">Description</span><span class="sxs-lookup"><span data-stu-id="10f6e-156">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="10f6e-157">Spécifie une information d'identification utilisée pour authentifier le client auprès d'un service homologue.</span><span class="sxs-lookup"><span data-stu-id="10f6e-157">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10f6e-158">Notes</span><span class="sxs-lookup"><span data-stu-id="10f6e-158">Remarks</span></span>  
 <span data-ttu-id="10f6e-159">Cet élément doit être configuré si l'authentification des messages est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="10f6e-159">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="10f6e-160">Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="10f6e-160">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="10f6e-161">Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément.</span><span class="sxs-lookup"><span data-stu-id="10f6e-161">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="10f6e-162">Le validateur peut accepter ou rejeter les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="10f6e-162">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10f6e-163"> Exemple</span><span class="sxs-lookup"><span data-stu-id="10f6e-163">Example</span></span>  
 <span data-ttu-id="10f6e-164">Les jeux de codes suivants affectent le mode de validation de l’expéditeur du message à `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="10f6e-164">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10f6e-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10f6e-165">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="10f6e-166">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="10f6e-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="10f6e-167">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="10f6e-167">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="10f6e-168">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="10f6e-168">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="10f6e-169">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="10f6e-169">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="10f6e-170">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="10f6e-170">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
