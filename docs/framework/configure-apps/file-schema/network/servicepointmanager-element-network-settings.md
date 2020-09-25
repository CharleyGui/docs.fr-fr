---
title: <servicePointManager>, élément (paramètres réseau)
description: L' <servicePointManager> élément paramètres réseau configure les connexions aux options des ressources réseau dans le .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: a6678a8fe7c6f962529f9d946b103b6224d58602
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174106"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="7716c-103">\<servicePointManager>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="7716c-103">\<servicePointManager> Element (Network Settings)</span></span>

<span data-ttu-id="7716c-104">Configure les connexions aux ressources réseau.</span><span class="sxs-lookup"><span data-stu-id="7716c-104">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="7716c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7716c-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7716c-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7716c-106">Attributes and Elements</span></span>  

 <span data-ttu-id="7716c-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7716c-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7716c-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="7716c-108">Attributes</span></span>  
  
|<span data-ttu-id="7716c-109">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="7716c-109">**Attribute**</span></span>|<span data-ttu-id="7716c-110">**Description**</span><span class="sxs-lookup"><span data-stu-id="7716c-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="7716c-111">Spécifie si le système doit vérifier que le nom du certificat correspond au nom d’hôte du serveur avant d’utiliser le certificat.</span><span class="sxs-lookup"><span data-stu-id="7716c-111">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="7716c-112">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="7716c-112">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="7716c-113">Spécifie si le système doit vérifier si le certificat a été révoqué avant d’utiliser le certificat.</span><span class="sxs-lookup"><span data-stu-id="7716c-113">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="7716c-114">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="7716c-114">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="7716c-115">Spécifie la durée de mise en cache des résolutions DNS (Domain Name Service) dans le cadre de l’option de tourniquet (Round Robin) DNS, en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="7716c-115">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="7716c-116">La valeur par défaut est 120 000 millisecondes (deux minutes).</span><span class="sxs-lookup"><span data-stu-id="7716c-116">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="7716c-117">Spécifie si les résolutions DNS des noms d’hôtes avec plusieurs adresses IP (Internet Protocol) renvoient toutes les adresses ou uniquement la première.</span><span class="sxs-lookup"><span data-stu-id="7716c-117">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="7716c-118">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="7716c-118">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="7716c-119">Spécifie la stratégie de chiffrement appliquée à une session SSL/TLS sur une <xref:System.Net.ServicePointManager> instance.</span><span class="sxs-lookup"><span data-stu-id="7716c-119">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="7716c-120">Les valeurs possibles sont équivalentes aux valeurs de l' <xref:System.Net.Security.EncryptionPolicy> énumération.</span><span class="sxs-lookup"><span data-stu-id="7716c-120">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="7716c-121">L’utilisation de <xref:System.Security.Authentication.CipherAlgorithmType.Null> est requise lorsque la stratégie de chiffrement est définie sur `NoEncryption` .</span><span class="sxs-lookup"><span data-stu-id="7716c-121">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="7716c-122">La valeur par défaut est `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="7716c-122">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="7716c-123">Spécifie si les méthodes de publication doivent s’attendre à recevoir une `100-continue` réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="7716c-123">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="7716c-124">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="7716c-124">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="7716c-125">Spécifie si les connexions contrôlées par le gestionnaire de point de service utilisent l’algorithme Nagle.</span><span class="sxs-lookup"><span data-stu-id="7716c-125">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="7716c-126">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="7716c-126">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7716c-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7716c-127">Child Elements</span></span>  

 <span data-ttu-id="7716c-128">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7716c-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7716c-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7716c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="7716c-130">**Element**</span><span class="sxs-lookup"><span data-stu-id="7716c-130">**Element**</span></span>|<span data-ttu-id="7716c-131">**Description**</span><span class="sxs-lookup"><span data-stu-id="7716c-131">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="7716c-132">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7716c-132">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="7716c-133">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="7716c-133">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7716c-134">Notes</span><span class="sxs-lookup"><span data-stu-id="7716c-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7716c-135">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="7716c-135">Configuration Files</span></span>  

 <span data-ttu-id="7716c-136">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="7716c-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7716c-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7716c-137">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="7716c-138">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="7716c-138">Network Settings Schema</span></span>](index.md)
