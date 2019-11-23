---
title: <mailSettings>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: 4e8bf23ce39edadf80f019315c690b597b3d7361
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089230"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="43e08-102">\<mailSettings >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="43e08-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="43e08-103">Configure les options d’envoi de courrier.</span><span class="sxs-lookup"><span data-stu-id="43e08-103">Configures mail sending options.</span></span>  

<span data-ttu-id="43e08-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="43e08-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="43e08-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="43e08-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="43e08-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<mailSettings** ></span><span class="sxs-lookup"><span data-stu-id="43e08-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="43e08-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43e08-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43e08-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="43e08-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43e08-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="43e08-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43e08-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="43e08-110">Attributes</span></span>  
 <span data-ttu-id="43e08-111">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="43e08-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43e08-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="43e08-112">Child Elements</span></span>  
  
|<span data-ttu-id="43e08-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="43e08-113">Attribute</span></span>|<span data-ttu-id="43e08-114">Description</span><span class="sxs-lookup"><span data-stu-id="43e08-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="43e08-115">\<l’élément de > SMTP (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="43e08-115">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="43e08-116">Configure les options de protocole de transport de messagerie simple.</span><span class="sxs-lookup"><span data-stu-id="43e08-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43e08-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="43e08-117">Parent Elements</span></span>  
  
|<span data-ttu-id="43e08-118">**Élément**</span><span class="sxs-lookup"><span data-stu-id="43e08-118">**Element**</span></span>|<span data-ttu-id="43e08-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="43e08-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="43e08-120">\<system.Net>, élément (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="43e08-120">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="43e08-121">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="43e08-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="43e08-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="43e08-122">Example</span></span>  
 <span data-ttu-id="43e08-123">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l’aide des informations d’identification réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="43e08-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43e08-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43e08-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="43e08-125">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="43e08-125">Network Settings Schema</span></span>](index.md)
