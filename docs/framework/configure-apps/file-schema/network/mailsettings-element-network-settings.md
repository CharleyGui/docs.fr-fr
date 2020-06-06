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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089230"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="5f211-102">\<mailSettings>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="5f211-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="5f211-103">Configure les options d’envoi de courrier.</span><span class="sxs-lookup"><span data-stu-id="5f211-103">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="5f211-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f211-104">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f211-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5f211-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5f211-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5f211-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f211-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="5f211-107">Attributes</span></span>  
 <span data-ttu-id="5f211-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5f211-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f211-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5f211-109">Child Elements</span></span>  
  
|<span data-ttu-id="5f211-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="5f211-110">Attribute</span></span>|<span data-ttu-id="5f211-111">Description</span><span class="sxs-lookup"><span data-stu-id="5f211-111">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="5f211-112">\<smtp>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="5f211-112">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="5f211-113">Configure les options de protocole de transport de messagerie simple.</span><span class="sxs-lookup"><span data-stu-id="5f211-113">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f211-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5f211-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5f211-115">**Appartient**</span><span class="sxs-lookup"><span data-stu-id="5f211-115">**Element**</span></span>|<span data-ttu-id="5f211-116">**Description**</span><span class="sxs-lookup"><span data-stu-id="5f211-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5f211-117">\<system.Net>, Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="5f211-117">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="5f211-118">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="5f211-118">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5f211-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="5f211-119">Example</span></span>  
 <span data-ttu-id="5f211-120">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l’aide des informations d’identification réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="5f211-120">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f211-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f211-121">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="5f211-122">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="5f211-122">Network Settings Schema</span></span>](index.md)
