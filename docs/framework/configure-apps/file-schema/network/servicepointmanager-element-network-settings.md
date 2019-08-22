---
title: <servicePointManager>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: a6a40d97bf16a3125452311e7762617e657ca384
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659145"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="5c580-102">\<servicePointManager >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="5c580-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="5c580-103">Configure les connexions aux ressources réseau.</span><span class="sxs-lookup"><span data-stu-id="5c580-103">Configures connections to network resources.</span></span>  
  
 <span data-ttu-id="5c580-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5c580-104">\<configuration></span></span>  
<span data-ttu-id="5c580-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5c580-105">\<system.net></span></span>  
<span data-ttu-id="5c580-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="5c580-106">\<settings></span></span>  
<span data-ttu-id="5c580-107">\<servicePointManager></span><span class="sxs-lookup"><span data-stu-id="5c580-107">\<servicePointManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c580-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c580-108">Syntax</span></span>  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c580-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5c580-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5c580-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5c580-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c580-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="5c580-111">Attributes</span></span>  
  
|<span data-ttu-id="5c580-112">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="5c580-112">**Attribute**</span></span>|<span data-ttu-id="5c580-113">**Description**</span><span class="sxs-lookup"><span data-stu-id="5c580-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="5c580-114">Spécifie si le système doit vérifier que le nom du certificat correspond au nom d’hôte du serveur avant d’utiliser le certificat.</span><span class="sxs-lookup"><span data-stu-id="5c580-114">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="5c580-115">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="5c580-115">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="5c580-116">Spécifie si le système doit vérifier si le certificat a été révoqué avant d’utiliser le certificat.</span><span class="sxs-lookup"><span data-stu-id="5c580-116">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="5c580-117">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="5c580-117">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="5c580-118">Spécifie la durée de mise en cache des résolutions DNS (Domain Name Service) dans le cadre de l’option de tourniquet (Round Robin) DNS, en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="5c580-118">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="5c580-119">La valeur par défaut est 120 000 millisecondes (deux minutes).</span><span class="sxs-lookup"><span data-stu-id="5c580-119">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="5c580-120">Spécifie si les résolutions DNS des noms d’hôtes avec plusieurs adresses IP (Internet Protocol) renvoient toutes les adresses ou uniquement la première.</span><span class="sxs-lookup"><span data-stu-id="5c580-120">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="5c580-121">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="5c580-121">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="5c580-122">Spécifie la stratégie de chiffrement appliquée à une session SSL/ <xref:System.Net.ServicePointManager> TLS sur une instance.</span><span class="sxs-lookup"><span data-stu-id="5c580-122">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="5c580-123">Les valeurs possibles sont équivalentes aux valeurs de l' <xref:System.Net.Security.EncryptionPolicy> énumération.</span><span class="sxs-lookup"><span data-stu-id="5c580-123">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="5c580-124">L’utilisation de <xref:System.Security.Authentication.CipherAlgorithmType.Null> est requise lorsque la stratégie de chiffrement est `NoEncryption`définie sur.</span><span class="sxs-lookup"><span data-stu-id="5c580-124">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="5c580-125">La valeur par défaut est `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="5c580-125">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="5c580-126">Spécifie si les méthodes de publication doivent s' `100-continue` attendre à recevoir une réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="5c580-126">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="5c580-127">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="5c580-127">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="5c580-128">Spécifie si les connexions contrôlées par le gestionnaire de point de service utilisent l’algorithme Nagle.</span><span class="sxs-lookup"><span data-stu-id="5c580-128">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="5c580-129">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="5c580-129">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c580-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5c580-130">Child Elements</span></span>  
 <span data-ttu-id="5c580-131">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5c580-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c580-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5c580-132">Parent Elements</span></span>  
  
|<span data-ttu-id="5c580-133">**Élément**</span><span class="sxs-lookup"><span data-stu-id="5c580-133">**Element**</span></span>|<span data-ttu-id="5c580-134">**Description**</span><span class="sxs-lookup"><span data-stu-id="5c580-134">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5c580-135">Réglages</span><span class="sxs-lookup"><span data-stu-id="5c580-135">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="5c580-136">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="5c580-136">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c580-137">Notes</span><span class="sxs-lookup"><span data-stu-id="5c580-137">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5c580-138">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="5c580-138">Configuration Files</span></span>  
 <span data-ttu-id="5c580-139">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5c580-139">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c580-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c580-140">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="5c580-141">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="5c580-141">Network Settings Schema</span></span>](index.md)
