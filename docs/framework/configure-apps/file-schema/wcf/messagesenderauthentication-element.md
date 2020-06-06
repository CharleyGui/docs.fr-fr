---
title: <messageSenderAuthentication> (élément)
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397789"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="47c17-102">\<messageSenderAuthentication>, élément</span><span class="sxs-lookup"><span data-stu-id="47c17-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="47c17-103">Spécifie les options d'authentification pour les expéditeurs du message du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="47c17-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="47c17-104">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="47c17-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="47c17-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47c17-105">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47c17-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="47c17-106">Attributes and Elements</span></span>  
 <span data-ttu-id="47c17-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="47c17-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47c17-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="47c17-108">Attributes</span></span>  
  
|<span data-ttu-id="47c17-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="47c17-109">Attribute</span></span>|<span data-ttu-id="47c17-110">Description</span><span class="sxs-lookup"><span data-stu-id="47c17-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="47c17-111">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="47c17-111">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="47c17-112">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="47c17-112">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="47c17-113">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="47c17-113">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="47c17-114">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="47c17-114">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="47c17-115">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="47c17-115">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="47c17-116">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="47c17-116">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="47c17-117">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="47c17-117">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="47c17-118">La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="47c17-118">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="47c17-119">customCertificateValidatorType, attribut</span><span class="sxs-lookup"><span data-stu-id="47c17-119">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="47c17-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="47c17-120">Value</span></span>|<span data-ttu-id="47c17-121">Description</span><span class="sxs-lookup"><span data-stu-id="47c17-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="47c17-122">String</span><span class="sxs-lookup"><span data-stu-id="47c17-122">String</span></span>|<span data-ttu-id="47c17-123">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="47c17-123">Optional.</span></span> <span data-ttu-id="47c17-124">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="47c17-124">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="47c17-125">Au minimum, un espace de noms et un nom de type sont requis.</span><span class="sxs-lookup"><span data-stu-id="47c17-125">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="47c17-126">Les informations facultatives incluent : le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="47c17-126">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="47c17-127">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="47c17-127">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="47c17-128">Valeur</span><span class="sxs-lookup"><span data-stu-id="47c17-128">Value</span></span>|<span data-ttu-id="47c17-129">Description</span><span class="sxs-lookup"><span data-stu-id="47c17-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="47c17-130">Énumération</span><span class="sxs-lookup"><span data-stu-id="47c17-130">Enumeration</span></span>|<span data-ttu-id="47c17-131">facultatif.</span><span class="sxs-lookup"><span data-stu-id="47c17-131">Optional.</span></span> <span data-ttu-id="47c17-132">Une des valeurs suivantes : `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust` et `Custom`.</span><span class="sxs-lookup"><span data-stu-id="47c17-132">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="47c17-133">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="47c17-133">The default is `ChainTrust`.</span></span> <span data-ttu-id="47c17-134">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="47c17-134">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="47c17-135">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="47c17-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="47c17-136">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="47c17-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="47c17-137">Valeur</span><span class="sxs-lookup"><span data-stu-id="47c17-137">Value</span></span>|<span data-ttu-id="47c17-138">Description</span><span class="sxs-lookup"><span data-stu-id="47c17-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="47c17-139">Énumération</span><span class="sxs-lookup"><span data-stu-id="47c17-139">Enumeration</span></span>|<span data-ttu-id="47c17-140">Une des valeurs suivantes : `NoCheck`, `Online` et `Offline`.</span><span class="sxs-lookup"><span data-stu-id="47c17-140">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="47c17-141">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="47c17-141">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="47c17-142">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="47c17-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="47c17-143">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="47c17-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="47c17-144">Valeur</span><span class="sxs-lookup"><span data-stu-id="47c17-144">Value</span></span>|<span data-ttu-id="47c17-145">Description</span><span class="sxs-lookup"><span data-stu-id="47c17-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="47c17-146">Énumération</span><span class="sxs-lookup"><span data-stu-id="47c17-146">Enumeration</span></span>|<span data-ttu-id="47c17-147">L’une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="47c17-147">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="47c17-148">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="47c17-148">The default is `CurrentUser`.</span></span> <span data-ttu-id="47c17-149">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="47c17-149">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="47c17-150">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="47c17-150">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="47c17-151">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="47c17-151">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47c17-152">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="47c17-152">Child Elements</span></span>  
 <span data-ttu-id="47c17-153">Aucun.</span><span class="sxs-lookup"><span data-stu-id="47c17-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="47c17-154">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="47c17-154">Parent Elements</span></span>  
  
|<span data-ttu-id="47c17-155">Élément</span><span class="sxs-lookup"><span data-stu-id="47c17-155">Element</span></span>|<span data-ttu-id="47c17-156">Description</span><span class="sxs-lookup"><span data-stu-id="47c17-156">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="47c17-157">Spécifie une information d'identification utilisée pour authentifier le client auprès d'un service homologue.</span><span class="sxs-lookup"><span data-stu-id="47c17-157">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47c17-158">Remarques</span><span class="sxs-lookup"><span data-stu-id="47c17-158">Remarks</span></span>  
 <span data-ttu-id="47c17-159">Cet élément doit être configuré si l'authentification des messages est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="47c17-159">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="47c17-160">Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="47c17-160">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="47c17-161">Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément.</span><span class="sxs-lookup"><span data-stu-id="47c17-161">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="47c17-162">Le validateur peut accepter ou rejeter les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="47c17-162">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47c17-163">Exemple</span><span class="sxs-lookup"><span data-stu-id="47c17-163">Example</span></span>  
 <span data-ttu-id="47c17-164">Les jeux de codes suivants affectent le mode de validation de l’expéditeur du message à `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="47c17-164">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47c17-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47c17-165">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="47c17-166">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="47c17-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="47c17-167">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="47c17-167">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="47c17-168">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="47c17-168">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="47c17-169">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="47c17-169">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="47c17-170">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="47c17-170">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
