---
title: Élément <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400080"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="4292f-102">Élément \<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="4292f-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="4292f-103">Spécifie les options d'authentification pour les clients du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="4292f-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="4292f-104">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="4292f-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="4292f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4292f-105">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4292f-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4292f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4292f-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4292f-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4292f-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="4292f-108">Attributes</span></span>  
  
|<span data-ttu-id="4292f-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="4292f-109">Attribute</span></span>|<span data-ttu-id="4292f-110">Description</span><span class="sxs-lookup"><span data-stu-id="4292f-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="4292f-111">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="4292f-111">Optional string.</span></span> <span data-ttu-id="4292f-112">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4292f-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="4292f-113">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="4292f-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="4292f-114">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="4292f-114">Optional enumeration.</span></span> <span data-ttu-id="4292f-115">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="4292f-115">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="4292f-116">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="4292f-116">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="4292f-117">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="4292f-117">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="4292f-118">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="4292f-118">Optional enumeration.</span></span> <span data-ttu-id="4292f-119">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="4292f-119">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="4292f-120">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="4292f-120">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="4292f-121">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="4292f-121">Optional enumeration.</span></span> <span data-ttu-id="4292f-122">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="4292f-122">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="4292f-123">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="4292f-123">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="4292f-124">La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="4292f-124">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="4292f-125">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="4292f-125">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="4292f-126">customCertificateValidatorType, attribut</span><span class="sxs-lookup"><span data-stu-id="4292f-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="4292f-127">Valeur</span><span class="sxs-lookup"><span data-stu-id="4292f-127">Value</span></span>|<span data-ttu-id="4292f-128">Description</span><span class="sxs-lookup"><span data-stu-id="4292f-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4292f-129">String</span><span class="sxs-lookup"><span data-stu-id="4292f-129">String</span></span>|<span data-ttu-id="4292f-130">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="4292f-130">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="4292f-131">Au minimum, un espace de noms et un nom de type sont requis.</span><span class="sxs-lookup"><span data-stu-id="4292f-131">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="4292f-132">Les informations facultatives incluent : le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="4292f-132">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="4292f-133">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="4292f-133">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="4292f-134">Valeur</span><span class="sxs-lookup"><span data-stu-id="4292f-134">Value</span></span>|<span data-ttu-id="4292f-135">Description</span><span class="sxs-lookup"><span data-stu-id="4292f-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4292f-136">Énumération</span><span class="sxs-lookup"><span data-stu-id="4292f-136">Enumeration</span></span>|<span data-ttu-id="4292f-137">Une des valeurs suivantes : `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust` et `Custom`.</span><span class="sxs-lookup"><span data-stu-id="4292f-137">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="4292f-138">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="4292f-138">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="4292f-139">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4292f-139">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="4292f-140">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="4292f-140">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="4292f-141">Valeur</span><span class="sxs-lookup"><span data-stu-id="4292f-141">Value</span></span>|<span data-ttu-id="4292f-142">Description</span><span class="sxs-lookup"><span data-stu-id="4292f-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4292f-143">Énumération</span><span class="sxs-lookup"><span data-stu-id="4292f-143">Enumeration</span></span>|<span data-ttu-id="4292f-144">Une des valeurs suivantes : `NoCheck`, `Online` et `Offline`.</span><span class="sxs-lookup"><span data-stu-id="4292f-144">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="4292f-145">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="4292f-145">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="4292f-146">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4292f-146">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="4292f-147">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="4292f-147">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="4292f-148">Valeur</span><span class="sxs-lookup"><span data-stu-id="4292f-148">Value</span></span>|<span data-ttu-id="4292f-149">Description</span><span class="sxs-lookup"><span data-stu-id="4292f-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4292f-150">Énumération</span><span class="sxs-lookup"><span data-stu-id="4292f-150">Enumeration</span></span>|<span data-ttu-id="4292f-151">L’une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="4292f-151">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="4292f-152">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="4292f-152">The default is `CurrentUser`.</span></span> <span data-ttu-id="4292f-153">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="4292f-153">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="4292f-154">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="4292f-154">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4292f-155">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4292f-155">Child Elements</span></span>  
 <span data-ttu-id="4292f-156">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4292f-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4292f-157">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4292f-157">Parent Elements</span></span>  
  
|<span data-ttu-id="4292f-158">Élément</span><span class="sxs-lookup"><span data-stu-id="4292f-158">Element</span></span>|<span data-ttu-id="4292f-159">Description</span><span class="sxs-lookup"><span data-stu-id="4292f-159">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="4292f-160">Spécifie une information d'identification utilisée pour authentifier le client auprès d'un service homologue.</span><span class="sxs-lookup"><span data-stu-id="4292f-160">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4292f-161">Remarques</span><span class="sxs-lookup"><span data-stu-id="4292f-161">Remarks</span></span>  
 <span data-ttu-id="4292f-162">L'élément `<authentication>` correspond à la classe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>.</span><span class="sxs-lookup"><span data-stu-id="4292f-162">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="4292f-163">Cet élément spécifie un validateur, appelé pendant l'authentification de voisins dans la maille.</span><span class="sxs-lookup"><span data-stu-id="4292f-163">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="4292f-164">Lorsqu'un nouvel homologue essaie d'établir une connexion avec un voisin, il transmet ses propres informations d'identification à l'homologue répondant.</span><span class="sxs-lookup"><span data-stu-id="4292f-164">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="4292f-165">Le validateur du répondeur est appelé pour vérifier les informations d'identification du tiers distant.</span><span class="sxs-lookup"><span data-stu-id="4292f-165">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="4292f-166">Chaque fois qu'une connexion est établie avec un homologue de la maille, les deux homologues sont authentifiés mutuellement, ce qui signifie que des validateurs sont appelés à chaque extrémité.</span><span class="sxs-lookup"><span data-stu-id="4292f-166">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4292f-167">Exemple</span><span class="sxs-lookup"><span data-stu-id="4292f-167">Example</span></span>  
 <span data-ttu-id="4292f-168">Le code suivant affecte la valeur `PeerOrChainTrust` au mode de validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="4292f-168">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="4292f-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4292f-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="4292f-170">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="4292f-170">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="4292f-171">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="4292f-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="4292f-172">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4292f-172">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="4292f-173">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4292f-173">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="4292f-174">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="4292f-174">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
