---
title: <mailSettings>, élément (paramètres réseau)
description: L' <mailSettings> élément paramètres réseau configure les options d’envoi de courrier dans la .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: ce7b8564e4ee5ea73d42259612c077420d36645b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504561"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="64893-103">\<mailSettings>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="64893-103">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="64893-104">Configure les options d’envoi de courrier.</span><span class="sxs-lookup"><span data-stu-id="64893-104">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="64893-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="64893-105">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="64893-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="64893-106">Attributes and Elements</span></span>  
 <span data-ttu-id="64893-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="64893-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="64893-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="64893-108">Attributes</span></span>  
 <span data-ttu-id="64893-109">Aucun.</span><span class="sxs-lookup"><span data-stu-id="64893-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="64893-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="64893-110">Child Elements</span></span>  
  
|<span data-ttu-id="64893-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="64893-111">Attribute</span></span>|<span data-ttu-id="64893-112">Description</span><span class="sxs-lookup"><span data-stu-id="64893-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="64893-113">\<smtp>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="64893-113">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="64893-114">Configure les options de protocole de transport de messagerie simple.</span><span class="sxs-lookup"><span data-stu-id="64893-114">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="64893-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="64893-115">Parent Elements</span></span>  
  
|<span data-ttu-id="64893-116">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="64893-116">**Element**</span></span>|<span data-ttu-id="64893-117">**Description**</span><span class="sxs-lookup"><span data-stu-id="64893-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="64893-118">\<system.Net>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="64893-118">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="64893-119">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="64893-119">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="64893-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="64893-120">Example</span></span>  
 <span data-ttu-id="64893-121">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l’aide des informations d’identification réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="64893-121">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="64893-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64893-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="64893-123">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="64893-123">Network Settings Schema</span></span>](index.md)
