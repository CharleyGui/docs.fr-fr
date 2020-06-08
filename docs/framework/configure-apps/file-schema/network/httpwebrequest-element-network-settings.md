---
title: <httpWebRequest>, élément (paramètres réseau)
description: L' <httpWebRequest> élément paramètres réseau personnalise les paramètres de la demande Web dans le .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 59ab425dcef8ac5283035910a9d78a89a16be8b1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504587"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="20fa1-103">\<httpWebRequest>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="20fa1-103">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="20fa1-104">Personnalise les paramètres de la demande Web.</span><span class="sxs-lookup"><span data-stu-id="20fa1-104">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="20fa1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="20fa1-105">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20fa1-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="20fa1-106">Attributes and Elements</span></span>  
 <span data-ttu-id="20fa1-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="20fa1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20fa1-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="20fa1-108">Attributes</span></span>  
  
|<span data-ttu-id="20fa1-109">**Attribut**</span><span class="sxs-lookup"><span data-stu-id="20fa1-109">**Attribute**</span></span>|<span data-ttu-id="20fa1-110">**Description**</span><span class="sxs-lookup"><span data-stu-id="20fa1-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="20fa1-111">Spécifie la longueur maximale d’un en-tête de réponse, en kilo-octets.</span><span class="sxs-lookup"><span data-stu-id="20fa1-111">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="20fa1-112">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="20fa1-112">The default is 64.</span></span> <span data-ttu-id="20fa1-113">La valeur-1 indique qu’aucune limite de taille n’est imposée sur les en-têtes de réponse.</span><span class="sxs-lookup"><span data-stu-id="20fa1-113">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="20fa1-114">Spécifie la longueur maximale d’une réponse d’erreur, en kilo-octets.</span><span class="sxs-lookup"><span data-stu-id="20fa1-114">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="20fa1-115">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="20fa1-115">The default is 64.</span></span> <span data-ttu-id="20fa1-116">La valeur-1 indique qu’aucune limite de taille n’est imposée à la réponse d’erreur.</span><span class="sxs-lookup"><span data-stu-id="20fa1-116">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="20fa1-117">Spécifie la longueur maximale d’un téléchargement en réponse à un code d’erreur non autorisé, en octets.</span><span class="sxs-lookup"><span data-stu-id="20fa1-117">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="20fa1-118">La valeur par défaut est -1.</span><span class="sxs-lookup"><span data-stu-id="20fa1-118">The default is -1.</span></span> <span data-ttu-id="20fa1-119">Une valeur de -1 indique qu'aucune limite de taille n'est imposée au transfert.</span><span class="sxs-lookup"><span data-stu-id="20fa1-119">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="20fa1-120">Spécifie si l’analyse d’en-tête non sécurisé est activée.</span><span class="sxs-lookup"><span data-stu-id="20fa1-120">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="20fa1-121">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="20fa1-121">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20fa1-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="20fa1-122">Child Elements</span></span>  
 <span data-ttu-id="20fa1-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="20fa1-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20fa1-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="20fa1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="20fa1-125">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="20fa1-125">**Element**</span></span>|<span data-ttu-id="20fa1-126">**Description**</span><span class="sxs-lookup"><span data-stu-id="20fa1-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="20fa1-127">settings</span><span class="sxs-lookup"><span data-stu-id="20fa1-127">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="20fa1-128">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="20fa1-128">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20fa1-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="20fa1-129">Remarks</span></span>  
 <span data-ttu-id="20fa1-130">Par défaut, le .NET Framework applique strictement la norme RFC 2616 pour l’analyse d’URI.</span><span class="sxs-lookup"><span data-stu-id="20fa1-130">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="20fa1-131">Certaines réponses du serveur peuvent inclure des caractères de contrôle dans les champs interdits, ce qui entraîne la <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> levée par la méthode de <xref:System.Net.WebException> .</span><span class="sxs-lookup"><span data-stu-id="20fa1-131">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="20fa1-132">Si **UseUnsafeHeaderParsing** a la valeur **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> ne lève pas d’exception dans ce cas ; toutefois, votre application est vulnérable à plusieurs formes d’attaques d’analyse d’URI.</span><span class="sxs-lookup"><span data-stu-id="20fa1-132">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="20fa1-133">La meilleure solution consiste à modifier le serveur afin que la réponse n’inclue pas les caractères de contrôle.</span><span class="sxs-lookup"><span data-stu-id="20fa1-133">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="20fa1-134">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="20fa1-134">Configuration Files</span></span>  
 <span data-ttu-id="20fa1-135">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="20fa1-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="20fa1-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="20fa1-136">Example</span></span>  
 <span data-ttu-id="20fa1-137">L’exemple suivant montre comment spécifier une longueur d’en-tête maximale supérieure à la normale.</span><span class="sxs-lookup"><span data-stu-id="20fa1-137">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="20fa1-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20fa1-138">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="20fa1-139">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="20fa1-139">Network Settings Schema</span></span>](index.md)
