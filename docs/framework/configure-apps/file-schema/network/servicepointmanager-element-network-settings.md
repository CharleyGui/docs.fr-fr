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
ms.openlocfilehash: b7333016fea2d46285d3c98181c0ca4904c376f8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089127"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="7bc35-102">\<servicePointManager>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="7bc35-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="7bc35-103">Configure les connexions aux ressources réseau.</span><span class="sxs-lookup"><span data-stu-id="7bc35-103">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="7bc35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bc35-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bc35-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7bc35-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7bc35-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7bc35-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bc35-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="7bc35-107">Attributes</span></span>  
  
|<span data-ttu-id="7bc35-108">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="7bc35-108">**Attribute**</span></span>|<span data-ttu-id="7bc35-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="7bc35-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="7bc35-110">Spécifie si le système doit vérifier que le nom du certificat correspond au nom d’hôte du serveur avant d’utiliser le certificat.</span><span class="sxs-lookup"><span data-stu-id="7bc35-110">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="7bc35-111">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="7bc35-111">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="7bc35-112">Spécifie si le système doit vérifier si le certificat a été révoqué avant d’utiliser le certificat.</span><span class="sxs-lookup"><span data-stu-id="7bc35-112">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="7bc35-113">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="7bc35-113">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="7bc35-114">Spécifie la durée de mise en cache des résolutions DNS (Domain Name Service) dans le cadre de l’option de tourniquet (Round Robin) DNS, en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="7bc35-114">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="7bc35-115">La valeur par défaut est 120 000 millisecondes (deux minutes).</span><span class="sxs-lookup"><span data-stu-id="7bc35-115">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="7bc35-116">Spécifie si les résolutions DNS des noms d’hôtes avec plusieurs adresses IP (Internet Protocol) renvoient toutes les adresses ou uniquement la première.</span><span class="sxs-lookup"><span data-stu-id="7bc35-116">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="7bc35-117">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="7bc35-117">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="7bc35-118">Spécifie la stratégie de chiffrement appliquée à une session SSL/TLS sur une <xref:System.Net.ServicePointManager> instance.</span><span class="sxs-lookup"><span data-stu-id="7bc35-118">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="7bc35-119">Les valeurs possibles sont équivalentes aux valeurs de l' <xref:System.Net.Security.EncryptionPolicy> énumération.</span><span class="sxs-lookup"><span data-stu-id="7bc35-119">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="7bc35-120">L’utilisation de <xref:System.Security.Authentication.CipherAlgorithmType.Null> est requise lorsque la stratégie de chiffrement est définie sur `NoEncryption` .</span><span class="sxs-lookup"><span data-stu-id="7bc35-120">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="7bc35-121">La valeur par défaut est `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="7bc35-121">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="7bc35-122">Spécifie si les méthodes de publication doivent s’attendre à recevoir une `100-continue` réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="7bc35-122">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="7bc35-123">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="7bc35-123">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="7bc35-124">Spécifie si les connexions contrôlées par le gestionnaire de point de service utilisent l’algorithme Nagle.</span><span class="sxs-lookup"><span data-stu-id="7bc35-124">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="7bc35-125">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="7bc35-125">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bc35-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7bc35-126">Child Elements</span></span>  
 <span data-ttu-id="7bc35-127">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7bc35-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bc35-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7bc35-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7bc35-129">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="7bc35-129">**Element**</span></span>|<span data-ttu-id="7bc35-130">**Description**</span><span class="sxs-lookup"><span data-stu-id="7bc35-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7bc35-131">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7bc35-131">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="7bc35-132">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="7bc35-132">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bc35-133">Remarques</span><span class="sxs-lookup"><span data-stu-id="7bc35-133">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7bc35-134">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="7bc35-134">Configuration Files</span></span>  
 <span data-ttu-id="7bc35-135">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="7bc35-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bc35-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bc35-136">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="7bc35-137">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="7bc35-137">Network Settings Schema</span></span>](index.md)
